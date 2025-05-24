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
Trong hệ thống mạng gia đình, chúng ta thường gặp hai loại dây phổ biến là **dây cáp đồng 8 sợi** và **dây quang**. Dây quang thường do nhà mạng cung cấp và lắp đặt sẵn, nên chúng ta không cần lo lắng nhiều. Vấn đề quan trọng là chọn loại dây cáp mạng **phù hợp nhất** cho nhu cầu sử dụng trong gia đình. Không phải cứ mua loại đắt tiền nhất là tốt – mà nên chọn đúng loại, đúng mục đích.

### Các loại dây cáp mạng phổ biến

Dưới đây là một số loại dây cáp đồng 8 lõi (4 cặp xoắn) và công dụng của chúng:

- **Cat5 – 100MHz – 100Mbps**: Gần như không còn ai dùng loại dây này nữa. Do tốc độ quá thấp và không phù hợp với nhu cầu hiện tại. Thêm vào đó, nếu dây được đi âm tường thì việc thay thế sau này rất khó khăn. Vậy nên nếu ai tư vấn dùng Cat5 thì bạn nên từ chối ngay.
    
- **Cat5e – 100MHz – 1Gbps**: Loại này rất phù hợp để chạy camera IP (mặc dù camera chỉ cần 100Mbps). Ngoài ra, cũng có thể dùng để đi dây LAN âm tường hoặc dây đến các bộ phát Wi-Fi. Tốc độ tối đa có thể đạt đến 2.5Gbps nếu thiết bị hỗ trợ. Nếu bạn muốn tiết kiệm thì Cat5e vẫn là lựa chọn ổn.
    
- **Cat6 / Cat6A / Cat6e**:
    
    - **Cat6** hỗ trợ 10Gbps ở khoảng cách dưới 55m, còn 2.5G và 5G thì đạt đủ 100m.
        
    - **Cat6A** là lựa chọn nên cân nhắc nếu bạn muốn xây dựng hệ thống mạng 10Gbps ổn định trong phạm vi 100m.
        
    - **Cat6e** là loại do một số hãng tự đặt tên, hoạt động ở tần số 550MHz – cao hơn một chút so với Cat6A (500MHz), nhưng hiệu năng thực tế còn phụ thuộc vào nhiều yếu tố khác.
        
- **Từ Cat7 trở lên**: Không khuyến khích dùng vì chi phí cao, chuẩn đầu nối không phổ biến, và hiệu quả mang lại không đáng kể so với Cat6A.
    

### Dây chống nhiễu và không chống nhiễu

Dây mạng còn chia thành hai loại:

- **UTP**: không có lớp chống nhiễu.
    
- **FTP, S/FTP, F/UTP...**: có lớp chống nhiễu, phù hợp với môi trường có nhiều nhiễu điện từ hoặc sóng vô tuyến – ví dụ như đi dây ngoài trời, gần tủ điện, hay đi chung ống với dây điện.
    

Tuy nhiên, nếu bạn sử dụng dây có lớp chống nhiễu **bắt buộc phải có tiếp địa** (thường được nối tại patch panel). Nếu không có tiếp địa, **tuyệt đối không nên dùng loại dây này**, vì dễ gây phản tác dụng – nhiễu còn nặng hơn.

Việc chọn dây chống nhiễu cần cân nhắc kỹ vì:

- Giá cao hơn.
    
- Dây cứng, khó thi công, khó bấm đầu.
    

### Về chiều dài dây mạng

Chiều dài tối đa khuyến nghị cho dây mạng là **100m**, được tính **từ đầu thiết bị này đến đầu thiết bị kia**, bao gồm toàn bộ đoạn dây đi qua âm tường, patch panel, hạt mạng và dây nối.

> Lưu ý: Không phải cắt 100m dây là được — tổng chiều dài _thực tế sử dụng_ phải ≤ 100m.


![cablelength](/cablelength.png)


### Kết nối các thiết bị với nhau

Có 3 cách phổ biến để kết nối dây mạng:

1. **Bấm hạt mạng RJ45 (8P8C)**:
    
    - Cách rẻ và dễ nhất, chỉ cần kìm bấm, hạt mạng, chụp đầu và bộ test mạng.
        
    - Nên dùng hạt **xuyên thấu** để dễ canh chỉnh và tiết kiệm thời gian.
        
    - Chọn hạt theo cỡ dây: phổ biến là **24 AWG**, dây to hơn thì dùng hạt 23 AWG.
        
    - Tuy nhiên, RJ45 dễ bị bụi, oxi hóa, dẫn đến tiếp xúc kém – không lý tưởng về lâu dài.
        
2. **Sử dụng Keystone Jack hoặc Toolless RJ45 Connector**:
    
    - Chuyên nghiệp hơn. Có mạch PCB giúp giảm nhiễu (cross talk).
        
    - Dễ bảo trì, dễ thay thế.
        
    - Thi công phức tạp hơn một chút nhưng rất đáng đầu tư, đặc biệt nếu bạn đi dây âm tường.
        
3. **Sử dụng Patch Cable (dưới 5m)**:
    
    - Nếu bạn chỉ cần kết nối tạm thời hoặc ở khoảng cách ngắn, patch cable là giải pháp nhanh, ổn định, không cần bấm đầu.
        

> Ngoài ra, việc **tự bấm dây RJ45** không đảm bảo độ ổn định nếu không có thiết bị test chuyên dụng. Với hệ thống mạng dưới 10G thì vấn đề nhiễu có thể không nghiêm trọng, nhưng nếu bạn hướng tới mạng 10G thì nên ưu tiên kết nối chắc chắn như Keystone.

### Sơ đồ đi dây mạng chuẩn

Đây là cấu trúc đi dây mạng lý tưởng từ thiết bị đầu cuối (máy tính) đến switch:

java

CopyEdit

`Máy tính → Patch cable (x) → Keystone Jack (âm tường) → Dây mạng âm tường Cat6A (y) → Patch Panel (Keystone) → Patch cable (z) → Switch`

Trong đó, tổng chiều dài của **x + y + z ≤ 100m**.

---

Nếu bạn cần thêm hình minh họa hoặc tư vấn chi tiết cho từng trường hợp cụ thể (nhà mới xây, cải tạo, đi dây trần, v.v...), cứ hỏi mình nhé.