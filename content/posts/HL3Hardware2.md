---
title: Home Lab Ep 2. Hardware Part 2 - Modem/Router
date: 2025-03-23
draft: false
tags:
  - HomeLab
  - IoT
categories: HomeLabJourney
---
## Modem và Router: Đừng Để "2 Trong 1" Làm Khó Bạn

Modem là thiết bị giúp chúng ta **kết nối ra thế giới bên ngoài**, còn router giúp các thiết bị **giao tiếp với nhau trong mạng nội bộ**. Thông thường, nhà mạng sẽ cung cấp cho bạn một thiết bị “2 trong 1” – tức là **modem tích hợp luôn router**. Tuy nhiên, theo kinh nghiệm cá nhân, bạn **không nên dùng combo này chính**, vì một vài lý do sau:

### Tại sao không nên dùng modem của nhà mạng làm router chính?

- **Độ tùy biến thấp**: Các modem do nhà mạng cấp chỉ có những tính năng cơ bản nhất, vì đa số người dùng phổ thông chẳng cần nhiều. Ngay cả các tính năng có sẵn, nhiều người còn không đụng tới bao giờ.
    
- **Vấn đề bảo mật**: Những thiết bị này thường không được cập nhật firmware định kỳ. Có lỗ hổng bảo mật cũng không ai vá. Một số nhà mạng thậm chí còn... không thèm update luôn!
    
- **Cấu hình yếu**: Vì là thiết bị “cho mượn” đi kèm gói cước nên cấu hình thường rất thấp để tiết kiệm chi phí. Mất hay hỏng thì cũng chẳng sao – trừ khi bạn làm mất thật, lúc đó phải đền theo hợp đồng đấy nhé.
    

### Giải pháp?

Theo mình, bạn nên **chỉ dùng modem của nhà mạng như một bộ chuyển đổi tín hiệu (converter)** – hoặc nếu có module **GPON SFP** thì có thể **bỏ luôn modem**, cắm thẳng vào router riêng của bạn cũng được.

---

## Chọn Router Riêng: Phần Cứng Và Phần Mềm Cần Quan Tâm Gì?

Trên thị trường hiện có rất nhiều loại router, từ giá rẻ cho đến thiết bị chuyên nghiệp. Khi chọn, bạn cần xem xét **cả cấu hình phần cứng lẫn phần mềm**.

### Cấu hình phần cứng

- **Số cổng mạng**: Thường chỉ cần 2 cổng là đủ, nhưng nếu muốn chia subnet, tách VLAN hoặc cắm nhiều thiết bị thì càng nhiều cổng càng tốt.
    
- **Tốc độ các cổng**: 10/100/1000 Mbps, hoặc cao hơn như 2.5G/5G/10G.
    
- **Cổng quang (SFP/SFP+)**: Quan trọng nếu bạn dùng kết nối tốc độ cao hoặc mạng doanh nghiệp nhỏ.
    
- **Cổng PoE**: Hữu ích nếu bạn dùng thiết bị như camera IP, access point…
    
- **CPU, RAM**: Ảnh hưởng trực tiếp đến hiệu suất mạng.
    
- **Switch chip**: Hỗ trợ các tính năng nâng cao như L3 Hardware Offloading.
    

### Phần mềm & tính năng

Hầu hết các router hiện nay đều hỗ trợ các tính năng cơ bản như **DHCP, TCP/IP, DNS**... Tuy nhiên, với người thích vọc và tối ưu mạng thì hai cái tên phổ biến là **Mikrotik** và **pfSense/OPNsense**.

---

## Dành Cho Người Mới: Đừng Cấu Hình “Chay”, Hãy Lên YouTube!

Nếu bạn chưa có nhiều kinh nghiệm về mạng, hoặc lần đầu cấu hình router, **hãy tìm đúng video hướng dẫn trên YouTube** (nhớ đúng phiên bản firmware nhé!). Làm sai một bước nhỏ thôi là:

- Không vào được internet
    
- Thậm chí không truy cập được vào router (do đặt sai firewall rule hoặc đổi mật khẩu rồi quên...)
    

### Các bước cấu hình cơ bản (giao diện có thể khác nhau, nhưng logic thì giống nhau hết):

1. **Đổi tài khoản đăng nhập mặc định** – không bao giờ dùng `admin/admin`
    
2. **Thiết lập kết nối WAN**:
    
    - Dùng **PPPoE** nếu modem đã chuyển sang bridge mode
        
    - Hoặc **Static IP/DHCP** nếu dùng trực tiếp modem nhà mạng
        
3. **Thiết lập mạng LAN**: IP nội bộ, DHCP server, dải IP cấp phát...
    
4. **Firewall rules**:
    
    - Ví dụ: pfSense mặc định block all, còn Mikrotik thì allow all
        
    - Phải đọc tài liệu chính xác để tránh "chặn nhầm"
        
5. **VLAN**: Tạo các mạng LAN ảo để tách riêng thiết bị IoT, camera, hoặc mạng khách
    
6. **Chặn quảng cáo (Ads Block)**:
    
    - Dùng DNS filter như AdGuard Home giúp **lướt web sạch hơn, nhanh hơn, an toàn hơn**
        
    - Tránh được quảng cáo lừa đảo – đặc biệt hữu ích trong nhà có người già, trẻ nhỏ
        

---

## Mikrotik vs pfSense/OPNsense – Mỗi Loại Có Gì Hay?

Mình đã từng dùng cả hai và đây là đánh giá cá nhân:

### Mikrotik

**Ưu điểm:**

- Cộng đồng người dùng tại Việt Nam đông đảo
    
- Thiết bị dễ mua bán, thanh khoản tốt
    
- Giá hợp lý, phần cứng tối ưu cho phần mềm
    
- Có thể chạy OS riêng (RouterOS) trên PC, cần license
    

**Nhược điểm:**

- Khó tiếp cận cho người mới, cần thực hành nhiều
    
- Dù rẻ hơn thiết bị doanh nghiệp nhưng vẫn đắt hơn PC router tự build
    
- Một số tính năng nâng cao cần mua thêm license
    

### pfSense / OPNsense

**Ưu điểm:**

- Giao diện dễ dùng, logic rõ ràng
    
- Tận dụng tốt phần cứng máy tính cũ
    
- Là hệ điều hành mã nguồn mở, cập nhật thường xuyên
    
- Cộng đồng quốc tế lớn, nhiều plugin hỗ trợ
    

**Nhược điểm:**

- Không chạy được trên ARM (chỉ hỗ trợ x86, bản community)
    
- Nếu phần cứng "dị" thì phải kiểm tra driver trước (do dựa trên FreeBSD)
    
- Tài liệu, video hướng dẫn đa phần là tiếng Anh
    

---

## Thiết Bị Mình Đang Dùng

Hiện tại mình đang dùng một con **Mikrotik RB4011**, mua cũ nên giá rất ổn. Con này có hỗ trợ **container**, nên mình cài luôn **AdGuard Home** để chặn quảng cáo – cực kỳ tiện lợi, hiệu quả cao.

---

Nếu bạn có đam mê mày mò về mạng gia đình, tối ưu hiệu năng và bảo mật, thì việc tách biệt modem và router, cũng như tự cấu hình một router chuyên nghiệp là một bước tiến rất đáng thử. Mình sẽ có thêm các bài chi tiết về DNS filter, AdGuard, hoặc hướng dẫn cài pfSense/Mikrotik từ A-Z trong tương lai.