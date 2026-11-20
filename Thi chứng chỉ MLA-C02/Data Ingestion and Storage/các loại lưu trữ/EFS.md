**EFS (Amazon Elastic File System)** là dịch vụ cung cấp **hệ thống file dùng chung qua mạng** trên AWS. Bạn có thể hình dung nhiều máy EC2 cùng kết nối đến một thư mục chung để đọc và ghi dữ liệu.

EFS thường dùng để lưu:

- File dùng chung giữa nhiều máy chủ.
- Nội dung website, file người dùng tải lên.
- Dữ liệu, mã nguồn và model ML cần truy cập từ nhiều máy.

Một vài điểm cần nhớ:

- **Nhiều máy có thể cùng đọc/ghi trên một EFS.**
- **Dữ liệu vẫn còn khi dừng hoặc xóa EC2** đang kết nối với EFS.
- Dung lượng **tự tăng/giảm theo lượng dữ liệu**, không cần cấp trước kích thước ổ.
- **EFS Regional** lưu dữ liệu trên nhiều AZ; **EFS One Zone** lưu trong một AZ.
- Bạn trả phí lưu trữ theo dung lượng sử dụng; phí truy cập và thông lượng phụ thuộc cấu hình.
- <mark style="background:#b1ffff">EFS có một life cycle để archive dữ liệu</mark> giống với [[S3 (Simple Storage Service)]] để tiết kiệm chi phí 
![[Pasted image 20261102114343.png|777]]
Ví dụ: bạn có ba EC2 chạy website. Cả ba dùng chung một EFS để lưu ảnh tải lên, nên ảnh được tải qua máy nào thì hai máy còn lại cũng truy cập được.