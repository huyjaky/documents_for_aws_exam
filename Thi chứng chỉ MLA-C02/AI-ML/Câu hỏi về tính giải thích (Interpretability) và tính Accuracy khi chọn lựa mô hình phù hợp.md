![[Pasted image 20261027125953.png|676]]

Hình đang mô tả **sự đánh đổi thường gặp, chứ không phải quy luật: mô hình càng khó giải thích thì càng tốt**. Ngoài ra, “performance” ở đây là **chất lượng dự đoán**, không phải tốc độ chạy hay mức tiết kiệm tài nguyên.

Sự đánh đổi này thường xuất hiện vì:

- **Mô hình đơn giản dễ hiểu nhưng bị giới hạn trong cách biểu diễn dữ liệu.** Ví dụ, hồi quy tuyến tính dự đoán giá nhà theo công thức: `Giá = a × diện tích + b × số phòng + c`. Bạn dễ thấy từng yếu tố đóng góp vào kết quả như thế nào.
- **Mô hình phức tạp biểu diễn được nhiều quan hệ hơn.** Chẳng hạn, ảnh hưởng của diện tích có thể thay đổi theo vị trí, loại nhà và tuổi nhà. Một mô hình kết hợp hàng trăm cây hoặc mạng nơ-ron có thể học những tương tác này, giúp dự đoán tốt hơn **nếu dữ liệu phù hợp**.
- **Nhưng nhiều phép biến đổi và tương tác khiến việc giải thích khó hơn.** Ta vẫn tính được kết quả, nhưng khó diễn đạt toàn bộ quá trình bằng vài quy tắc con người dễ hiểu.

Có thể hình dung: **một cây quyết định nhỏ giống vài câu “nếu… thì…”; một rừng gồm hàng trăm cây là hàng trăm bộ quy tắc cùng bỏ phiếu**. Kết quả tổng hợp có thể tốt hơn, nhưng khó theo dõi hơn.

**Tuy nhiên, hình này đơn giản hóa quá mức.** Nếu dữ liệu có quan hệ gần tuyến tính, hồi quy tuyến tính có thể vừa dễ giải thích vừa dự đoán tốt nhất. Mô hình phức tạp cũng có thể học cả nhiễu và dự đoán kém trên dữ liệu mới.

Vì vậy, khi chọn mô hình, nên hỏi: **“Độ phức tạp tăng thêm có cải thiện dự đoán đủ nhiều để đáng đánh đổi sự dễ hiểu không?”** Muốn biết, phải so sánh trên dữ liệu kiểm tra, chứ không thể dựa vào thứ tự các mô hình trong hình.