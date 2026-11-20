**EBS (Amazon Elastic Block Store)** là dịch vụ cung cấp **ổ đĩa lưu trữ cho máy chủ EC2** trên AWS. Bạn có thể hình dung EC2 là máy tính, còn EBS là ổ SSD/HDD gắn vào máy đó.

EBS thường dùng để lưu:

- Hệ điều hành của EC2.
- Dữ liệu ứng dụng, database, file và model ML.

Một vài điểm cần nhớ:
- 1 [[EBS]] <mark style="background:#b1ffff">chỉ được gắn với 1</mark> [[EC2]] instance thôi <mark style="background:#b1ffff">nhưng 1 EC2 có thể được gắn với nhiều</mark> [[EBS]] 
![[Pasted image 20261102110304.png|586]]
- **Dữ liệu vẫn còn khi dừng rồi bật lại EC2.**
- Khi **xóa EC2**, EBS có thể bị xóa theo hoặc được giữ lại, tùy cấu hình (Delete on Termination.
![[Pasted image 20261102110331.png]]
- Có thể tạo **snapshot** để sao lưu và khôi phục.
- Bạn trả phí theo dung lượng được cấp và loại ổ, kể cả khi EC2 đang dừng.

Trong ngữ cảnh **SageMaker**, EBS có thể là ổ lưu trữ gắn với máy chạy notebook hoặc tác vụ ML, dùng để chứa dữ liệu, mã nguồn và model.