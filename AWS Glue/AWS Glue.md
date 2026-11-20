**AWS Glue** là dịch vụ tích hợp dữ liệu của AWS. Bạn dùng Glue để **đọc dữ liệu từ nhiều nguồn, làm sạch hoặc kết hợp dữ liệu, rồi ghi kết quả** [[ETL (Extract - Transform - Load)]] vào nơi như Amazon S3 hay Redshift. AWS quản lý hạ tầng chạy các tác vụ này.

Ví dụ, mỗi đêm Glue đọc **đơn hàng từ S3** và **thông tin khách hàng từ RDS**, ghép chúng theo `customer_id`, rồi ghi kết quả thành file Parquet trên S3 để Athena truy vấn.


```mermaid
flowchart LR
    S3["S3 · Đơn hàng"] --> GLUE["Glue ETL · Làm sạch và ghép dữ liệu"]
    RDS["RDS · Khách hàng"] --> GLUE
    GLUE --> OUT["S3 · Dữ liệu đã xử lý"]
    OUT --> ATHENA["Athena · Truy vấn bằng SQL"]
```


Ba thành phần bạn thường gặp:

- **Glue ETL Job** chạy logic xử lý dữ liệu. Job có thể chạy theo lô (_batch_) hoặc đọc luồng liên tục (_streaming_).
- **[[Glue Data Catalog]]** lưu thông tin mô tả bảng như tên cột, kiểu dữ liệu và vị trí file. Trong ví dụ trên, dữ liệu thực tế vẫn nằm trên S3.
- **[[GLUE Crawler]]** khảo sát nguồn dữ liệu để tự tạo hoặc cập nhật thông tin bảng trong Catalog.

```mermaid
flowchart LR
  A["Dữ liệu trong S3"] --> B["Glue crawler"]
  B --> C["Glue Data Catalog"]
  C --> D["Athena"]
  C --> E["Redshift"]
  C --> F["EMR Hive"]
  A --> G["Glue ETL trên Spark"]
```


![[Pasted image 20261103153910.png]]