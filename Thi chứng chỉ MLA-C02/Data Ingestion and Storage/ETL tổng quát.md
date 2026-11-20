1. [[Kinesis Data Streams]]: lấy dữ liệu trực tiếp từ nguồn (không thực hiện biến đổi hoặc tính toán) - hiện tại đang được thay thế bằng [[Amazon MSK (Managed streaming for apache kafka)]]
2. [[Data Firehouse]]: lấy dữ liệu từ **data stream** hoặc những produce khác để thực hiện biến đổi (chỉ biến đổi thôi)
3. [[AWS Glue]]: thực hiện sử lý dữ liệu, làm sạch, tinh chỉnh và chuẩn bị dữ liệu 
4. [[Amazon Flink (Amazon Managed Service for Apache Flink)]]: là nơi tính toán dữ liệu realtime để chuyển sang destination

> [!note]
> Trong pipeline bạn đang học, **Kinesis Data Streams hoặc MSK giữ luồng sự kiện**, **Firehose gom và chuyển dữ liệu đến đích**, còn **Glue ETL chuẩn bị dữ liệu để phân tích**. Glue có thể đọc trực tiếp từ Kinesis hoặc MSK khi bạn muốn xử lý luồng thay vì chờ file trên S3.
```mermaid
flowchart LR
    KDS["Kinesis Data Streams"] --> FLINK["Managed Service for Apache Flink"]
    KDS --> FH["Amazon Data Firehose"]
    FLINK --> FH

    FH --> S3["Amazon S3"]
    S3 -->|Firehose COPY| RS["Amazon Redshift"]

    S3 --> GLUE["AWS Glue ETL"]
    RDS["Amazon RDS"] --> GLUE
    GLUE --> S3

    S3 -.-> CRAWLER["Glue Crawler"]
    CRAWLER --> CATALOG["Glue Data Catalog"]
    CATALOG -.-> ATHENA["Amazon Athena"]
    S3 --> ATHENA
```

## Chi tiết
```mermaid
flowchart TD
    APP["Ứng dụng bán hàng<br/>Phát sinh sự kiện đơn hàng"]
    KDS["Kinesis Data Streams<br/>Nhận và giữ luồng sự kiện"]

    APP --> KDS

    subgraph Realtime["Nhánh 1 — Phân tích liên tục"]
        FLINK["Managed Service for Apache Flink<br/>Tính doanh thu mỗi phút<br/>Phát hiện giao dịch bất thường"]
        ALERT["Ứng dụng cảnh báo<br/>Xử lý sự kiện bất thường"]
        RESULTFH["Amazon Data Firehose<br/>Gom và giao kết quả"]
        STAGE["S3 trung gian"]
        RS["Amazon Redshift<br/>Dữ liệu phục vụ báo cáo"]

        FLINK -->|Sự kiện bất thường| ALERT
        FLINK -->|Kết quả tổng hợp| RESULTFH
        RESULTFH --> STAGE
        STAGE -->|Firehose chạy COPY| RS
    end

    KDS -->|Consumer xử lý luồng| FLINK

    subgraph RawStorage["Nhánh 2 — Lưu dữ liệu gốc"]
        RAWFH["Amazon Data Firehose<br/>Đọc stream và gom bản ghi thành file"]
        RAW["Amazon S3 — Raw<br/>Dữ liệu đơn hàng gốc"]

        RAWFH --> RAW
    end

    KDS -->|Consumer lưu trữ độc lập| RAWFH

    subgraph GlueETL["Nhánh 3 — Chuẩn bị dữ liệu bằng Glue"]
        CUSTOMER["Dữ liệu khách hàng<br/>RDS hoặc S3"]
        TRIGGER["Lịch chạy<br/>Ví dụ: mỗi đêm"]
        JOB["Glue ETL Job<br/>1. Đọc đơn hàng và khách hàng<br/>2. Làm sạch, chuẩn hóa<br/>3. Join theo customer_id<br/>4. Ghi dữ liệu dạng Parquet"]
        CLEAN["Amazon S3 — Curated<br/>Dữ liệu đã làm sạch và kết hợp"]

        CUSTOMER --> JOB
        TRIGGER -->|Khởi chạy| JOB
        JOB --> CLEAN
    end

    RAW -->|Đọc dữ liệu gốc| JOB

    subgraph Metadata["Glue — Quản lý metadata"]
        CRAWLER["Glue Crawler<br/>Khảo sát cấu trúc dữ liệu"]
        CATALOG["Glue Data Catalog<br/>Tên bảng, cột, kiểu dữ liệu<br/>và vị trí file"]

        CRAWLER -->|Tạo hoặc cập nhật| CATALOG
    end

    RAW -.->|Khảo sát| CRAWLER
    CLEAN -.->|Khảo sát| CRAWLER
    CATALOG -.->|Cung cấp metadata| JOB

    ATHENA["Amazon Athena<br/>Truy vấn dữ liệu S3 bằng SQL"]
    BI["Dashboard / Công cụ BI"]

    CLEAN -->|Dữ liệu được truy vấn| ATHENA
    CATALOG -.->|Mô tả bảng| ATHENA
    ATHENA --> BI
    RS --> BI
```


