#advance #Knowledge #logistic

## Logistic regression là gì? 
Logistic regression là hàm chủ yếu dùng để [[Classification]] khác với [[Linear regression]] chỉ để tính xu hướng của dữ liệu thì Logistic regression dùng để xác định cá thể đó thuộc lớp nào trong tập dữ liệu và <font color="#f79646">chỉ áp dụng cho bài toán phân loại nhị phân</font>

## Vậy làm sao để tìm được logistic regression

![[[Slide-V3]-Logistic-Regression.pdf#page=21&rect=2,11,941,455|[Slide-V3]-Logistic-Regression, p.21]]
ở đây ta dùng hàm [[Sigmoid]] để có thể tính được $\hat{y}$

=> vì bài này là bài toán binary nên ta dùng  [[Sigmoid]] để có thể dễ dàng xác định được lớp của cá thể đó 

## Ý tưởng tạo nên thuật toán Logistic regression 

=> Bởi vì bài toán logistic regression thường được dùng để giải quyết bài toán<font color="#f79646"> binary classification</font> vì thế nên công thức [[Sigmoid]] được áp dụng để giải quyết bài toán đấy với công thức:
$$\hat{y} = \sigma(z) = \frac{1}{1 + e^{-z}}$$
- $z=wx+b$

=> Và cách nó hoạt động thì khá giống với [[Linear regression]] vì cũng là $z = wx + b$  nhưng khác ở chỗ là thay vì dùng công thức bậc nhất thì ta thay vào đấy là hàm [[Sigmoid]] và công thức tính loss [[BCE (binary cross entropy)]] là:
$$L(\theta) = ( -y \log \hat{y} - (1-y) \log (1-\hat{y}) )$$
 - $\theta = w$ : hai ký hiệu này đề là đặc trưng của hàm loss
## vậy tại sao ta lại thay thế hàm loss MSE thành [[BCE (binary cross entropy)]] ?

=> vì như ta đã biến thì công thức tính $\hat{y}$ là ta dùng hàm [[Sigmoid]] nhưng khi áp dụng vào MSE thì nó sẽ sảy ra một vấn đề về [[Hàm lồi-lõm (Convex-Concave)]]

=> ta sẽ cố đưa hàm loss về một hàm convex vì nó sẽ dễ dàng tìm được điểm loss toàn cục vì chỉ có một điểm loss duy nhất 


VD về việc khi áp dụng MSE vào logistic regression:
![[convex-concave.excalidraw.md#^group=aT7yTti6|800]]

### Đạo hàm Loss
![[logistic regression.excalidraw.md#^group=mVWwNtPZo5RRUBSLq-qYJ|800]]

---

## [[Multiple regression]]
=> Cái này thì khá là giống với [[Linear regression]] 




---
## Code Logistic regression
![[Pasted image 20241222120459.png]]
=> Pipeline để code [[ex.py]]

![[Advanced Logistic Regression_v3.pdf#page=5&rect=429,0,938,539|Advanced Logistic Regression_v3, p.5]]


