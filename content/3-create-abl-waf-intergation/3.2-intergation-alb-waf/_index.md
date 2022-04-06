+++
title = "Configure ALB với WAF"
date = "`r Sys.Date()`"
weight = 2
chapter = false
pre = "<b>3.2 </b>"
+++
Sau khi tạo Application load balancer, chúng ta kết nối nó với WAF đã được tạo trong phần 2.
1. Đăng nhập vào trang quản trị AWS Management Console và tìm WAF trên thanh tìm kiếm
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-1.png)
2. Nhấn nút **Go to AWS WAF**
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-2.png)
3. Nhấn vào **Switch to AWS WAF Classic** 
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-3.png)
4. Chọn Region tương ứng với Region mà bạn chạy CloudFormation, sau đó hiện thị danh sách Web ACLs. Chọn web ACL đã tạo (WAFLabReg-WebACL1)
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-4.png)
5. Nhấn tab **Rule**
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-5.png)
6. Kéo xuống dưới và nhấn nút **Add association** tại mục **AWS resources using this web ACL**
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-6.png)
7. Chọn **Application Load Balancer** cho **Resource type**, sau đó chọn load balancer tạo ở bước 3.1 cho mục **Resource**. Kết thúc bằng việc nhấn nút **Add**
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-7.png)
8. Application load balancer xuất hiện trong bảng **AWS resources using this web ACL**
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-8.png)
9. Giờ bạn có thể kiểm tra quyền truy cập bằng cách nhập DNS của load balancer vào trình quyệt web.
![WAFSearch](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-9.png)
10. Để kiểm tra hoạt động của WAF, thêm condition cho rule: **WAFLabReg-WhitelistRule1**
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-10.png)
11. Nhấn vào nút **Edit Rule**
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-11.png)
12. Nhấn nút **Add condition** để thêm condition mới cho rule
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-12.png)
13. Cài đặt cho điều kiện cho rule
- Chọn điều kiện **originate from IP address in**
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-13.png)
- Chọn địa chỉ IP match condition
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-14.png)
- Nhấn vào **Edit** để thêm địa chỉ IP Address cho **WAFLabReg-WhitelistIPSet1**
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-15.png)
- Nhấn nút **Add IP addresses or ranges**
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-16.png)
- Nhập địa chỉ IP máy của bạn, sau đó nhấn nút **Add IP address or range**
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-17.png)
- Nhấn nút **Add**
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-18.png)
- Sau khi cài đặt địa chỉ IP xong trở lại trang thêm điều kiện cho rule, nhấn nút **Update**.
14. Làm lại bước số 9 nhiều lần
- Tại AWS WAF console, nhấn **Web ACLs** bên trái, sau đó chọn ACLs của bạn.
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-19.png)
- Sau đó kéo xuống dưới để thấy kết quả.
![WAFAddCondition](/images/3-Create-ALB-with-WAF/3-2-Intergate-ALB-WAF/3.2-Intergate-ALB-WAF-20.png)



