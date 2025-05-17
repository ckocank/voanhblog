---
title: Home Lab Ep 2. Hardware Part 1 - Cable
date: 2025-03-22
draft: false
tags:
  - HomeLab
  - IoT
  - Cable
  - RJ45
  - Keystone
categories: HomeLabJourney
---
Ở đây có 2 loại chính là dây cáp đồng 8 sợi và dây quang, do dây quang nhà mạng sẽ cung cấp nên chúng ta không phải lo về vấn đề đấy. Vậy chọn loại dây cáp mạng cho gia đình như thế nào? Không phải chúng ta cứ mua dây xịn nhất là tốt nhất, ở đây chúng ta sẽ ưu tiên chọn dây phù hợp nhất.

Đầu tiên hãy liệt kê một số loại dây cáp mạng 8 lõi 4 cặp xoắn và công dụng của chúng.
- **Dây cat5** - 100MHz - 100mbps: dây này chúng ta không dùng và các chuẩn từ cat5 chở xuống cũng không dùng do dây mạng đa phần sẽ đi âm tường nên việc thay đổi trong tương lai là rất khó khăn. Cộng thêm việc tốc độ mạng kia thì quá chậm ở thời điểm hiện tại và chi phí giữa cat5 và cat 5e chênh nhau không đáng kể nên ông nào tư vấn cái này thì bye luôn nhé.
- **Dây cat5e** - 100MHz - 1G: dây này dùng tốt nhất cho việc chạy camera mặc dù camera chỉ cần 100mbps thôi nhưng cũng nên đi dây này cho việc update trong tương lai nữa. Ngoài ra để tiết kiệm thì dùng dây này làm dây wifi và dây LAN âm tường cũng được (do tốc độ tối đa có thể lên tới 2.5G) nhưng nếu có điều kiện hãy chọn các loại dưới đây.
- **Dây cat6**: chúng ta có 3 loại dây cat6 đó là cat6 / cat6A / cat6e trong đó cat 6A là loại chúng ta nên chọn cho hệ thống mạng 10G. 
	- Nhược điểm của dây cat6 so với cat6A là chỉ hỗ trợ 10G lên tới 55m, còn 2.5G và 5G thì full 100m. 
	- Còn cat6e này là do mấy nhà sản xuất họ tự nghĩ ra, cat6e hoạt động ở 550MHz cao hơn 500MHz của cat6A, tần số càng cao càng tốt nhưng sẽ có nhiều yếu tố khác ảnh hưởng tới tốc độ mạng hơn là tần số hoạt động của dây.
- Các dây từ cat7 trở lên thì không nên chọn do chi phí cao và tính thực tiễn gần như không có.

Các loại dây mạng như trên còn chia được thêm ra 2 kiểu nữa là có bọc chống nhiễu (S/FTP, F/UTP) và không có chống nhiễu (UTP). Cáp mạng có vỏ bọc sẽ sử dụng tốt nhất cho môi trường có khả năng bị nhiễu sóng vô tuyến hoặc nhiễu điện từ. Các tình huống cần có cáp mạng chống nhiễu bao gồm khi chạy cáp bên ngoài trời trên mặt đất, gần bảng điện cao thế hoặc hệ thống dây điện, và dọc theo hệ thống dây điện AC thông thường bên trong tường. Các bạn hãy lưu ý rằng khi sử dụng dây cáp này bắt buộc các bạn phải có tiếp địa (thông thường sẽ đấu tiếp địa vào patch panel). Nếu không có tiếp địa thì **tuyệt đối không** sử dụng loại này nhé! Vậy nên ở phần trước mình có nói về việc đi dây mạng và dây điện ở cạnh nhau cần có quy chuẩn như thế nào. Nếu có tiếp địa tốt và dây mạng bị bắt buộc đi chung ống với dây điện thì hãy sử dụng loại có chống nhiễu này. Dây có chống nhiễu sẽ đắt hơn, thi công khó hơn (dây cứng và khó bấm) nên cần phải cân nhắc kỹ lưỡng.

Chiều dài tối đa của dây mạng là 100m, vượt qua khoảng cách này sẽ không đảm bảo mức tín hiệu nữa. Vậy tính như nào để tối đa 100m? Không phải là chúng ta cứ cắt đủ 100m dây mạng là sẽ đảm bảo mà ở đây, 100m được tính từ điểm đầu đến điểm cuối. Hãy xem hình minh họa dưới đây để tính được chính xác chiều dài dây cần có.

![cablelength](cablelength.png)

Sau khi kéo dây ta sẽ nối các thiết bị với nhau như nào? Cách đơn giản nhất là sử dụng hạt mạng 8p8c hay còn gọi là RJ45. Đây là phương án rẻ, dễ thi công và tiết kiệm nhất. Chúng ta chỉ cần 1 cái kìm bấm, 1 ít hạt mạng + đầu chụp và 1 bộ test mạng. Tất cả đều có thể dễ dàng mua được thông qua các sàn TMĐT với chi phí rất phải chăng. Ngoài ra khi bấm mạng hãy chọn loại hạt xuyên thấu cùng kìm bấm xuyên thấu sẽ giúp tiết kiệm rất rất nhiều thời gian thi công. Lưu ý khi chọn hạt mạng, hạt mạng không có chuẩn cat như các NSX hay quảng cáo nên chú ý chọn hạt mạng có chống nhiễu hoặc không có chống nhiễu, hạt mạng theo kích cỡ của dây mạng là 23 AWG hoặc 24 AWG, mặc định sẽ là 24 AWG. 

Cách bấm hạt RJ45 dễ thực hiện nhưng không phải là phương án tối ưu vì đầu nối RJ45 không đảm bảo do bụi và mảnh vụn có thể tích tụ trong đầu nối RJ45, dẫn đến kết nối kém và hiệu suất giảm. Vậy nên cách tốt nhất là hạn chế dùng hạt RJ45 mà hãy sự dụng keystone jack (hiểu nôm na là đầu nối RJ45 cái) hoặc toolless RJ45 connector (đầu nối RJ45 đực không cần kìm bấm). Đặc điểm của 2 loại này là bên trong các đầu nối sẽ có 1 cái pcb nhỏ, pcb này giúp các đầu kết nối giảm tình trạng cross talk (nhiễu tín hiệu). Thật ra việc nhiễu tín hiệu này thường ảnh hưởng tới hệ thống 10G còn các hệ thống dưới 10G thì không đáng kể lắm. 

Ngoài ra việc tự bấm đầu RJ45 cũng sẽ không đảm bảo (kể cả bấm đủ 8 dây) nếu không có thiết bị chuyên dụng để đo. Vì thế chúng ta nên sử dụng patch cable nếu cần 2 dầu nối RJ45 đực trong khoảng cách ngắn (dưới 5m).

Tóm lại cách đi dây chuẩn từ máy tính đến switch là như sau: 
Máy tính -> patch cable (x) -> keystone jack (hạt mạng âm tường) -> cat 6A (y) -> keystone jack (patch panel) -> patch cable (z) -> switch. 
Trong đó x + y + z <= 100m.