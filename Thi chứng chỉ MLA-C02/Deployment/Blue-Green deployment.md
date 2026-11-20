**Blue/green deployment trong SageMaker là cách cập nhật model đang phục vụ bằng cách tạo một cụm máy mới, rồi chuyển traffic từ cụm cũ sang cụm mới.**

- **Blue:** cụm đang chạy model hiện tại, ví dụ `v1`.
- **Green:** cụm mới chạy model cập nhật, ví dụ `v2`.

SageMaker tạo Green trong khi Blue vẫn phục vụ request. Sau đó chuyển traffic sang Green, theo dõi trong một khoảng thời gian gọi là **baking period**. Nếu ổn, SageMaker kết thúc Blue; nếu CloudWatch alarm đã cấu hình được kích hoạt, SageMaker tự chuyển traffic về Blue. [Tài liệu AWS](https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails-blue-green.html)

Có ba cách chuyển traffic:

|Cách|Ví dụ traffic sang Green|
|---|---|
|**All at once**|Chuyển ngay 100%|
|**Canary**|Chuyển thử 10%, theo dõi, rồi chuyển 90% còn lại|
|**Linear**|Tăng đều: 20% → 40% → 60% → 80% → 100%|

Các tỷ lệ trên là ví dụ. Bạn cấu hình cách chuyển và thời gian theo dõi theo nhu cầu. [Tài liệu AWS](https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails-blue-green.html)


> [!warning]
> 
Ví dụ: bạn deploy model dự đoán giá `v2` theo Canary. Ban đầu chỉ một phần request dùng `v2`; nếu tỷ lệ lỗi hoặc độ trễ vượt ngưỡng alarm, traffic quay về `v1`. Cách này giảm rủi ro khi cập nhật production. Với chuyển traffic nhiều bước hoặc có baking period, bạn trả phí cho cả hai cụm trong thời gian cập nhật. [Tài liệu AWS](https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails-blue-green.html)
