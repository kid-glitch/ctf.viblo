# https://ctf.viblo.asia/


Tiến hành Scan:

![image](https://user-images.githubusercontent.com/72652376/127117770-c1c4349f-e1ad-4767-bc5e-1bba5dc30f05.png)


![image](https://user-images.githubusercontent.com/72652376/127117829-c02cd5ff-3f24-47f5-9228-2770f966c43d.png)


![image](https://user-images.githubusercontent.com/72652376/127117874-7622b303-27d1-4e1a-8bf4-cc930cb9d5d5.png)

Truy cập vào thư mục ẩn được đoạn code về quá trình đăng nhập

Giải thích dễ hiểu gồm 2 thành phần

Thành phần 1 là hàm STRXOR: đóng vai trò là hàm XOR các ký tự

Thành phần 2 là hàm kiểm tra chuỗi đăng nhập vào

![image](https://user-images.githubusercontent.com/72652376/127118230-20accb9c-086d-4452-b975-e16002c6e1f8.png)

Hàm quan trọng để kiểm tra xem có đúng mật khẩu hay không bao gồm:

base64_decode($this_password): dùng để decode cái this_password đã cho sẵn

STRXOR($key, $pass): ở hàm xor này $pass đã được cho sẵn. Nghĩa là phải đi tìm $key 


Mô tả hoạt động:

Khi nhập mật khẩu (Chưa biết) vào mật khẩu sẽ được băm md5 bằng đoạn mã <code>$pass = md5($_POST['password']);</code>

Sau đó sẽ được XOR với biến $key (đã biết)

Nếu kết quả của hàm XOR này khớp với base64_decode($this_password) thì sẽ là kết quả đúng là có được cờ (kết quả hàm base64_decode($this_password) đã biết)

Tiến hành giải mã:

![image](https://user-images.githubusercontent.com/72652376/127119244-3c9112d5-43f0-443e-98f8-79d7754dfc83.png)

Sau đó crack md5 thu được: 

![image](https://user-images.githubusercontent.com/72652376/127119341-3d5fcbe4-01e1-4756-bb30-7a21835cc362.png)

Nhập và thu được cờ
