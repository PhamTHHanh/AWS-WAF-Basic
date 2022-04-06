+++
title = "Khởi tạo AWS WAF Rules"
date = "`r Sys.Date()`"
weight = 2
chapter = false
pre = "<b>2. </b>"
+++
Chúng ta sẽ khởi tạo một AWS WAF cơ bản dùng cho Application Load Balancer bằng AWS CloudFormation.
#### Khởi tạo AWS WAF bằng AWS CloudFormation
1. Đăng nhập vào trang quản trị AWS Management Console và tìm kiếm dịch vụ **CloudFormation**.
![CloudFormationSearch](/images/2-Create-WAF/2-Create-WAF-1.png)
2. Nhấn **Create Stack**
![StackCreate](/images/2-Create-WAF/2-Create-WAF-2.png)
3. Nhập **`https://s3-us-west-2.amazonaws.com/aws-well-architected-labs/Security/Code/waf-regional.yaml`** vào ô **Amazon S3 URL**, sau đó nhấn **Next**
![StackCreate](/images/2-Create-WAF/2-Create-WAF-3.png)
4. Nhập tên cho stack, ví dụ: **`lab-waf-regional`**
![StackCreate](/images/2-Create-WAF/2-Create-WAF-4.png)
5. Nhấn nút **Next**
![StackCreate](/images/2-Create-WAF/2-Create-WAF-5.png)
6. Xem lại thông tin của stack và ấn nút **Create Stack**
![StackCreate](/images/2-Create-WAF/2-Create-WAF-6.png)
7. Đợi stack chuyển status từ **CREATE_IN_PROGRESS** sang **CREATE_COMPLETE**.
![StackCreate](/images/2-Create-WAF/2-Create-WAF-7.png)
Vậy là bạn đã hoàn thành tạo WAF cơ bản bằng CloudFormation.

