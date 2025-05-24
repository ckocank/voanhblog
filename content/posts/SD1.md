---
title: Design League of Legend
date: 2025-05-18
draft: false
tags:
  - Interview
  - SystemDesign
categories: Interview Experience
---
Không biết là có bao giờ được hỏi không nhưng là một người chơi LMHT được 12 năm thì mình chọn tựa game này để thiết kế cho post đầu tiên của mục này.

Đây là hệ thống thực tế được Riot triển khai trên AWS. Trước khi chuyển lên cloud thì Riot tự chạy máy chủ ở các data center khác nhau nhưng không tối ưu được chi phí. Còn sau khi lên cloud của AWS thì nghe nói tiết kiệm được 10 triệu đô la hàng năm luôn.

Về Functional Requirements và Non-Functional Requirements thì không có nhiều điều để nói lắm, mình muốn tập chung vào cách mà LMHT xử lý hàng triệu CCU như thế nào. LMHT sử dụng cơ chế dedicated game server, tức là trận đấu sẽ diễn ra ở trên server chứ không phải là ở trong máy tính của các bạn, máy tính của các bạn chỉ có nhận và gửi thông tin của trận đấu lên server thôi. Game server có thể là VM cũng có thể là K8S (trước Riot dùng VM sau dùng K8S), 1 game server sẽ chạy nhiều trận đấu một lúc và mỗi trận đấu sẽ là 1 container instance. Mỗi khu vực / máy chủ sẽ có nhiều game server như vậy. 

Hãy giả sử LMHT có 100 triệu CCU thì ta có phép tính sau:
- Có 20 khu vực trên trái đất này đặt máy chủ LMHT thì mỗi máy chủ đó phải gánh khoảng 5 triệu CCU.
`100,000,000 / 20 = 5,000,000 (CCU/region), 20 regions` 
- Mỗi instance có 10 người chơi và 1 game server có thể chạy được 20 instance thì mỗi khu vực sẽ cần phải có 25000 cái game server như vậy.
`5,000,000 / (10 x 20) = 25,000 (VM/region), 10 players * 20 instances/vm`
- Mỗi trận đấu giả sử là 1800 giây thì mỗi giây sẽ có 278 instance mới cần được tạo ra ở mỗi khu vực.
`5,000,000 / (10 x 1800) = 278 allocation_req/sec, 10 players * 1800 secs/game`

Sau khi đã có con số là 278 thì hãy tìm cách chia 278 request đó vào trong 25000 cái game game server và lặp đi lặp lại sau mỗi giây vậy thì 1 phút sẽ có 16680 reqs. cái này tính cho vui thôi hehe. 

Như giả sử ở trên, 1 server sẽ host được 20 cái game instance như vậy nhưng thực tế là các game instance không start cùng 1 lúc và cũng không stop cùng 1 lúc. Quan trọng nhất là ở mỗi thời điểm của trận đấu thì CPU usage cũng khác nhau. Ví dụ early game thì các bạn chỉ có đi đường, farm lính, cấp thấp, chiêu hồi lâu, lúc này CPU usage sẽ là thấp nhất vì chả có gì nhiều để xử lý cả, nhất là mấy ông LCK. Bù lại khi chuyển qua mid và late game thì lúc này bạn có đồ có đồ, có hồi chiêu, có nhiều mục tiêu lớn để giao tranh thì CPU usage sẽ tăng cao hơn do có nhiều action cùng một lúc hơn. Vậy thì tất cả các trận đấu bắt đầu cùng nhau thì sẽ cả cái game server sẽ sử dụng ít CPU nhưng đến late thì sẽ lag thôi rồi do cả 20 ông cùng ăn CPU. Vậy giải pháp là gì? Mỗi máy chỉ host 10 game thôi à, như vậy thì x2 lượng máy chủ lên à. Chắc chắn là không rồi vì như vậy vừa tốn kém lại còn không tối ưu phần cứng do lúc thì CPU cùng cao lúc thì cùng thấp. Cách tốt nhất là luôn giữ lượng CPU usage ổn định mặc kệ thời gian bắt đầu trận đấu có như nào. Để làm như vậy thì cần có một thuật toán load balancing hiệu quả và các rules cho nó. 

Thôi chém gió thế thôi, các bạn tự tìm hiểu sâu hơn nhé. Dưới đây là phần phân tích cho một buổi phỏng vấn. Các bạn phải phân tích được Functional Requirements, Non Functional Requirements, Core Entity, ngoài ra mình có thêm cả Game Data Flow nữa nhưng chỉ có cái này có thôi.

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
