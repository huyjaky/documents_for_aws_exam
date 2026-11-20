**AWS Glue DataBrew** là công cụ của AWS để **khám phá, làm sạch và chuẩn hóa dữ liệu bằng giao diện trực quan**. Bạn chọn các bước xử lý trên màn hình và xem trước kết quả trên dữ liệu mẫu mà không cần viết code. [Tài liệu AWS về DataBrew](https://docs.aws.amazon.com/databrew/latest/dg/what-is.html)

> [!warning]
> nói ngắn gọn là tiền xử lý các tập dữ liệu lớn như convert, transform, gộp, ...

Ví dụ, bạn có file đơn hàng trên S3 với ngày tháng ghi theo nhiều định dạng và một số dòng bị trùng. Trong DataBrew, bạn chọn các bước **chuẩn hóa ngày → xóa dòng trùng → chuyển cột số tiền sang kiểu số**. DataBrew lưu các bước này thành một **recipe** (công thức). Khi chạy **recipe job**, DataBrew áp dụng công thức lên bộ dữ liệu và ghi kết quả đến vị trí bạn chọn. File nguồn vẫn giữ nguyên. [Tài liệu AWS về recipe job](https://docs.aws.amazon.com/databrew/latest/dg/jobs.recipe.html)

| Thành phần                          | Vai trò trong ví dụ đơn hàng                                                                                   |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **[[GLUE Crawler]] + Data Catalog** | Phát hiện và lưu mô tả bảng, chẳng hạn tên cột, kiểu dữ liệu và vị trí file.                                   |
| **[[GLUE data quality]]**           | Kiểm tra dữ liệu có đạt quy tắc hay không, chẳng hạn mã đơn hàng có bị trùng.                                  |
| **Glue DataBrew**                   | Cho bạn chọn thao tác làm sạch, xem trước kết quả và lưu các bước để chạy lại.                                 |
| **Glue ETL**                        | Chạy pipeline tích hợp dữ liệu, chẳng hạn đọc đơn hàng từ S3, ghép với khách hàng từ RDS rồi ghi vào Redshift. |

DataBrew cũng có **profile job** để xem thống kê như số dòng và phân bố giá trị. Bạn có thể chạy profile để hiểu dữ liệu trước, rồi dùng recipe job để biến đổi dữ liệu. [Tài liệu AWS về profile job](https://docs.aws.amazon.com/databrew/latest/dg/jobs.profile.html)