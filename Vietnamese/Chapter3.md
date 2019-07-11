
3. Lý giải "Klaytn"
3.1 Đồng thuận
Trong các chương trước, chúng tôi đã thảo luận về các vấn đề của blockchain hiện tại. Hãy nói về cách blockchain Klaytn giải quyết các vấn đề bằng thuật toán đồng thuận. Có nhiều loại thuật toán đồng thuận, chẳng hạn như PoW (Proof-of-Work) hoặc PoS (Proof-of-Stake), thường được sử dụng trong các blockchain công cộng và PBFT (Dung sai lỗi thực tế Byzantine) hoặc Raft, được sử dụng trong blockchains riêng tư (private). Nhìn chung, blockchains riêng tư có thể đạt được đông thuận hiệu quả hơn so với blockchains công cộng. Đặc biệt, các chuỗi khối riêng dựa trên BFT có thể đạt được hiệu suất và hiệu quả cao bằng cách giới hạn số lượng nút tham gia. Tuy nhiên, cấu hình này giới hạn số lượng nút đồng thuận, làm suy yếu sự phân cấp và nội dung của kết quả đồng thuận chỉ được tiết lộ cho các nhóm nhỏ. Do đó, nó hạn chế tính minh bạch và gây hại cho lợi ích của blockchain.

Mặt khác, Klaytn chọn Istanbul BFT làm thuật toán đồng thuận vì họ tin rằng bằng cách sử dụng tốt các lợi thế của BFT, nó có thể kết hợp cả hai lợi thế của các chuỗi khối công khai và riêng tư. Nó hướng tới một blockchain công cộng cung cấp hiệu suất và sự ổn định cho các doanh nghiệp lớn trong khi vẫn duy trì tính bảo mật và minh bạch mạnh mẽ. Để đạt được mục tiêu này, Klaytn áp dụng mô hình tin cậy về sự đồng thuận riêng tư với công bố công khai. Nó bao gồm một số lượng nhỏ các nút riêng tư đạt được sự đồng thuận và các nút khác có thể truy cập công khai và xác minh kết quả của việc tạo khối. Bây giờ chúng ta hãy xem thêm về Istanbul BFT (Byzantine Fault Tolerance) mà Klaytn đang sử dụng như một thuật toán thỏa thuận.

BFT Istanbul có một quy trình đồng thuận ba bước. Có các bước chuẩn bị trước, chuẩn bị và cam kết. Klaytn sử dụng phương pháp quay vòng để chọn người đề xuất trong số các nút đồng thuận mỗi vòng. Nó có nghĩa là một người đề xuất. Các nút đồng thuận còn lại là trình xác nhận. Và làm xác minh.

Nếu bạn nhìn vào bức tranh, có người đề xuất, trình xác nhận 1, 2, 3, v.v. Trong số đó, nút được đánh dấu bằng X ở trạng thái hiện đang ở trạng thái bị lỗi. Nó có nghĩa là nó không hoạt động đúng như một trình xác minh. Khi máy tính bị hỏng, mạng bị ngắt kết nối hoặc máy tính có hành động độc hại kiểu này xảy ra.

Bước đầu tiên là một đề xuất của người Hồi giáo trong đó một trong những nút đồng thuận được chọn làm người đề xuất. Bước thứ hai là chuẩn bị trước trong đó nút đề xuất tạo các khối và đưa ra gợi ý cho các nút khác. Sau đó, gửi đề xuất đến nút trình xác nhận 1, gửi nó đến nút trình xác nhận 2 và gửi nó đến nút trình xác nhận 3. Đây là bước để vượt qua cùng với thông điệp.

Trong bước chuẩn bị thứ ba, khi các nút xác minh 1, 2 hoặc 3 nhận được thông báo từ người đề xuất, họ sẽ gửi các thông báo rằng họ đã nhận được nút thành công đến các nút khác. Nút trình xác nhận 1 gửi tin nhắn đến cả ba nút và nút trình xác thực 2 cũng gửi tin nhắn đến cả ba nút. Tuy nhiên, nút xác thực 3 không gửi gì và chỉ nhận được thông báo vì hiện tại nó bị lỗi.

Ở cuối trạng thái chuẩn bị, bạn có thể thấy có bao nhiêu nút trong hệ thống. Giống như hình ảnh này ở đây, chúng ta có thể thấy rằng cả ba đều sống sót: người đề xuất, trình xác nhận 1 và trình xác nhận 2. Quá trình này sẽ đảm bảo rằng tất cả các trình xác minh nằm trong cùng một vòng.

Cuối cùng, trong giai đoạn cam kết, đó là quá trình giao tiếp với các nút khác để quyết định có chấp nhận một khối nhận được từ một người đề xuất hay không. Ví dụ, nó sẽ gửi một phản hồi tới các nút để kiểm tra xem các khối từ người đề xuất có ổn hay sai hay không. Nếu các nút hơn hai phần ba đồng ý, khối sẽ được phê duyệt ngay lập tức. Cuối cùng, nó được quyết định trong giai đoạn cam kết và tính cuối cùng được thực hiện. Đó là, sự vắng mặt của tính cuối cùng không tồn tại và trạng thái cuối cùng không thể thay đổi được hình thành ở giai đoạn này. Đó không phải là một trạng thái mơ hồ như PoW.

Vì vậy, lợi thế là giao tiếp dẫn đến sự đồng thuận và hoàn thành ngay lập tức. Tuy nhiên, có một bất lợi là lưu lượng truy cập tăng theo cấp số nhân khi số lượng nút đồng thuận tăng. Phần này được đặt để chỉ chọn một phần của nút đồng thuận và duy trì biểu mẫu BFT.

Chúng ta hãy xem cách khối được tạo và lan truyền trong lớp tiếp theo.

3.2 Tạo và phổ biến khối
Hãy xem cách Klaytn tạo và truyền bá các khối để cung cấp thỏa mãn trải nghiệm người dùng.

Trước tiên chúng ta hãy nhìn vào chu trình tạo khối. Chu kỳ tạo khối của Klaytn được gọi là vòng và một khối mới được tạo mỗi vòng và vòng mới được bắt đầu ngay khi kết thúc. Khoảng thời gian tạo khối mất khoảng 1 giây.

Chúng ta hãy xem cách các đề xuất và lựa chọn ủy ban hoạt động. Trong mỗi vòng, người đề xuất để tạo khối được kéo từ một trong các nút của hội đồng quản trị một cách ngẫu nhiên nhưng quyết đoán. Hội đồng quản trị là một tập hợp các tế bào cốt lõi hoặc các nút đồng thuận. Nếu bạn nhìn vào hình ảnh, các vòng tròn này là các nút đồng thuận, trong đó màu xanh lam được chọn làm người đề xuất của vòng hiện tại. Và sau đó chọn một nhóm nút đồng thuận khác làm ủy ban của vòng đó. Chúng là các nút xác nhận hợp lệ với màu hồng được lựa chọn bởi ủy ban. Cụ thể hơn, mỗi nút đồng thuận sử dụng một số ngẫu nhiên xuất phát từ tiêu đề khối gần đây nhất để thực hiện thao tác mã hóa để chứng minh rằng nó đã được chọn cho vòng này.

Continuae...
