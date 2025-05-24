---
title: Home Lab Ep 1. Preparation
date: 2025-03-15
draft: false
tags:
  - HomeLab
  - IoT
categories: HomeLabJourney
---
## Thiết Kế Hệ Thống Mạng Gia Đình Từ Con Số 0

Giả sử bạn đang bắt đầu từ con số 0: không có hạ tầng, cũng chưa có kinh nghiệm. Vậy khi xây dựng một căn nhà mới, bên cạnh bản thiết kế điện, bạn cũng nên có một bản thiết kế hệ thống mạng với các hạng mục sau:

- Vị trí đặt **tủ rack**.
    
- Vị trí đặt **modem** (có thể tích hợp trong tủ rack).
    
- Vị trí các **access point** (thiết bị phát Wi-Fi).
    
- Vị trí lắp **camera an ninh**.
    
- Vị trí các **thiết bị sử dụng mạng có dây** (PC, TV...).
    
- Vị trí các thiết bị **nhà thông minh** như công tắc, cảm biến.
    

Việc lập kế hoạch chi tiết từ đầu sẽ giúp thợ thi công kéo dây đúng cách, tránh phát sinh sửa chữa, bổ sung gây tốn công và khó chịu cho cả hai bên.

---

### Lựa Chọn Tủ Rack

![rack4u](/rack4u.png)

Tủ rack không chỉ dành cho server hay data center. Trong mạng gia đình, bạn chỉ cần một tủ rack nhỏ gọn (4U hoặc 6U) là đủ.

**Lợi ích:**

- **Quản lý tập trung** các thiết bị mạng.
    
- **Gọn gàng**, chuyên nghiệp.
    
- Tăng độ **ổn định và dễ bảo trì**.
    
- Và đặc biệt: “show hàng” với khách tới chơi!
    

Tủ rack chuẩn là loại **19 inch**, phổ biến và dễ tìm phụ kiện. Bạn có thể chọn:

- **Tủ 4U**: gọn gàng, đủ dùng.
    
- **Tủ 6U**: có không gian mở rộng về sau.
    

Chi phí tủ 4U dao động từ 600.000đ – 800.000đ, mua cũ chỉ khoảng 300.000đ – 400.000đ (tủ rack hầu như không hỏng, chỉ cần tránh mua tủ móp méo là được).

![10inchrack](/10inchrack.png)

Ngoài ra còn có **loại 10-inch rack**, nhỏ và đẹp nhưng phụ kiện khó kiếm. Nếu bạn có máy in 3D hoặc thích custom DIY thì có thể thử, còn không thì nên ưu tiên chuẩn 19 inch.

---

### Vị Trí Lắp Thiết Bị

Các thiết bị như **Wi-Fi và camera** nên kéo dây mạng sẵn **mà không cần dây điện**, vì chúng ta sẽ dùng công nghệ **PoE** (Power over Ethernet). Mình sẽ nói chi tiết về PoE trong bài khác, nhưng tóm lại: nó giúp bạn **quản lý tập trung thiết bị** và **tắt điện tầng mà không ảnh hưởng đến mạng**.

- **Wi-Fi** nên đặt ở trung tâm **khu vực sử dụng**, không nhất thiết ở trung tâm nhà. Mỗi tầng nên có ít nhất 1 AP riêng.
    
- Nếu không dùng AP gắn trần/tường, bạn có thể dùng **Wi-Fi âm tường**, ví dụ: [EAP230-Wall của Omada](https://www.omadanetworks.com/vn/business-networking/omada-wifi-wall-plate/eap230-wall/).
    
- **Camera** không bị giới hạn về số lượng. Nếu chưa lắp ngay, hãy **đi dây chờ**. Lắp ở cửa ra vào, hành lang... Lắp trong phòng hay không tùy nhu cầu riêng. Do server lưu trữ đặt tại nhà, **rủi ro bảo mật** sẽ thấp hơn đáng kể.
    

---

### Thiết Bị Nhà Thông Minh (IoT)

Tùy loại thiết bị, bạn cần cấp nguồn khác nhau. Với nhu cầu cơ bản như **công tắc, cảm biến, aptomat**, bạn nên:

- Ưu tiên thiết bị **dùng pin hoặc điện 220V**.
    
- Nếu dùng công tắc thông minh 220V, **nhớ bổ sung dây nguội (trung tính)**. Không nên dùng loại không cần dây nguội, vì loại này không tắt hẳn thiết bị và có thể ảnh hưởng độ bền.
    
- Để đồng bộ thiết kế, nên chọn **công tắc kiểu module** thay vì nguyên bộ hạt công tắc.
    
- Nếu bạn dùng **công tắc đảo chiều**, việc tích hợp sẽ phức tạp hơn và mình sẽ nói ở bài khác.
    
- Các **cảm biến dùng pin** thì chỉ cần dán lên trần. Nhưng loại **cảm biến âm trần** (ví dụ cảm biến hiện diện) thì cần **đưa vào bản vẽ trần và bản vẽ điện** để thi công đúng.
    

---

### Đặt Tủ Rack Ở Đâu?

Tủ rack là trung tâm kết nối.

- Nếu muốn **tiết kiệm dây**, hãy đặt **ở vị trí trung tâm** căn nhà.
    
- Nếu muốn **gọn gàng**, hãy đặt **trong kho hoặc tủ kỹ thuật**.
    
- Tủ nhỏ nên bạn có thể **treo tường**, sẽ gọn và dễ vệ sinh hơn đặt sàn.
    

---

### Đi Dây Mạng Như Thế Nào?

Kéo dây mạng đến:

- **Camera**.
    
- **Wi-Fi**.
    
- **TV, máy tính, bàn làm việc**, kể cả chưa dùng ngay. Đi dây từ đầu sẽ **tiết kiệm thời gian và chi phí về sau**.
    

Lưu ý:

- Không nên đi dây mạng **song song với dây điện** để tránh nhiễu. Khoảng cách tối thiểu nên là **20cm**, hoặc **sử dụng hai ống gen riêng biệt**, càng xa nhau càng tốt.
    
- Trong tầng, đi dây trong **ống gen điện chống cháy**, rồi tập trung về **hộp kỹ thuật**.
    
- Dây xuyên tầng nên đi trong **ống thoát nước uPVC D42**, dùng **tê thu xiên 45 độ** để dễ luồn dây và chia tầng.
    
- Dây kéo về tủ rack cần có **chiều dài vừa đủ**, tránh quá ngắn hoặc dư quá nhiều.
    
- **Không nên nối dây mạng**, nhất là với hệ thống 10G. Nếu cần, hãy thay dây nguyên đoạn.
    
- Gọi **nhà mạng kéo dây cáp quang** từ hộp kỹ thuật khu vực vào **thẳng tủ rack**.
    
- Dây mạng và dây quang **không được gập góc vuông 90°**. Nên uốn ống mềm cong tròn để **giảm suy hao và dễ kéo dây**.
    
- Nếu có kế hoạch **thêm đường truyền cáp quang**, hãy **để sẵn dây cước chờ** trong ống.
    

---

Trên đây là phần **chuẩn bị hạ tầng** cơ bản. Trong các phần tiếp theo, mình sẽ hướng dẫn cách **lựa chọn phần cứng**, từ router, switch đến thiết bị Wi-Fi và camera.