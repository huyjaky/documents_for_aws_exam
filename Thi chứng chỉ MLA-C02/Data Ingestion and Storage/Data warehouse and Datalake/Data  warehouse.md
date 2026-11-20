[[Data warehouse]](ref từ aws)
![[Pasted image 20261020112719.png|883]]
1. đây là nơi tập hợp tất cả dữ liệu [[Structure]] (đã được xử lý) đổ về cùng một nơi để query 
2. ở đây ta sẽ sử dụng [[Amazon Redshift]] là [[Data  warehouse]] của AWS
3. vì đây là nơi tập hợp tất cả nguồn [[Structure]] data đều đổ về đây vì thế nó sẽ có đa dạng monitor, view, query để thực hiện vì thế bạn sẽ thấy nó sẽ chứa những thứ không cần thiết khi vào truy vấn 

> [!note]
> và [[Data warehouse]] sẽ dùng [[Amazon Redshift]]

> [!warning]
> 
vì [[Data warehouse]] là dạng nơi lưu trữ mà dữ liệu, thông tin cần phải được xử lý thành những dạng có [[Structure]] để có thể lưu trữ vì thế nó theo dạng [[ETL (Extract - Transform - Load)]] ([[Data warehouse]] là bước nằm giữa Transform và Load vì sau khi Transform nó sẽ phải đỗ dữ liệu vào [[Data warehouse]] để Load lên)

![[Pasted image 20261020131219.png]]

![[Pasted image 20261020121819.png|643]]