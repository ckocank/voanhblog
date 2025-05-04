---
title: Home Lab Ep 2. Hardware Part 2 - Modem/Router
date: 2025-03-23
draft: false
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
- Switch chip, cái này cho mấy tính năng nâng cao như L3 Hardware Offloading hoặc switch hết cổng thì cắm luôn vào router.

Về phần mềm, các chức năng cơ bản của router đều như nhau (DHCP, TCP/IP, DNS, etc). Do mình chỉ có kinh nghiệm sử dụng Mikrotik và pfSense/OPNsense nên mình sẽ nói về 2 loại này thôi.

Với những người không có kiến thức cơ bản về mạng máy tính hay kể cả có nhưng lần đầu làm quen thì chắc chắn các bạn nên lên YouTube xem cách config thiết bị của mình rồi. Hãy nhớ tìm đúng phiên bản nhé, đặc biệt là phải làm theo đúng các bước nếu nhỡ bỏ 1 bước nào đó quan trọng là thôi khỏi vào mạng luôn đó, tệ nhất và vừa không vào được mạng lại còn không vào được router (do set up firewall rules sai hoặc đổi mật khẩu xong quên) thì mất công reset lại lắm.

Tóm lại có mấy bước cơ bản sau mà router nào cũng giống nhau chỉ khác cái giao diện nè:
- Đổi tên đăng nhập và mật khẩu. Không bao giờ được đặt là admin admin nhé.
- Cài đặt WAN. Có 2 lựa chọn là quay PPPoE nếu dùng modem với chức năng bridge. Hoặc set up static IP/ DHCP nếu cắm trực tiếp vào modem nhà mạng mà không config lại. 
- Cài đặt LAN. Cài IP cho mạng LAN sau đó cài đặt DHCP server.
- Cài đặt Firewall rules. Cái này thì tuỳ OS nhé, pfSense mặc định là block all, có cái mặc định allow all nên phải xem tài liệu mới biết được.
- Cài VLAN. Cái này nâng cao hơn 1 tí, đại loại là mình tạo nhiều mạng LAN ảo khác nhau để quản lý traffic cho dễ. Kiểu như muốn chặn thiết bị camera, IoT kết nối internet. Thêm mạng cho khách để họ không truy cập được mạng nội bộ.
- Cài Ads block, chặn quảng cáo. Cái này thì siêu tiện luôn nhé. Gần như là chặn hết các loại quảng cáo trên web, tất nhiên là trừ quảng cáo native hoặc YouTube. Chặn quảng cáo còn giúp trang web load nhanh hơn, xem các nội dung tập trung hơn đỡ bực mình. Đặc biệt là chặn các quảng cáo lừa đảo tránh việc trong nhà có người già trẻ em tò mò bấm vào. Nếu dùng DNS serv của quad9 còn an toàn nữa cơ. Mình sẽ có bài chia sẻ riêng về vấn đề này sau.

Về lựa chọn mik (Mikrotik) hay sen (pfSense/opnSense) thì sau đây là trải nghiệm của mình. 
- Điểm cộng của mik: 
	- Cộng đồng người sử dụng ở Việt Nam khá nhiều, hơn sen là chắc chắn. 
	- Thiết bị mua đi bán lại dễ.
	- Khá rẻ so với các dòng thiết bị doanh nghiệp không đến từ Trung Quốc.
	- Phần cứng tối ưu với phần mềm.
- Điểm trừ của mik:
	- Khá khó cho người không biết gì. Cần phải thực hành nhiều mới thạo được.
	- Rẻ hơn một số thiết bị doanh nghiệp nhưng đắt hơn các thiết bị PC router tự build.
	- Có thể chạy OS riêng trên PC router nhưng cần license. Cái này cũng là điểm cộng luôn.
- Điểm cộng của sen:
	- Dễ dùng hơn mik.
	- Tận dụng tốt phần cứng máy tính cũ.
	- Hệ điều hành mã nguồn mở.
	- Cộng đồng tốt hơn (ý kiến cá nhân).
- Điểm trừ của sen:
	- Không chạy được arm cpu mà chỉ chạy được x86 thôi (bản community).
	- Các phần cứng phổ thông đều có driver cho freebsd nhưng dùng phần cứng dị cần kiểm tra độ tương thích trước.
	- Video hướng dẫn toàn tiếng Anh.

Sau khi đã dùng qua cả 2 thì hiện tại mình đang dùng 1 con mikrotik rb4011. Con này mình mua cũ nên giá cũng hợp lý. Cũng may mà con này có hỗ trợ container nên cài adguard được. 

