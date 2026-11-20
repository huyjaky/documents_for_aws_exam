**AWS Glue Data Quality** là tính năng kiểm tra xem **dữ liệu thực tế có đạt các quy tắc bạn đặt ra hay không**. Ví dụ, với bảng `orders` trên S3, bạn có thể kiểm tra `order_id` có bị thiếu hoặc trùng, và `total_amount` có bị âm. Glue trả kết quả đạt hoặc không đạt cho từng quy tắc. Các quy tắc được viết bằng **DQDL** (_Data Quality Definition Language_). [Tài liệu AWS về DQDL](https://docs.aws.amazon.com/glue/latest/dg/dqdl.html)

> [!note]
> GLUE data quality là một bước được chèn vào GLUE job ([[AWS Glue]]) để tự động đánh giá chất lượng dữ liệu đầu vào và nếu vi phạm các tham số hay quy tắt đặt ra thì nó sẽ ngừng ngay hoặc ghi log trực tiếp vào [[Amazon CloudWatch]]

> [!warning]
> các quy tắt trong [[GLUE data quality]] có thể tạo bằng tay hoặc tạo tự động đều được vì [[GLUE data quality]] có tính năng đọc và tạo tự động quy tắt

| Thành phần            | Vai trò với bảng `orders`                                            |
| --------------------- | -------------------------------------------------------------------- |
| **Glue Crawler**      | Khảo sát file trên S3 và phát hiện các cột.                          |
| **Glue Data Catalog** | Lưu tên bảng, tên cột, kiểu dữ liệu và vị trí file.                  |
| **Glue Data Quality** | Đọc dữ liệu trong file để kiểm tra các giá trị có đạt quy tắc không. |


Bạn có thể chạy kiểm tra **từ Data Catalog** để giám sát bảng đã đăng ký, hoặc **trong Glue ETL job** để kiểm tra dữ liệu trước khi ghi kết quả. Nếu phát hiện đơn hàng lỗi, bạn có thể cấu hình ETL job để tách các dòng lỗi sang một thư mục S3 riêng. Việc sửa hoặc loại bỏ dòng lỗi do logic của job quyết định. [Tài liệu AWS về Glue Data Quality](https://docs.aws.amazon.com/glue/latest/dg/glue-data-quality.html)