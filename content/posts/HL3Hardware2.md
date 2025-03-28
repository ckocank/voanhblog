---
title: Home Lab Ep 2. Hardware Part 2 - Modem/Router
date: 2025-03-22
draft: true
tags:
  - HomeLab
  - IoT
categories: HomeLabJourney
---
Modem là thiết bị giúp chúng ta giao tiếp ra thế giới bên ngoài. Router giúp chúng ta giao tiếp trong nhà. Thông thường các nhà mạng sẽ cấp cho chúng ta 1 cục Modem, cục này thường đảm nhiệm luôn vai trò làm Router. Thế nhưng chúng ta không nên kiêm nhiệm như thế do một số vấn đề sau:
- **Độ tùy biến thấp**. Các cục modem này chỉ có các chức năng cơ bản nhất do phần lớn người dùng không cần quá nhiều chức năng, thậm chí ngay cả các chức năng có sẵn nhiều người còn không dùng đến.
- **Vấn đề bảo mật**. Các cục modem tặng kèm thông thường sẽ không được update phần cứng thường xuyên dẫn tới việc dễ bị hacker tấn công nếu như có những lỗ hổng bảo mật chưa được vá (thậm chí nhà mạng còn không thèm update firmware luôn ý chứ).
- **Cấu hình thấp**. Các cục modem tặng kèm thường có cấu hình thấp nhằm tiết kiệm chi phí vì đây là thiết bị đi kèm gói cước, chúng ta đang "mượn" thiết bị theo hợp đồng, nếu chúng ta có làm mất hoặc hỏng thì nhà mạng người ta cũng chả quan tâm, thường là thế chứ theo hợp đồng thì phải đền đấy.

Theo ý kiến cá nhân mình thì các bạn không nên sử dụng cục Modem nhà mạng làm Router mà hãy sử dụng chúng như một chiếc Converter (chuyển đổi tín hiệu quang điện), thậm chí nếu có module GPON SFP thì ta bỏ luôn cục Modem đấy đi cũng được. 

Trên thị trường hiện nay có rất nhiều loại router khác nhau thì chúng ta sẽ chọn router như nào? Theo cấu hình và tính năng. Về cấu hình phần cứng, các yếu tố sau sẽ được cân nhắc:
- **Số cổng của router**. Về cơ bản thì chỉ cần 2 cổng là đủ, thế nhưng việc có nhiều cổng sẽ giúp ta có nhiều lựa chọn hơn. Ví dụ như thêm nhiều subnet khác nhau hoặc 
- **Tốc độ các cổng** 10/100/1000 hoặc cổng 2.5G/5G/10G.
- **Số cổng quang**, SFP/SFP+ port.
- **Số cổng PoE**.
- **Cấu hình CPU, RAM** (ảnh hưởng trực tiếp tới tốc độ mạng).
