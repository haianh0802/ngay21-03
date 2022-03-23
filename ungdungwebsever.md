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
### Bước 1: Cài đặt JDK
sudo apt-get install default-jdk

![image](https://user-images.githubusercontent.com/101684058/159615563-f0afa09c-0964-4749-aace-b4e68b85ef12.png)

### Bước 2: Kiểm tra Java đã được cài đặt hay chưa
Java -version


![image](https://user-images.githubusercontent.com/101684058/159615675-ecf4b881-0851-42d5-bf66-1ad5ce650cea.png)

### Bước 3: Cài đặt tomcat
3.1 Truy cập trang web https://tomcat.apache.org/

![image](https://user-images.githubusercontent.com/101684058/159620545-87f694a5-779f-46a6-8fe5-7338ab614af9.png)

Chọn Tomcat 9 => 9.0.60

![image](https://user-images.githubusercontent.com/101684058/159620613-1a75873a-96e8-4cb8-bc07-bc97de36ef57.png)

Nhấn chuột phải và chọn copy link

3.2 Download gói cài đặt tomcat

![image](https://user-images.githubusercontent.com/101684058/159615980-0c263753-c3da-49c8-b60d-b8096c55b3d3.png)

wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.60/bin/apache-tomcat-9.0.60.tar.gz

3.3 Giải nén gói cài đặt vừa tải về


![image](https://user-images.githubusercontent.com/101684058/159616035-42a02e84-033c-4d65-a579-6e5bce4f6c79.png)

tar -xzf apache-tomcat-9.0.60.tar.gz

3.4 Di chuyển file đã giải nén vào thư mục tùy chọn
Tạo thư mục: sudo mkdir /opt/tomcat

Di chuyển các mục vào thư mục vừa tạo: mv apache-tomcat-9.0.60/* /opt/tomcat/

![image](https://user-images.githubusercontent.com/101684058/159616233-e5ee38aa-8d79-4784-b420-e53ae9918543.png)

3.5 kiểm tra các tệp đã được chuyển đến thư mục chưa
cd /opt/tomcat/

ls

![image](https://user-images.githubusercontent.com/101684058/159618400-f96ac38c-07ee-4a9d-b452-f5cd45462325.png)

3.6 Tạo quản trị viên và trình quản lí:
cd conf/

ls

Tạo quản trị viên và user

sudo nano tomcat-users.xml

Bổ sung user

![image](https://user-images.githubusercontent.com/101684058/159618498-c9e38f51-e4f2-4916-b629-36c2e2486376.png)

Kiểm tra xem tomcat đã được khởi động chưa

./startup.sh

![image](https://user-images.githubusercontent.com/101684058/159619280-ec1e4779-5427-401a-8ab5-70ed77f9a1fc.png)

![image](https://user-images.githubusercontent.com/101684058/159619495-7493c748-f567-429e-b0e6-b7091babda32.png)

3.7 Kiểm tra
Mở trình duyệt truy cập đường dẫn: Localhost:8080



![image](https://user-images.githubusercontent.com/101684058/159619622-7e1ce1a1-5206-4a60-ae23-1f50cd6e30a4.png)


# Cài đặt Lighttpd trên Ubuntu 20.04
Lighttpd là một giải pháp thay thế rất phổ biến cho các máy chủ web phổ biến trên hệ điều hành họ Unix. Nhờ đó, Chúng ta có thể tìm thấy nó có sẵn thông qua các kho lưu trữ Ubuntu 20.04 chính. Do đó, để cài đặt nó trong Ubuntu 20.04, chúng ta sẽ chỉ phải mở một thiết bị đầu cuối (Ctrl + Alt + T) và thực hiện lệnh:

sudo apt install lighttpd


![image](https://user-images.githubusercontent.com/101684058/159663041-c9b205a3-445d-44ff-911b-4c673764068e.png)

### Khởi động dịch vụ lighttpd

sudo systemctl start lighttpd

![image](https://user-images.githubusercontent.com/101684058/159663561-db1a86a3-9012-4f17-b9e9-d6e927d6ca22.png)


### kiểm tra trạng thái dịch vụ lighttpd
sudo systemctl status lighttpd

![image](https://user-images.githubusercontent.com/101684058/159663630-5ba3855a-baba-4cd1-bb73-041477499f9b.png)

### Vào trình duyệt, truy cập vào địa chỉ ip để kiểm tra

![image](https://user-images.githubusercontent.com/101684058/159664798-321c8899-b7b2-4873-b689-05280e12c2ce.png)

## Thêm hỗ trợ PHP vào Lighttpd
Cài đặt php 7.4

sudo apt install php7.4 php7.4-fpm php7.4-mysql php7.4-cli php7.4-curl php7.4-xml

![image](https://user-images.githubusercontent.com/101684058/159665395-b4ccc507-c55c-4418-999c-bc89a2769792.png)


## Mở rộng một trong những tệp cấu hình
sudo nano /etc/php/7.4/fpm/pool.d/www.conf

## Thay đổi giá trị listen thành 127.0.0.1:9000

thực hiện nhiều thay đổi hơn đối với tệp cấu hình khác
sudo nano /etc/lighttpd/conf-available/15-fastcgi-php.conf

Thay đổi 2 dòng:

"bin-path" => "/usr/bin/php-cgi",

"socket" => "/var/run/lighttpd/php.socket",

Thành:

"host" => "127.0.0.1",

"port" => "9000",

![image](https://user-images.githubusercontent.com/101684058/159665534-0f94b26d-d37d-43e6-a672-81a4a9f37c25.png)

## kích hoạt các mô-đun giúp Lighttpd hoạt động với PHP:
sudo lighty-enable-mod fastcgi

sudo lighty-enable-mod fastcgi-php

![image](https://user-images.githubusercontent.com/101684058/159665755-8b004f77-60db-4649-9683-70b8b4fc4592.png)

## khởi động lại các dịch vụ Lighttpd và php-fpm:
Kiểm tra xem PHP đã được kích hoạt chưa
chúng ta sẽ viết một tệp PHP trong thư mục gốc của Lighttpd, và sau đó mở nó bằng trình duyệt.
sudo nano /var/www/html/test.php

Bên trong tệp dán đoạn lệnh sau:

![image](https://user-images.githubusercontent.com/101684058/159666421-3c647e23-e434-4db2-b1b2-60965048ec5b.png)

## thay đổi quyền của thư mục và đặt Lighttpd làm chủ sở hữu của nó
sudo chown -R www-data:www-data /var/www/html/

sudo chown -R 755 /var/www/html/

![image](https://user-images.githubusercontent.com/101684058/159666799-2e09f1ac-8b30-4149-a31e-7ca1b4bab7b0.png)

Bây giờ chúng ta mở trình duyệt và truy cập vào đường dẫn để kiểm tra

192.168.1.70/test.php


