+++
title = "Tạo Application Load Balancer"
date = "`r Sys.Date()`"
weight = 1
chapter = false
pre = "<b>3.1 </b>"
+++
Chúng ta sẽ tạo một Application Load Balancer với target group gồm EC2 instance tạo ở bước 1.
1. Mở Amazon EC2 console tại: https://console.aws.amazon.com/ec2/, sau đó bấm vào **Load Balancers** ở menu bên trái.
![ALBOpen](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-1.png)
2. Nhấn nút **Create** của phần Application Load Balancer
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-2.png)
3. Nhập tên cho load balancer, ví dụ **`lab-alb`**.
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-3.png)
4. Tiếp theo chọn tất cả AZ của Region của bạn.
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-4.png)
5. Xoá default security và nhấn vào **Create a new security** để tạo SG cho ALB
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-5.png)
6. Nhập name cho SG, ví dụ **`lab-sg`**. Sau đó thêm rule có **Port: 80** và **Source: Anywhere IPv4**
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-6.png)
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-7.png)
7. Nhấn **Create** để tạo SG. Sau đó trở lại màn hình đang tạo ALB
8. Nhấn nút refresh và chọn SG mà chúng ta vừa tạo.
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-8.png)
9. Kéo xuống dưới phần **Listeners and routing**, nhấn **Create target group** để tạo target group mới
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-9.png)
10. Nhập tên cho target group, ví dụ `WAF-TG`.
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-10.png)
11. Ấn **Next**. Từ danh sách instance, nhấn vào check box của instance mà chúng ta đã tạo, sau đó ấn nút **Include as pending below**.
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-11.png)
12. Ấn nút **Create target group**.
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-12.png)
- Vậy là chúng ta đã tạo xong một target group
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-13.png)
13. Trở lại màn hình đang tạo ALB, nhấn nút refresh và chọn target group mà chúng ta vừa tạo.
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-14.png)
14. Các thông số khác để mặc định, kéo xuống và nhấn nút **Create load balancer**
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-15.png)
- Nhấn **View load balancer**
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-16.png)
15. Vậy chúng ta đã tạo xong một load banlancer, copy DNS của nó ra broswer để chạy thử.
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-17.png)
![ALBCreate](/images/3-Create-ALB-with-WAF/3-1-Create-ALB/3-1-Create-ALB-18.png)