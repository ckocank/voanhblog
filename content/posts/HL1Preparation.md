---
title: Home Lab Ep 1. Preparation
date: 2025-03-15
draft: false
tags:
  - HomeLab
  - IoT
categories: HomeLabJourney
---
Mình sẽ giả sử mọi người bắt đầu với con số 0. Tức là hạ tầng chưa có, kinh nghiệm cũng không. 

Với một căn nhà mới bắt đầu hoàn thiện, ngoài bản thiết kế các thiết bị điện hãy thêm một bản thiết kế các thiết bị mạng bao gồm các thiết bị sau:
- Vị trí đặt tủ rack.
- Vị trí đặt modem, có thể tích hợp luôn vào tủ rack cho gọn.
- Vị trí các thiết bị access point (cục wfi).
- Vị trí lắp camera an ninh.
- Vị trí các thiết bị sử dụng mạng có dây (máy tính, tivi).
- Vị trí lắp các thiết bị thông minh như công tắc, cảm biến.
Cần phải có mô tả chi tiết ngay từ đầu để khi thi công các bác thợ còn kéo dây, hay biết cách đi dây sao cho đúng. Tránh việc làm rồi mới nghĩ ra thêm vào gây sự khó chịu cho cả 2 bên.

### Lựa chọn tủ rack.
![rack4u](/rack4u.png)
Có cần lắp tủ rack trong gia đình không? Tủ rack thường gắn liên đến các server, data center, to cồng kềnh, ồn ào, tốn điện, chính vì thế nên nhiều người không nghĩ đến việc lắp tủ rack trong nhà. Nhưng với tủ rack mạng gia đình thì ta chỉ cần 1 tủ  bé bé xinh xinh, khoảng 4-6u là đủ rồi. Lắp tủ rack đầu tiên sẽ giúp chúng ta quản lý tập trung các thiết bị, sau đó là sự gọn gàng, cuối cùng là sự chuyên nghiệp. Đặc biệt các bác không làm IT mà tự lắp tủ rack thì khách đến nhà chơi có thể tự hào giới thiệu là hệ thống mạng gia đình tự tay thiết kế xong chém gió đủ thứ luôn.
Tủ rack tiêu chuẩn là tủ rack 19 inch. Các bạn hãy chọn tủ 4u nếu muốn gọn gàng, tủ 6u nếu muốn mở rộng các thiết bị trong tương lai. Chi phí cho tủ rack cũng khá dễ chịu với tủ 4u (6-800k). Các bác mà đi săn tủ cũ thì còn rẻ nữa, chỉ khoảng 3-400k là có rồi. Vì tủ rack không có gì để hỏng nên mua cũ không sao nhé, tủ cũ xấu xấu bẩn bẩn lau đi là được, đừng chọn tủ móp méo là ok.

![10inchrack](/10inchrack.png)
Ngoài ra thì còn loại 10 inch rack này nữa mà loại này khá hiếm và khó mua phụ kiện nên chỉ dành cho các bạn nào chịu chơi thôi chứ mình không ưu tiên lắm dù nó gọn và đẹp lắm. Đôi khi mua đồ tìm tai rack chuẩn 19 inch đã khó rồi lại còn chơi đồ không đúng chuẩn còn khó nữa. Cơ mà ai có máy in 3D thì chơi cái này cũng ok đấy.

### Vị trí đặt thiết bị
Các thiết bị như wifi, camera hãy kéo dây mạng cho chúng và không cần dây điện. Lý do là bởi chúng ta sẽ sử dụng PoE nên không cần kéo dây điện nữa. Về cơ chế hoạt động của wifi và camera thông qua PoE mình sẽ có bài giải thích riêng nên tóm tắt lại là làm như vậy sẽ giúp chúng ta quản lý tập trung các thiết bị mạng và có thể tắt cầu giao các tầng nhưng mà không ảnh hưởng tới Internet.
- Wifi sẽ đặt ở trung tâm của nơi sẽ có nhiều thiết bị sử dụng mạng không dây nhất, thay vì đặt ở trung tâm của nhà. Mỗi tầng cũng nên có wifi riêng.
- Nếu không muốn sử dụng loại wifi ốp trần hay ốp tường thì cũng có loại [wifi âm tường](https://www.omadanetworks.com/vn/business-networking/omada-wifi-wall-plate/eap230-wall/). Loại này rất nhỏ ngọn và chỉ to hơn mặt công tắc điện một tí thôi nên không ảnh hưởng tới thiết kế trần có sẵn. 
- Camera sẽ không bị giới hạn về số lượng, có thể nếu chưa lắp luôn thì đi dây mạng chờ ra chỗ đó là được. 
- Vị trí lắp sẽ là những nơi cơ bản như trước cửa nhà hay hành lang. Còn việc lắp camera ở trong các phòng hay không sẽ tùy lựa chọn mỗi gia đình, vì là server camera được đặt ở ngay tại nhà nên rủi ro về an toàn dữ liệu cũng sẽ giảm đi đáng kể.

Với các thiết bị IoT, tùy thiết bị sẽ có yêu cầu cấp nguồn khác nhau, để thuật tiện nhất thì mình chọn các thiết bị chạy pin hoặc nguồn AC 220V. Ở đây, các thiết bị cơ bản bao gồm công tắc, cảm biến và aptomat. 
- Các loại công tắc sử dụng điện AC 220V sẽ cần phải có dây nguội (dây trung tính) nên phải lưu ý điều này. Có thể chọn loại công tắt thông minh không cần dây nguội nhưng không nên sử dụng loại này, vì công tắt này sẽ không tắt hẳn thiết bị điện mà vẫn phải truyền 1 ít điện để công tắc có thể hoạt động được.
- Để giữ được sự đồng nhất trong thiết kế của ngôi nhà thì mình sẽ chọn loại công tắc thông minh kiểu module thay vì loại công tắc có cả hạt công tắc.
- Với các loại công tắc đảo chiều muốn tích hợp công tắc thông minh thì sẽ phức tạp hơn một tí nên mình sẽ đề cập ở bài viết sau.
- Các loại cảm biến chạy pin thì chỉ đơn giản chỉ cần dán lên trần là được nhưng những loại cảm biến cơ thể người âm trần yêu cầu khoét lỗ thạch cao thì phải đưa vào bản vẽ trần + bản vẽ điện.

Tủ rack là nơi tập trung của tất cả nên nếu muốn tiết kiệm dây mạng nhất thì có thể đặt ở trung tâm của cả nhà, nếu muốn gọn gàng thì nên đặt trong kho. Do tủ này khá bé nên là treo tường sẽ tốt hơn việc mình đặt trực tiếp dưới sàn nhà. 

### Nên đi dây mạng như thế nào
Ngoài việc kéo đến các vị trí camera và wifi thì cũng cần có các ổ mạng cắm dây cho TV, máy tính, bàn làm việc do việc kéo dây sau khi hoàn thiện tổng thể sẽ khó khăn hơn rất nhiều, kể cả nếu chưa có nhu cầu sử dụng trong hiện tại.
- Có thể với hệ thống mạng gia đình việc này không quá quan trọng nhưng dây mạng không nên chạy song song với dây điện do nhiễu tín hiệu. Về lý thuyết thì khoảng cách tối thiểu là 20cm nhưng thực tế thi công hệ thống điện và mạng trong gia đình sẽ rất khó đạt tiêu chuẩn như vậy. Nên ít nhất hãy sử dụng 2 ống gel khác nhau cho 2 loại dây và để chúng cách nhau xa nhất có thể.
- Dây ở trong các tầng sẽ được đi trong ống gel điện chống cháy sau đó tập trung vào hộp kỹ thuật để đi vào tủ rack. Trong hộp kỹ thuật để tiết kiệm hãy dùng ống thoát nước uPVC d42 để chạy qua các tầng và sử dụng tê thu xiên 45 độ để chia dây qua từng tầng.
- Dây mạng kéo đến tủ rack cần phải có chiều dài hợp lý, tránh kéo việc kéo thiếu hoặc thừa quá nhiều dây. 
- Dây mạng hoàn toàn có thể nối được nhưng chúng ta không nên nối dây mạng để đảm bảo tín hiệu (với hệ thống 10G) và đỡ đau đầu nếu phát sinh lỗi. 
- Hãy gọi tổng đài lắp đặt internet của nhà mạng để họ có phương án kéo dây cáp quang từ hộp kỹ thuật khu vực vào trong nhà khi thi công phần này. Nên kéo dây cáp quan vào luôn tủ rack cho tiện việc quản lý.
- Dây mạng và dây quang cần hạn chế gập vuông góc 90 độ. Các khúc cần vuông góc thì hãy nhờ thợ uốn ống cho cong nhất có thể. Nhất là với các sợi dây quang, gấp khúc càng nhiều thì suy hao sẽ càng lớn. Việc uốn ống cong cũng sẽ giúp kéo dây dễ hơn. Nếu có dự định kéo thêm đường truyền cáp quang trong tương lai để cân bằng tải thì nên để thêm dây cước chờ.

Phần chuẩn bị ban đầu chỉ có vậy thôi, ở các phần sau chúng ta sẽ đến với công việc lựa chọn phần cứng.
