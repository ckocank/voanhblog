---
title: Design League of Legend
date: 2025-05-18
draft: false
tags:
  - Interview
  - SystemDesign
categories: Interview Experience
---
## Riot và Hành Trình Đưa LMHT Lên Cloud: Giải Quyết Bài Toán Hàng Triệu CCU

Đây là hệ thống thực tế được Riot Games triển khai trên nền tảng AWS. Trước khi chuyển lên cloud, Riot vận hành các máy chủ riêng tại nhiều data center khác nhau trên thế giới. Tuy nhiên, cách làm này không tối ưu về chi phí và khả năng mở rộng. Sau khi chuyển hạ tầng lên AWS, Riot được cho là đã tiết kiệm đến **10 triệu đô la mỗi năm** – một con số không hề nhỏ.

Trong bài viết này, mình sẽ không đi sâu vào các **Functional Requirements (yêu cầu chức năng)** hay **Non-Functional Requirements (yêu cầu phi chức năng)**, mà muốn tập trung vào **cách mà Liên Minh Huyền Thoại (LMHT) xử lý hàng triệu người chơi đồng thời (CCU)**.

---

### LMHT và Kiến Trúc Dedicated Game Server

LMHT sử dụng mô hình **dedicated game server**: toàn bộ trận đấu được xử lý trên server, còn máy tính của người chơi chỉ đóng vai trò gửi/nhận dữ liệu trận đấu. Trước đây Riot dùng **VMs (máy ảo)**, sau này chuyển sang dùng **Kubernetes (K8s)** để chạy các game server container.

Một **game server** có thể chạy đồng thời nhiều **game instance** – mỗi instance là một trận đấu. Thông thường, mỗi server sẽ host khoảng **20 trận đấu** cùng lúc, và mỗi trận đấu có **10 người chơi**.

---

### Bài Toán Quy Mô: Nếu Có 100 Triệu CCU

Giả sử LMHT đạt 100 triệu CCU trên toàn cầu, ta có thể tính toán sơ bộ như sau:

- LMHT có mặt tại **20 khu vực** trên thế giới → mỗi khu vực phải xử lý ~5 triệu CCU:  
    `100,000,000 / 20 = 5,000,000 CCU/khu vực`
    
- Mỗi trận có 10 người chơi và mỗi server xử lý được 20 trận → mỗi khu vực cần:  
    `5,000,000 / (10 x 20) = 25,000 game server/khu vực`
    
- Giả sử mỗi trận kéo dài trung bình **1.800 giây (30 phút)** → số lượng instance cần tạo mới mỗi giây tại mỗi khu vực:  
    `5,000,000 / (10 x 1800) = 278 yêu cầu khởi tạo/giây`
    

Vậy trong mỗi giây, hạ tầng cần **xử lý và phân phối 278 yêu cầu tạo game instance mới** đến hơn 25.000 game server – và điều này lặp lại **mỗi giây**, 24/7. Tức là mỗi phút có khoảng **16.680 yêu cầu phân phối**. Tính cho vui vậy thôi, nhưng nó cho thấy rõ bài toán **scaling** là không hề đơn giản.

---

### Thách Thức về CPU Load và Tối Ưu Phân Bổ

Một server có thể host 20 trận đấu là lý tưởng trong điều kiện **các trận diễn ra xen kẽ nhau**. Nhưng trên thực tế:

- Các trận không **bắt đầu** và **kết thúc** cùng lúc.
    
- Quan trọng hơn, **CPU usage thay đổi theo giai đoạn trận đấu**:
    
    - Early game: đi đường, farm lính, ít giao tranh → CPU thấp
        
    - Mid/late game: nhiều kỹ năng, giao tranh tổng, AI phức tạp hơn → CPU tăng vọt
        

Nếu tất cả 20 trận trên một server đều đồng loạt bước vào **late game**, thì server đó sẽ **quá tải CPU** và gây lag. Vậy có phải giảm xuống 10 trận/server để tránh điều này? Không hề đơn giản, vì làm vậy sẽ:

- **Tăng gấp đôi số lượng server**, kéo theo chi phí vận hành cao
    
- **Lãng phí tài nguyên** ở các giai đoạn CPU usage thấp
    

---

### Giải Pháp: Load Balancing Thông Minh

Riot không chỉ đơn giản tăng số server, mà họ cần:

- Một **thuật toán phân phối tải thông minh**, có thể:
    
    - Phân tích mức CPU usage hiện tại của mỗi server
        
    - Ước tính mức tài nguyên tiêu thụ của trận đấu mới dựa trên nhiều yếu tố (giờ chơi, số người, tướng chọn,...)
        
- **Quy tắc phân bổ hợp lý** để duy trì mức CPU usage ổn định giữa các game server
    

Mục tiêu cuối cùng là **tối ưu tài nguyên phần cứng mà không làm ảnh hưởng đến trải nghiệm người chơi** – một bài toán rất thực tế, và cực kỳ thử thách ở quy mô toàn cầu.

---

### Phần Phân Tích Cho Phỏng Vấn

Nếu bạn đang luyện tập cho phỏng vấn (đặc biệt là các vị trí về backend/game infra), hãy tự phân tích hệ thống này với các góc độ sau:

- **Functional Requirements**: tạo trận đấu, phân phối người chơi, truyền dữ liệu thời gian thực, giữ kết nối ổn định...
    
- **Non-Functional Requirements**: scalability, latency thấp, fault tolerance, cost efficiency...
    
- **Core Entities**: game instance, server, player session, match scheduler, resource allocator...
    
- **Game Data Flow**: từ client đến server, các bước xử lý game tick, đồng bộ trạng thái,...
    

---

**Tạm kết:**  
Mình chọn tựa game này cho bài viết đầu tiên là bởi vì 12 năm gắn bó với nó. Chém gió vậy thôi, hy vọng bài viết giúp bạn hiểu thêm về cách một tựa game trăm triệu người chơi như LMHT xử lý hạ tầng phía sau.

![LOL-SD](LOL-SD.png)

# Functional Requirements

## 1. Gameplay & Player Interaction
- Players can create, join, and play real-time 5v5 matches.
- Players can select champions, summoner spells, and runes.
- Real-time combat mechanics with abilities, movement, and cooldowns.
- Game map (Summoner’s Rift) with towers, jungle camps, minions, and objectives.

## 2. Matchmaking & Game Sessions
- Matchmaking system to create balanced matches based on rank (MMR).
- Queue types: Solo, Duo, Flex, ARAM, etc.
- Game session provisioning and synchronization.

## 3. Account & Progression
- User registration, login, and account management.
- Progression tracking: XP, level, ranked tier, honor level.
- Match history, replays, and statistics.

## 4. Cosmetics & Store
- In-game shop to purchase champions, skins, and items.
- Loot system: Hextech chests, keys, and crafting.
- Events and missions system.

## 5. Communication & Social
- In-game voice and text chat.
- Party creation and friend system.
- Reporting and punishment system for toxicity.

## 6. Security & Integrity
- Anti-cheat system to detect and block unfair behavior.
- Secure client-server communication.

---

# Non-Functional Requirements

## 1. Performance & Latency
- Real-time responsiveness: player actions must reflect on screen with <100ms delay.
- Stable frame rates and low server tick latency.

## 2. Scalability
- Handle millions of concurrent players across multiple regions.
- Scale game servers globally with minimal downtime.

## 3. Availability & Reliability
- 99.9%+ uptime for live services (matchmaking, login, store).
- Auto-recovery from server crashes or player disconnects.
- Session continuity for reconnecting players.

## 4. Security
- Protection against cheating, botting, and third-party tools.
- Secure player data and transactions.

## 5. Maintainability & Upgradability
- Frequent patching with zero or minimal downtime.
- Blue-green or rolling deployments for updates.

## 6. Observability
- Real-time metrics: match errors, player reports, latency spikes.
- Logs and traces for game crashes, errors, and abuse.

---

# Game Data Flow

## 1. Game Start Flow
This is where the game is requested and provisioned:
- Riot Client initiates a game request (e.g. player clicks “Start Match”).
- Game Flow Service receives the request.
- It sends a request to the Game Session Manager (GSM) to prepare a match.
- GSM builds the game session metadata and sends a Game Start Request to the Game Provisioning Service (GPS).
- GPS sends this to the Game Placement Orchestrator (GPO), which:
  - Selects the best region or pod based on latency or availability.
- GPO delegates to GLM/SVM (Game Lifecycle & Server Version Manager), which:
  - Boots up a Game Server container on a Linux pod.
- Game is now running → GPS notifies Game Flow Service → which notifies the Riot Client that the match is ready.

**Result**: A dedicated game server is running for the players.

## 2. Game Server Lifecycle
- The game server handles all real-time gameplay, independently.
- Player actions and state remain within the server during the match.
- Server health is monitored by GLM.

## 3. Game Result Flow
After the match ends, results must be processed:
- Game Server finishes the match and sends results to the GDP Service (Game Data Processor).
- GDP does two key things:
  - Posts the results to Amazon S3 for storage (e.g., logs, replays).
  - Publishes a message to MSK (Kafka) topic with structured match result data.

## 4. Result Consumption & Analytics
- Results Processing Service listens to MSK and consumes match result messages.
- It processes the data:
  - Updates player stats, ratings, MMR.
  - Stores structured match data in a persistent database.
  - Triggers downstream systems (e.g., leaderboards, achievements).

**Result**: Player performance is updated, match is recorded, and game analytics can be run.
