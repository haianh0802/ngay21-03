# Cài đặt Nginx trên Ubuntu
Nginx là 1 phần mềm mã nguồn mở để phục vụ web. Nó sử dụng kiến trúc đơn luồng và được thiết kế để có hiệu suất và độ ổn định tối đa, vì thế nó hiệu quả hơn Apache nếu được cấu hình chính xác. Ngoài các khả năng của máy chủ HTTP, NGINX cũng có thể hoạt động như một máy chủ proxy cho email (POP3, SMTP, …), một trình cân bằng tải và proxy ngược cho các máy chủ HTTP, TCP và UDP.
### Bước 1: Cài đặt Nginx
Vì Nginx có sẵn trong kho lưu trữ của Ubuntu nên ta có thể trực tiếp cài đặt Nginx bằng hệ thống cài đặt và quản lý gói apt.

Đầu tiên, tiến hành update các gói trong hệ thống :

sudo apt install -y update

Cài đặt Nginx cho máy chủ Ubuntu của bạn :

sudo apt install -y nginx

Kiểm tra phiên bản Nginx:

sudo nginx -v

Cho phép Nginx khởi động cùng hệ thống :

sudo systemctl enable nginx

Khởi động và kiểm tra trạng thái của dịch vụ Nginx :

systemctl start nginx 

systemctl status nginx

### Bước 2: Cấu hình tường lửa
Sử dụng ufw để biết cách sử dụng cấu hình tường lửa cho Nginx :

sudo ufw app list 
nó sẽ có đầu ra như sau :

Available applications:
  CUPS
  Nginx Full
  Nginx HTTP
  Nginx HTTPS
  OpenSSH
Ta thấy rằng đối với nginx, có 3 cấu hình có thể để cấu hình cho nginx, nhưng hiện tại mình chưa có cấu hình sử dụng SSL đối với trang web nên mình chỉ cho lưu lượng đi qua port 80.

Kích hoạt điều trên bằng cách sử dụng câu lệnh sau:

sudo ufw allow 'Nginx HTTP'
Sau đó kiểm tra lại thay đổi với lệnh sau:

sudo ufw status

### Bước 3: Kiểm tra trang web
Để kiểm tra trang web, ta mở trình duyệt và nhập vào địa chỉ ip của máy chủ Nginx.
http://IP_address 
ta sẽ được điều hướng đến trang web mặc định của Nginx :

![image](https://user-images.githubusercontent.com/101684058/159602834-e49f203b-b6b8-4f92-9cba-931b431ade45.png)


Khi bạn hiển thị như này tức là đã cài đặt thành công và nginx đã sẵn sàng để được quản lý.


# Cài đặt Tomcat trên Ubuntu

![image](https://user-images.githubusercontent.com/101684058/159615563-f0afa09c-0964-4749-aace-b4e68b85ef12.png)


![image](https://user-images.githubusercontent.com/101684058/159615675-ecf4b881-0851-42d5-bf66-1ad5ce650cea.png)


![image](https://user-images.githubusercontent.com/101684058/159615980-0c263753-c3da-49c8-b60d-b8096c55b3d3.png)


![image](https://user-images.githubusercontent.com/101684058/159616035-42a02e84-033c-4d65-a579-6e5bce4f6c79.png)


![image](https://user-images.githubusercontent.com/101684058/159616233-e5ee38aa-8d79-4784-b420-e53ae9918543.png)


![image](https://user-images.githubusercontent.com/101684058/159616287-9e48a33b-2f1c-4c2c-9f3b-b5d9e2245410.png)

![image](https://user-images.githubusercontent.com/101684058/159618400-f96ac38c-07ee-4a9d-b452-f5cd45462325.png)

![image](https://user-images.githubusercontent.com/101684058/159618498-c9e38f51-e4f2-4916-b629-36c2e2486376.png)


![image](https://user-images.githubusercontent.com/101684058/159619280-ec1e4779-5427-401a-8ab5-70ed77f9a1fc.png)

![image](https://user-images.githubusercontent.com/101684058/159619495-7493c748-f567-429e-b0e6-b7091babda32.png)

![image](https://user-images.githubusercontent.com/101684058/159619622-7e1ce1a1-5206-4a60-ae23-1f50cd6e30a4.png)


