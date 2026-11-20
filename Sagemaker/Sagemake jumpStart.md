![[Pasted image 20260408140548.png]]


**Amazon SageMaker JumpStart** là một "trung tâm điều khiển" (hub) trong Amazon SageMaker, giúp bạn đẩy nhanh quá trình triển khai Machine Learning bằng cách cung cấp các mô hình, thuật toán và giải pháp đã được xây dựng sẵn (pre-built). <font color="#f79646">cho phép bạn can thiệp code trực tiếp </font>

-> ta có thể sử dụng [[Guardrails]] để có thể chặn những cuộc tấn công bằng [[English/từ vựng hàng ngày/Prompt]] tới model AI được sử dụng thông qua [[Bedrock]]

---

### 1. Các thành phần chính của JumpStart

#### **Foundation Models (Các mô hình nền tảng)**

JumpStart là nơi bạn tiếp cận các mô hình ngôn ngữ lớn (LLM) và mô hình tạo ảnh (Diffusion Models) mã nguồn mở hàng đầu:

- **LLMs:** Meta Llama 3, Mistral, Falcon, Cohere.
    
- **Hình ảnh:** Stable Diffusion (tạo ảnh từ văn bản).
    
- **Vision & Audio:** Các mô hình Whisper (chuyển âm thanh thành văn bản), Vision Transformers.
    
#### **Pre-built Solutions (Giải pháp dựng sẵn)**

Thay vì chỉ đưa cho bạn một mô hình, JumpStart cung cấp các "bản thiết kế" (Blueprints) cho các bài toán kinh doanh cụ thể:

- Hệ thống phát hiện gian lận tài chính.
    
- Dự báo nhu cầu hàng tồn kho.
    
- Phân tích thị hiếu khách hàng.
    
- Các giải pháp này đi kèm với đầy đủ hạ tầng (CloudFormation), mã nguồn và dữ liệu mẫu.
    
---
### 2. Lợi ích vượt trội cho lập trình viên

- **Triển khai chỉ với 1-Click:** Bạn có thể tạo một Endpoint (cổng kết nối) cho các mô hình như Llama 3 chỉ trong vài phút mà không cần viết code cấu hình server phức tạp.
    
- **Fine-tuning dễ dàng:** Nếu bạn có dữ liệu riêng của công ty, JumpStart cung cấp sẵn các Notebook để bạn huấn luyện thêm (Fine-tune) mô hình mà không cần phải hiểu sâu về kiến trúc mạng nơ-ron bên dưới.
    
- **Bảo mật tối đa:** Dữ liệu bạn dùng để huấn luyện trong JumpStart **không bao giờ** bị dùng để huấn luyện lại các mô hình gốc của AWS hay các bên thứ ba. Nó nằm hoàn toàn trong VPC của bạn.
    
- **Mã nguồn mở (Notebooks):** Mọi thứ trong JumpStart đều minh bạch. Bạn có thể mở các file Jupyter Notebook để xem cách AWS cấu hình mô hình và tùy chỉnh theo ý muốn.
    

---

### 3. Quy trình làm việc (Workflow)

1. **Duyệt (Browse):** Vào SageMaker Studio, chọn JumpStart và tìm mô hình bạn muốn (ví dụ: `Llama-3-8B`).
    
2. **Chọn hành động:**
    
    - **Deploy:** Nếu muốn dùng ngay qua API.
        
    - **Train/Fine-tune:** Nếu muốn mô hình học thêm dữ liệu của bạn.
        
3. **Sử dụng:** Sau khi Deploy, AWS trả về một **Endpoint**. Bạn chỉ cần dùng Python (`boto3`) để gửi yêu cầu và nhận kết quả.
    

---

### 4. So sánh với các tầng khác

|**Tầng**|**Dịch vụ tiêu biểu**|**Mức độ tùy chỉnh**|**Kỹ năng yêu cầu**|
|---|---|---|---|
|**Tier 1 (AI Services)**|Rekognition, Polly|Thấp nhất (Chỉ dùng API)|Developer (Python/JS)|
|**JumpStart**|**Llama 3, Stable Diffusion**|**Trung bình - Cao**|**ML Engineer / Dev**|
|**SageMaker (Core)**|Notebooks, Training Jobs|Cao nhất (Tự xây từ đầu)|Data Scientist|
