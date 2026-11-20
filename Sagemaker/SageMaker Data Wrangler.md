**SageMaker Data Wrangler** là công cụ trực quan để **khám phá, làm sạch và chuẩn bị dữ liệu cho mô hình machine learning**. Trong trải nghiệm SageMaker hiện nay, bạn truy cập Data Wrangler qua **SageMaker Canvas**. Bạn có thể thiết lập các bước bằng giao diện và thêm Python khi cần xử lý riêng. [Tài liệu AWS về Data Wrangler trong Canvas](https://docs.aws.amazon.com/sagemaker/latest/dg/canvas-data-prep.html)

![[Pasted image 20261104092305.png|528]]

> [!note]
> nó có chức năng giống với [[AWS Glue DataBrew]] nhưng dành cho ML (có thêm chức năng Visual data để kiểm tra outlier - không có tác dụng sử lý outlier)
> 

![[Pasted image 20261104092134.png|717]]

> [!warning]
> [[SageMaker Data Wrangler]] sẽ tự sinh ra code để transform dữ liệu mà không cần ta code 
> 
### Ví dụ

Ví dụ, để huấn luyện mô hình dự đoán khách hàng rời bỏ dịch vụ, bạn có thể dùng Data Wrangler để:

1. **Làm sạch dữ liệu** bằng cách xử lý các giá trị bị thiếu.
2. **Tạo đặc trưng (_feature_)** bằng cách chuyển `ngày_đăng_ký` thành `số_ngày_đã_sử_dụng` và mã hóa `loại_gói_cước` thành dữ liệu số.
3. **Lưu các bước thành một Data Flow** để chạy lại và xuất dữ liệu đã chuẩn bị ra S3 cho bước huấn luyện. [Tài liệu AWS về chuẩn bị dữ liệu](https://docs.aws.amazon.com/sagemaker/latest/dg/canvas-data-prep.html)

**So với Glue DataBrew**, cả hai đều có giao diện làm sạch và biến đổi dữ liệu. **DataBrew** phục vụ chuẩn bị dữ liệu nói chung, còn **Data Wrangler** tập trung vào quy trình ML, với các thao tác tạo đặc trưng và phân tích như phát hiện cột có thể vô tình tiết lộ đáp án cho mô hình. [AWS Glue DataBrew](https://docs.aws.amazon.com/databrew/latest/dg/what-is.html) · [SageMaker Data Wrangler](https://docs.aws.amazon.com/sagemaker/latest/dg/canvas-data-prep.html)