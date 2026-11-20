#extra #linear-regression


-> <span style="background:#b1ffff">Vì Feauture đầu vào không phải chỉ duy nhất 1 Feature nên ta có công thức (1) như dưới </span>

Một cách đơn giản nhất, chúng ta có thể thấy rằng: i) diện tích nhà càng lớn thì giá nhà càng cao; ii) số lượng phòng ngủ càng lớn thì giá nhà càng cao; iii) càng xa trung tâm thì giá nhà càng giảm. Một hàm số đơn giản nhất có thể mô tả mối quan hệ giữa giá nhà và 3 đại lượng đầu vào là:

$$
y \approx f(x) = \hat{y}
$$

$$
f(x) = w_1 x_1 + w_2 x_2 + w_3 x_3 + w_0 \tag{1}
$$

trong đó, $w_1$, $w_2$, $w_3$, $w_0$ là các hằng số, $w_0$ còn được gọi là bias. Mối quan hệ $y \approx f(x)$ bên trên là một mối quan hệ tuyến tính (linear). Bài toán chúng ta đang làm là một bài toán thuộc loại regression. Bài toán đi tìm các hệ số tối ưu $\{w_1, w_2, w_3, w_0\}$ chính vì vậy được gọi là bài toán Linear Regression.

<font color="#f79646">Vậy suy ra ta có công thức tổng quát khi khai triển ra hết là: </font>
$$
X_{\text{new}} = X - \alpha \cdot \nabla L(y, w \cdot X)
$$

##### vậy tại sao phải dùng [[Math/Gradient descent|Gradient descent]] có thêm [[Learning rate|Learning rate]] vào làm gì?

-> [[Learning rate|Learning rate]] giúp tránh việc bị [[Overfitting|Overfitting]] và đồng thời giảm nhiễu trong mô hình với việc bước những bước quá lớn thì không thể tìm tới được cực tiểu của hàm Loss