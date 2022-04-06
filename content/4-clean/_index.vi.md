+++
title = "Dọn dẹp tài nguyên"
date = "`r Sys.Date()`"
weight = 4
chapter = false
pre = "<b>4. </b>"
+++
Chúng ta sẽ dọn dẹp tài nguyên theo thứ tự như sau:
1. Xoá Load balancer
  - Truy cập EC2 Management Console
  - Trên thanh điều hướng bên trái, chọn Load Balancers
  - Chọn Load Balancer liên quan tới bài lab.
  - Click Actions.
  - Click Delete.

2. Xoá target group
  - Truy cập EC2 Management Console
  - Trên thanh điều hướng bên trái, chọn Target Groups
  - Chọn Target Group liên quan tới bài lab.
  - Click Actions.
  - Click Delete.
  - Click Yes, delete

3. Terminate EC2 instance
  - Truy cập EC2 Management Console
  - Trên thanh điều hướng bên trái, chọn Intances
  - Chọn tất cả EC2 Instance liên quan tới bài lab.
  - Click Actions.
  - Click Manage Instance State.
  - Chọn Terminate.
  - Click Change State

4. Xoá AWS WAF stack
  - Truy cập CloudFormation Console
  - Chọn `lab-waf-regional` stack
  - Click nút **Action**, và sau đó click Delete Stack
  - Xác nhận stack, ấn nút **Yes, Delete**