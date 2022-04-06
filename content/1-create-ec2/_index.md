+++
title = "Khởi tạo EC2 instance"
date = "`r Sys.Date()`"
weight = 1
chapter = false
pre = "<b>1. </b>"
+++
Chúng ta sẽ khởi tạo EC2 Linux instance bằng Amazon EC2 console trên Singapore(ap-southeast-1).
#### Khởi chạy EC2 instance
1. Đăng nhập vào trang quản trị AWS Management Console và tìm kiếm dịch vụ EC2.
![EC2Search](/images/1-Create-EC2/1-Create-EC2-2.png)
2. Để khởi tạo máy ảo chọn **Launch instance**.
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-3.png)
3. Ở trang Choose an Amazon Machine Image (AMI) sẽ thể hiện một danh sách các Amazon Machine Images (AMIs). Lựa chọn AMI với tên Amazon Linux 2 AMI (HVM).
- Click **Select**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-4.png)
4. Tiếp theo, ở trang Choose an Instance Type, chúng ta sẽ lựa chọn cấu hình tài nguyên máy ảo. Lựa chọn loại **t2.micro**. Sau đó nhấn nút **Next: Configure Instance Details**.
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-5.png)
5. Tại trang Configure Instance Detail. Để giá trị mặc định. EC2 Instance của chúng ta sẽ được tạo trong VPC Default.
- Chọn subnet cho instance, ví dụ **`ap-southeast-1a`**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-6.png)
- Tại mục **IAM role**, chọn **Create new IAM role**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-7.png)
- Trong tab mới, chọn **Create role**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-8.png)
- Chọn **EC2** là dịch vụ sẽ sử dụng role này, sau đó kéo xuống và click nút **Next: Permissions**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-9.png)
- Nhập **S3** vào thanh tìm kiếm, sau đó chọn **AmazonS3ReadOnlyAccess** từ danh sách policies, sau đó click **Next: Review**. Policy này cho phép instance truy cập vào S3 để đọc và liệt kê bất cứ object nào trong tài khoản AWS của người dùng.
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-10.png)
- Nhập tên cho Role, ví dụ **`ec2-s3-read-only-role`**, sau đó click **Create role**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-11.png)
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-12.png)
- Trở lại tab đang tạo EC2, chọn button refresh ngay cạnh **Create new IAM role**, sau đó chọn role vừa tạo( ví dụ: **ec2-s3-read-only-role** )
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-13.png)
- Sao chép đoạn mã sau vào User Data. Đoạn mã này cho phép tự động cài đặt Apache web server và cấu hình cơ bản khi instance chạy lần đầu tiên. Sau đó ấn nut **Next: Add Storage**
```
#!/bin/bash
yum update -y
yum install -y httpd
service httpd start
chkconfig httpd on
groupadd www
usermod -a -G www ec2-user
chown -R root:www /var/www
chmod 2775 /var/www
find /var/www -type d -exec chmod 2775 {} +
find /var/www -type f -exec chmod 0664 {} +
```
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-14.png)
6. Ấn nút **Next: Add Tags**
7. Ấn nút **Next: Add Configure Security Group**
- Thêm các rule theo mục dưới. Chọn **Add rule** để thêm 1 rule.
  - Type: **SSH** | Source: **My IP**
  - Type: **HTTP** | Source: **Anywhere**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-15.png)
- Sau đó ấn nút **Review and Launch**
8. Xem lại các thông tin và ấn nút **Launch**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-16.png)
9. Tạo một key-pair mới, đặt tên ví dụ `**WAF-Lab**`, sau đó ấn nút **Download Key Pair** để tải key pair về. Cuối cùng ấn nút **Launch Instances**.
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-17.png)
{{% notice note %}} 
Nếu bạn đã có key pair sẵn rồi thì có thể chọn **Choose an existing key pair**, sau đó chọn key pair mà mình muốn và tích vào ô **I acknowledge that I have access to the corresponding private key file, and that without this file, I won't be able to log into my instance.**
{{% /notice %}}
![EC2LaunchNote](/images/1-Create-EC2/1-Create-EC2-note-1.png)
10. Chọn **View Instance**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-18.png)
11. Chờ một vài phút để instance chuyển sang trạng thái **Running**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-19.png)
12. Ấn vào instance, copy DNS và mở nó trong browser để kiểm tra **Application test page**
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-20.png)
![EC2Launch](/images/1-Create-EC2/1-Create-EC2-21.png)
