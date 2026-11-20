#Algorithm #deep-learning

## Linear regression là gì 

![[Pasted image 20241103142514.png]]

- Linear regression là những bài toán tính toán và dự đoán xu hướng của Feature trong dữ liệu đó

## Linear regression hoạt động như thế nào 

![[LinearRegression_Fri_v3.pdf#page=15&rect=0,3,479,465|LinearRegression_Fri_v3, p.15|400]]
-> Như hình ta có thể thấy rằng là khi tính toán đường thẳng theo trend của dữ liệu để có thể dự đoán thì ta phải tìm ra $X$ và $b$ để có thể tính ra được $\hat{y}$ 

### B1: tạo lập một đường thẳng random từ dữ liệu đầu vào 
![[Linear-regression.excalidraw.md#^group=HvG-m21HJY8lbmdeAbIVl|image]]

vậy làm sao để có thể đưa đường thẳng đấy trùng với xu hướng của tập dữ liệu

-> Ta đã biết rằng là đường thẳng có công thức cơ bản là $y=a\cdot x+b$ 

### B2: chọn một hàm Loss $f(x)$ thích hợp

Ta có rất nhiều lựa chọn sáng giá như [[Sigmoid|Sigmoid]], ..
- Nhưng ở đây ta có thể chọn [[MSE (mean of square error)|MSE (mean of square error)]]
	- $$
MSE = \frac{SSE}{n} = \frac{1}{n} \cdot \frac{1}{2} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$


#### Vậy tại sao lại đề cập tới hàm Loss?

Vì ta có thể dễ dàng thấy rằng là ta mong muốn Gap giữa đường thẳng dự đoán và dữ liệu phải thấp nhất có thể 
![[Linear-regression.excalidraw.md#^group=J4JK0N1UVZuQH-sMkEVag|image]]
-> Như vậy ta có thể nói rằng ta phải tìm được điểm cực tiểu toàn cục cho phương trình bậc 2 [[MSE (mean of square error)|MSE (mean of square error)]] 
- Với $y$ là dữ liêụ Label cho trước trong tập dữ liệu đầu vào 
#### Vậy làm sao để tìm được điểm cực tiểu của [[MSE (mean of square error)|MSE (mean of square error)]]

vậy ta phải biết [[Math/Gradient descent|Gradient descent]] với công thức này dùng để cập nhật các giá trị sau khi bước một bước

vì ta có công thức đường thẳng là $\hat{y}=w \cdot X$ + b 

$$
w_{\text{new}} = w_{\text{old}} - \alpha \cdot \frac{\partial L}{\partial w}
$$
- $w$ là Feature đầu vào
- $\frac{\partial L}{\partial w}$ là đạo hàm của hàm loss theo w
- $\alpha$ là [[Learning rate|Learning rate]]


$$
b_{\text{new}} = b_{\text{old}} - \alpha \cdot \frac{\partial L}{\partial b}
$$
- $b$ là Feature đầu vào
- $\frac{\partial L}{\partial b}$ là đạo hàm của hàm loss theo b
- $\alpha$ là [[Learning rate|Learning rate]]

Vì trong công thức  $\hat{y}=w \cdot X$ + b:
- X là hằng số
- <span style="background:#b1ffff">w, b là ẩn số cần tìm sao cho loss bé nhất tại w và tại b nên ta mới có 2 phương trình tính loss như trên</span>

-> đa dạng Feature đầu vào [[Giải thích thêm cho Linear regression|Giải thích thêm cho Linear regression]] 

-> chứng minh các đạo hàm [[Chứng minh đạo hàm MSE|Chứng minh đạo hàm MSE]]


---
### Dùng [[Chain rules|Chain rules]] để tính toán đạo hàm của [[MSE (mean of square error)|MSE (mean of square error)]]

---

### Làm thế nào để tính được regression trong khi có đa feature(hay đa biến X)

=> [[Multiple regression]]

---

### [[Feed forward|Feed forward]] và [[Backpropagation|Backpropagation]]

---

### [[Mini-batch|Mini-batch]] để giảm tài nguyên dùng

---

### Có phải lúc nào cũng dùng mô hình [[Linear regression]] không?

=> vì trong thực tế có những bài toán không thể dùng mô hình liear regression để giải được vì độ gap giữa kết quả dự đoán và thực tế quá cao 

=> vì thế trước khi áp dụng bài toán này ta phải dùng [[Correlation efficency]] để đánh giá mức độ tuyến tính của dữ liệu

---
## Công thức đi kèm với learning rate trong [[MSE (mean of square error)]]

![[Pasted image 20241130185347.png]]

- $\lambda$ : [[Learning rate]]
- w : số lượng của các cá thể trong quần thể 

