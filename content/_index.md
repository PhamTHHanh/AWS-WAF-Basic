+++
title = "CƠ BẢN VỀ WEB APPLICATION FIREWALL VỚI EC2"
date = "`r Sys.Date()`"
weight = 1
chapter = false
+++
# CƠ BẢN VỀ WEB APPLICATION FIREWALL VỚI EC2
#### Tổng quan
Ở bài lab này hứng dẫn với Web application firewall cơ bản để bảo vệ EC2 instance workload bởi các cuộc tấn công thông qua mạng. Chúng ta sẽ sử dụng AWS Management Console và AWS CloudFormation để hướng dẫn cách bảo vệ một ứng dụng web chạy trên EC2. 
![LabDiagram](/images/LabWAFBasic.png)
#### Web Application Firewall
AWS WAF là một tưởng lửa cho ứng dụng web cho phép người dùng giám sát các yêu cầu HTTP/HTTPS được chuyển tiếp đến CloudFront, Amazon API Gateway REST API,  Application Load Balancer, hoặc AWS AppSync GraphQL API. AWS WAF cũng cho phếp đồng kiểm soát quyền truy cập vào nội dung của bạn. Dựa trên các điều kiện mà bạn chỉ định, như giá trị của chuỗi truy vấn hoặc địa chỉ IP của các yêu cầu. Các dịch vụ được liên kết với WAF phản hồi các yêu cầu hoặc với mã trạng thái 403 (Forbidden).

- Web ACLs: Sử dụng web access control list để bảo vệ những AWS resources. Bạn tạo web ACL và định nghĩa chiến lược bảo vệ tài nguyên bằng cách thêm các Rule.
- Rules: Mỗi Rule định nghĩa tiêu chí kiểm tra và hành động cần thực hiện nếu một yêu cầu web đáp ứng tiêu chí. Có thể cấu hình các quy tắc để chặn các yêu cầu phù hợp, cho phép chúng thông qua, đếm chúng hoặc chạy các điều khiển CAPTCHA đối với chúng.
- Rules groups: Bạn có thể sử dụng các rule riêng lẻ hoặc sử dụng lại các nhóm rule. CAWS Managed Rules và AWS Marketplace sellers cung cấp các rule được quản lý để bạn sử dụng. Cũng có thể xác định các nhóm quy tắc riêng cho mình.

#### Nội dung
1. [Tạo EC2 instance](1-create-ec2)
2. [Tạo AWS WAF Rules với CloudFormation](2-create-waf-rules-with-cloudformation)
3. [Tạo ALB tích hợp với WAF](3-create-abl-waf-intergation)
4. [Dọn dẹp tài nguyên](4-clean)
