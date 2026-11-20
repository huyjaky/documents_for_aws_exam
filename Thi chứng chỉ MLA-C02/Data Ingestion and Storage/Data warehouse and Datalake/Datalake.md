[[Knowledge/base-knowledge/DevOps/AWS/Terminology/storage/Datalake|Datalake]] (ref từ aws)

![[Pasted image 20261020130640.png|905]]

- đây là nơi mọi dữ liệu từ mọi nguồn chưa qua xử lý đổ về bao gồm nhiều dạng dữ liệu như [[Structure]] [[Unstructure]] [[Semi-Structure]], ... 
- vì đây là nơi thập cẩm nhất nên yêu cầu của nó phải có volume lớn để chưa hết tất cả 

> [!note]
> và ở đây [[Knowledge/Thi chứng chỉ/MLA-C02/Data Ingestion and Storage/Data warehouse and Datalake/Datalake|Datalake]] thì sẽ dùng [[S3 (Simple Storage Service)]])

> [!warning]
> vì đây là nơi để mọi nguồn dữ liệu có thể thoải mái đổ vào vì thế [[Knowledge/Thi chứng chỉ/MLA-C02/Data Ingestion and Storage/Data warehouse and Datalake/Datalake|Datalake]] có dạng cấu trúc là ELT (Extract - Load - Transform) đây là ngược lại với [[ETL (Extract - Transform - Load)]] và ở cũng như ở giữa Load và Transform của ELT là Datalake để khi đã load lên thì sẽ được đổ về Datalake và bắt đầu biến đổi thành [[Structure]] hoặc query từ đây 


> 