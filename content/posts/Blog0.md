---
title: Lần đầu phỏng vấn ở FAANG
date: 2025-05-17
draft: false
tags:
  - Interview
categories: Interview Experience
---
Đây là bài viết chia sẻ kinh nghiệm chuẩn bị cho việc phỏng vấn vị trí SWE tại Meta của mình. Trong quá trình này mình đã học được rất là nhiều. Thật sự là không dễ với mình, hy vọng các bạn chuẩn bị thật tốt.
### Quy trình phỏng vấn.

Quy trình phỏng vấn bao gồm 5 bước:
- **CV Screening**: Các bạn có thể nộp CV ngay trên web career hoặc được referrals, nếu các bạn có quen hoặc xin được referrals thì CV của bạn sẽ được đánh giá trực tiếp bởi Recruiter.
- **Recruiter Conversation**: Sau khi công ty đánh giá CV của bạn phù hợp với vị trí công việc thì Recruiter sẽ liên hệ với bạn thông qua email để có thể hẹn 1 cuộc nói chuyện ngắn giữa 2 người. Đây chỉ là cuộc gọi để trao đổi qua về vị trí công việc, kinh nghiệm làm việc của bạn.
- **Screening Interviews** (Phone Screen): Ở đây thì tùy công ty và tùy vị trí mà bạn có 1 đến 2 cuộc phỏng vấn, ở Meta mình được phỏng vấn 1 vòng Coding.
- **Virtual or Onsite Interview**: Ở vòng này bạn sẽ có từ 3 đến 6 cuộc phỏng vấn khác nhau tùy vào vị trí bạn ứng tuyển. Của mình bao gồm 2 Coding, 2 System Design, 1 Behavioral.
- Decision: Đơn giản chỉ là quyết định xem bạn có được chọn hay không thôi, nếu được chọn thì tùy vị trí mà có Team Matching nữa.

### Chuẩn bị cho phỏng vấn.

Thật sự thì mình cũng khá bất ngờ khi CV của mình pass vòng screening và mình hoàn toàn không chuẩn bị 1 chút gì cho cuộc phỏng vấn này. Sau khi nói chuyện với Recruiter thì mình còn chưa hình dung được interview loop sẽ như thế nào cơ. Nói chung là mình bắt đầu lên kế hoạch từ sau cuộc trò chuyện với Recruiter và kế hoạch của mình như sau: ban ngày LeetCode, tối System Design và Behavioral. Kế hoạch của mình đơn giản thế thôi và mình đã tuân thủ đúng theo nó 6 tuần liên tục kể cả ngày nghỉ. 

Theo mình để chuẩn bị cho interview loop này thì bạn cần dành ra ít nhất 3 tháng trước khi nộp CV để chuẩn bị các kỹ năng cần thiết. Đấy là với người đi làm và đã có kinh nghiệm liên quan nhé. Còn với những bạn mới ra trường hoặc chưa có tí kinh nghiệm gì thì ít nhất cũng phải 6 tháng. Mình biết 1 ông chuẩn bị trước hẳn 1 năm nhưng vẫn trượt. Vậy nên các bạn không nghiêm túc thì cơ hội sẽ là rất thấp.

#### Vậy chiến lược ở đây là gì? 
##### Về coding:
- Đầu tiên, các bạn cần phải nắm vững kiến thức DSA cơ bản như array, stack, hash table, heap, linked list, tree, graph. 
- Sau đó hãy học các kỹ thuật sử dụng array hiệu quả như two pointers, sliding window, prefix sum, binary search. Các brute force solution sẽ không được chấp nhật kiểu như 2 vòng for lồng nhau với độ phức tạp của thật toán (TC) là O(N^2). Hãy tận dụng hash table như set hoặc map để giảm TC xuống O(N). 
- Về phần Tree/Graph, hãy thật thành thạo BFS và DFS. BFS thì phải thành thạo cách sử dụng queue, DFS thì phải thành thạo call stack và phân biệt được các kỹ thuật tree traversal như pre-order, in-order, post-order. Nếu một bài Tree mà có thể giải được bằng cả 2 cách thì hãy làm cả 2.

Solution của bạn phải là solution tốt nhất về Time Complexity và Space Complexity. Nên kể cả bạn có làm xong 1 problem trên LeetCode nhưng hãy tham khảo thêm các solution khác nữa để đề phòng có follow up question hoặc solution của bạn chưa tối ưu nhất.

Tất nhiên sẽ có một số problem sử dụng các thuật toán đặc biệt mà để làm được thì bạn phải học thuộc nó. Lúc này thì bạn chỉ cần dụng thuật toán kém tối ưu hơn thôi và giải thích cho Interviewer là được. Chỉ dùng brute force khi mà bạn không bằng cách nào tìm được thuật toán tối ưu nhất và lúc này bạn sẽ bị đánh giá thấp bới Interviewer.

Các bạn cần nhớ rằng để đánh giá một phần phỏng vấn coding, thì việc bạn code được ra solution không thôi là chưa đủ, nó là tập hợp của nhiều yếu tố: giao tiếp, đọc hiểu vấn đề, giải quyết vấn đề, xác nhận.
- Communication: ở đây giám khảo sẽ đánh giá bạn về khả năng giao tiếp và làm việc nhóm của bạn, cần nhớ rằng Interviewer là người biết đáp án cho bài toán của bạn và việc của bạn ở đây là làm việc với họ để ra giải pháp. Nếu bạn có kẹt ở đâu thì họ cũng sẽ đưa ra các gợi ý cho bạn nên đừng cứng đầu mà hãy biết cách lắng nghe và giao tiếp. Kể cả bạn có code đúng hết nhưng trong quá trình đó bạn không trao đổi gì thì chắc chắn bạn vẫn sẽ fail.
- Problem Understanding: khi nhận được vấn đề hãy đảm bảo là bạn hoàn toàn hiểu được nó và nếu còn cảm thấy mơ hồ, hãy trao đổi với giám khảo vì bạn không muốn code 1 solution cho 1 vấn đề khác hoàn toàn với vấn đề được đưa ra. Ngoài ra cũng cần phải làm rõ về input và các case cơ bản như input có null không, string có chứa ký tự đặc biệt không hay input có thể âm không, mình chỉ ví dụ cơ bản thế thôi.
- Problem Solving: sau khi thật sự hiểu vấn đề và xác nhận điều đó với Interviewer, bạn lúc này mới bắt đầu code. Trong lúc code, hãy nói ra những suy nghĩ của bạn thành lời, vừa code vừa nói để giám khảo có thể hiểu được là chỗ này bạn định làm gì và tại sao nó lại như thế. Ngoài ra nhỡ bạn có kẹt ở dâu thì giám khảo còn biết đường mà giúp bạn.
- Confirmation: khi code xong bạn tưởng là xong á, không nhé. Bước cuối cùng là xác nhận lại code của bạn chạy đúng đề bài và không có bug. Ở LC khi làm xong bạn có thể bấm run nhưng khi phỏng vấn thì không. Làm xong các bạn tự trở thành một human debugger theo nghĩa đen. Hãy nghĩ ra một test case nào đó mà có bảo gồm cả các edge case để dry run lại code một lần cuối cùng. Sau đó hãy đưa ra TC và SC của solution của bạn.

Ngoài ra thì mỗi câu hỏi bạn chỉ có 20 phút để trả lời thôi nên có khi bạn còn không đủ thời gian để nghĩ ấy. Vậy việc bạn làm thật nhiều LeetCode, thậm chỉ mỗi bài còn phải làm đi làm lại 3, 4 lần nếu bạn chưa hiểu rõ solution sẽ giúp bạn giải hoàn thành câu hỏi nhanh nhất có thể, thậm chí là nhắm mắt bạn cũng phải code được. 

##### Về System Design:
Cái này tưởng dễ nhưng cũng không dễ tí nào, cơ bản là mình fail ở đây nên mình mới nói thế :)
Ở vòng này giám khảo sẽ đánh giá khả năng của bạn trong việc xây dựng một software systems hoặc end-to-end systems mà giải quyết nhu cầu hoặc một vấn đề cụ thể nào đó. Nó đánh giá việc bạn có một cái nhìn tổng thể về hệ thống hay không.
Tùy vị trí mà bạn sẽ được chọn 1 trong 2 hoặc cả 2 đó là: Systems Design hoặc Product Architectural Design.
Ví dụ nếu bạn phỏng vấn làm mảng mobile thì người ta có thể yêu cầu bạn thiết kế 1 cái app mobile, nếu làm game thì thiết kế 1 con game. Ngoài ra là thiết kế một hệ thống/ ứng dụng như Facebook, Youtube, Instagram, Uber, hay hệ thống theo dõi ads click, top bài hát được nghe nhiều nhất, live stream comment.
Cái này khá là rộng và bạn cần phải trang bị được các kiến thức cơ bản về các services khác nhau trong hệ thống.

##### Về Behavioral:
Đây là vòng mình làm tốt nhất và theo mình cũng là vòng dễ nhất vì các bạn chỉ việc nói thôi. Vòng này thì công ty nào cũng có và họ sẽ đánh giá những gì bạn đã làm trong quá khứ và có thể là cả tương lai. Tại vì với các công ty, họ sẽ không thể nào biết được bạn là một con người như thế nào hay bạn có phù hợp với môi trường của công ty không. Đừng vì vòng này không có phỏng vấn kỹ thuật mà chủ quan vì rất nhiều người dù làm tốt coding và system design nhưng vẫn fail vì vòng này nhé.

Để chuẩn bị đầu tiên hãy viết ra những dự án bạn đã làm trong quá khứ, sau đó hãy xem công ty bạn định phỏng vấn có các tiêu chí gì, AMZ là Leadership Principle, Meta có 5 tiêu chí. Hãy chuẩn bị các câu chuyện ứng với các tiêu chí của công ty.

Các bạn phải kể câu chuyện của mình dựa vào STAR hoặc CARL method, C: context, A: action, R: result, L: learning. Đầu tiên là hoàn cảnh của câu chuyện, sau đó là các hành động của bạn trong câu chuyện đó, tiếp theo là kết quả của câu chuyện, cuối cùng là bạn đã học được gì.

Các câu hỏi có rất nhiều nhưng chúng cũng dễ bị overlap, một câu chuyện của bạn có thể trả lời được cho nhiều câu hỏi, chỉ cần lái nó đi một tí là được. Mình chuẩn bị khoảng 11 câu chuyện khác nhau bằng cách: Chọn 1 câu hỏi nào đấy, bảo chatgpt soạn sẵn promt để mình có thể trả lời theo cái promt đấy rồi để chatgpt soạn câu chuyện theo CARL method cho mình. Trước khi phỏng vấn mình list ra các gạch đầu dòng của mỗi câu chuyện để đề phòng mình có quên thì có thể mở ra xem lại.

##### Vậy kết quả của mình là gì? 
Là bị reject các bạn ạ. Với 6 tuần, mình chỉ tập trung vào coding nên cả 2 phần system design của mình đều bị down level và kết quả tổng thể là mình không được nhận. Có thể nếu mình có nhiều thời gian chuẩn bị hơn thì chắc chắn mình sẽ dành thêm thời gian để học system design. Tất cả các vòng phỏng vấn đều quan trong như nhau nên tạch 1 vòng gần như là xác định nhé. Mỗi vị trí có đến cả trăm cái CV khác nhau nên là các bạn cũng cần chuẩn bị cả tâm lý nữa. Nhiều khi bạn có thể là tốt tất cả các vòng nhưng có người còn làm tốt hơn bạn và CV của họ cũng có nhiều kinh nghiệm hơn bạn thì bạn vẫn trượt bình thường.

Các tài liệu mình tham khảo cho quá trình PV:
CD: YouTube CodingWithMinmer, NeetCode, Cracking FAANG
SD: YouTube HelloInterview, ByteByteGo
