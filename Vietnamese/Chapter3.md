
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

Chúng ta hãy xem khối gợi ý và khối xác minh. Khi một nút đồng thuận được chọn làm người đề xuất, nó sẽ thông báo cho các nút đồng thuận khác về bằng chứng rằng nó đã được chọn làm người đề xuất trong vòng. Tại thời điểm này, nó sẽ chứng minh điều này bằng bằng chứng mật mã có thể được xác minh bằng khóa chung của người đề xuất. Sau đó, nhóm nút đồng thuận được bầu vào ủy ban trong vòng nói với người đề xuất, tương tự, với bằng chứng, tại sao họ được chọn làm thành viên của ủy ban. (Bấm) Bây giờ bạn biết ai là người đề xuất và ủy ban, người đề xuất chọn và sắp xếp các giao dịch trong nhóm giao dịch và tạo các khối. Sau đó, nó đồng ý với ủy ban, đồng ý với khối mới được tạo và hoàn thành.

Cuối cùng, hãy nhìn vào sự lan truyền khối. Khối đề xuất phải được hai phần ba thành viên của ủy ban ký để hoàn thành thành công. Khi ủy ban đạt được thỏa thuận, khối mới được chuyển đến tất cả các nút đồng thuận và vòng đồng thuận kết thúc. Sau đó, bây giờ bạn có thể truyền khối tới các nút điểm cuối thông qua nút proxy (nhấp). Cho đến nay, chúng ta đã hiểu làm thế nào những người đề xuất và ủy ban có thể được lựa chọn và đồng ý để ngăn chặn việc tạo và tuyên truyền.

3.3 Cấu trúc mạng
Hãy dành một chút thời gian để giải thích cấu trúc mạng của Klaytn. Bên trái là phiên bản tóm tắt của mạng. Có một mạng tế bào lõi trong toàn bộ mạng và có một mạng nút điểm cuối bao quanh ô lõi. Nếu bạn nhìn vào phần mở rộng bên cạnh nó, bên trong hộp màu đỏ là mạng di động lõi và hộp màu xanh bên ngoài là mạng điểm cuối. Trong mạng tế bào lõi, phần màu vàng là CNN, mạng nút đồng thuận và phần màu đỏ là PNN, mạng nút proxy. Các CN trong màu vàng sẽ chịu trách nhiệm về sự đồng thuận.

Một tế bào lõi được vận hành bởi một người tham gia. Nó hoạt động với một CN và một số nút proxy được kết nối với CN. Để tham gia vào CN, bạn phải đáp ứng các điều kiện khó khăn. Và các CN đều được kết nối với nhau để họ có thể giao tiếp với nhau. Nếu có 10 CN, chúng được kết nối với nhau. Tất cả đều được kết nối bởi vì họ phải liên lạc với nhau nhanh nhất có thể khi họ đang trong quá trình đồng thuận. Và các CN không thể liên lạc trực tiếp với bên ngoài. Bởi vì nó là một môi trường rất riêng tư, không có sự can thiệp, nó có lợi thế là có thể nhanh chóng quyết định có nên tạo khối hay không, như một nút đồng thuận. Vì vậy, làm thế nào để bạn tiếp cận nó? Là một người tham gia tế bào cốt lõi, nó giống như bạn chạy mạng proxy mà bạn có thể quản lý và tin tưởng để đại diện cho họ.

Và ở bên ngoài, các nút điểm cuối được kết nối với mạng tế bào lõi. Các nút điểm cuối này có thể kết nối với nút proxy trong ô lõi để nhận thông tin. Tất nhiên, các nút điểm cuối có thể kết nối và trao đổi thông tin với nhau. Tuy nhiên, nếu nút điểm cuối kết nối với nút proxy, bạn có thể nhận được khối nhanh hơn. Lưu ý rằng không có yêu cầu phải là nút điểm cuối. Bất cứ ai cũng có thể là một nút điểm cuối và truyền thông tin cho khách hàng như web hoặc thiết bị di động. Đó là nút điểm cuối hoạt động như một nhà cung cấp dịch vụ.

Và một lần nữa, bạn có nút khởi động CN, ghi chú khởi động PN và nút khởi động EN, là nút loại đặc biệt được vận hành bởi Klaytn giúp các nút mới đăng ký vào mạng và kết nối với nút khác. Nút khởi động CN nằm trong mạng CN và không được công bố. Các nút khởi động PN và EN là các nút công khai. Các nút khởi động PN cho phép bạn chỉ đăng ký các nút proxy được phép và giúp bạn kết nối với các nút điểm cuối. Nút khởi động EN cung cấp thông tin cho các nút điểm cuối về nút proxy nào được kết nối. Cho đến đây chúng tôi đã đề cập ngắn gọn về cấu trúc mạng Klaytn.

3.4 Tế bào lõi
Hãy nói nhiều hơn về các tế bào cốt lõi. Khi mạng chính được đưa ra, trong tế bào cốt lõi chịu trách nhiệm cho sự đồng thuận sẽ hoạt động trong vài chục đơn vị. Khi các dịch vụ trở nên tốt hơn, chúng ta nên làm gì về khả năng mở rộng nếu có nhiều kết nối đến tế bào lõi? Trong trường hợp chung, không phải blockchain, khi người dùng phát triển, chúng tôi sẽ phát triển máy chủ và phân tách các yêu cầu. Tuy nhiên, trong trường hợp của blockchain, việc tăng số lượng nút có thể làm chậm tốc độ xử lý vì cần thêm thông tin cho mỗi nút khi nó phát triển. Tăng số lượng nút không tăng hiệu suất. Vì vậy, thay vì tăng số lượng nút, tăng hiệu suất của chính nút là cách đúng đắn. Ví dụ: bạn có thể tăng hiệu suất của RAM hoặc CPU. Hãy xem xét các điều kiện để tham gia như một nút đồng thuận. Hiệu suất của người tham gia

・Hơn 40 lõi vật lý
・RAM 256GB
・Tiết kiệm khoảng 14TB dữ liệu trong một năm
・Mạng 10G
Lưu ý rằng hiệu suất cao của một trong các nút đồng thuận của người tham gia không có nghĩa là tốc độ cao của toàn bộ mạng di động lõi. Bởi vì các nút còn lại với hiệu suất thấp hơn đang hoạt động ở thông số kỹ thuật thấp. Do đó, để cải thiện hiệu suất của ô lõi, cần phải khớp các thông số kỹ thuật tương tự để cải thiện hiệu suất.

Và nhìn vào cấu trúc của tế bào lõi một lần nữa, có thể thấy rằng nó bao gồm một CN và một số PN. Có một số lý do tại sao một nút proxy được gọi là PN. Vì CN có nguồn lực hạn chế để kết nối và số lượng CN bị hạn chế, nên nó hỗ trợ kết nối các điểm cuối bằng PN. Ví dụ: giả sử các nút điểm cuối có thể kết nối trực tiếp với CN. Nếu CN này có thể chấp nhận tới một nghìn kết nối điểm cuối, thì nếu vượt quá điều đó, nó sẽ bị gánh nặng bởi CN và hiệu suất của nó có thể bị sai. Vì vậy, PN đang làm phần này thay thế. PN kết nối với các nút điểm cuối và chuyển quá cảnh đến CN. Và vì CN chỉ cần kết nối với một vài PN, nên nó ít gánh nặng hơn và bạn có thể giải quyết các vấn đề kết nối của các điểm cuối cố gắng kết nối với ô lõi bằng cách đặt nhiều PN.

Tóm lại, vì CN là nút chịu trách nhiệm cho thỏa thuận, kết nối không phải là trở ngại về hiệu suất. Vì vậy, vai trò của PN là bảo vệ CN và vấn đề về khả năng mở rộng có thể được giải quyết bằng cách đặt nhiều PN.

3.5 Chuỗi dịch vụ
Chuỗi dịch vụ của Klaytn là một blockchain hoạt động độc lập được kết nối với mạng chính. Ý tưởng này xuất phát từ khả năng mở rộng. Trong tình huống bạn muốn sử dụng chuỗi dịch vụ, bạn cần đặt nó trong môi trường nút đặc biệt hoặc nếu bạn muốn tùy chỉnh mức bảo mật, ví dụ như khi bạn muốn chạy blockchain riêng. Dịch vụ đòi hỏi thông lượng rất lớn. Khi việc phân phối dịch vụ đến mạng chính không khả thi về mặt kinh tế, họ sử dụng chuỗi dịch vụ.

Nếu bạn nhìn vào hình ảnh, vòng tròn lớn ở giữa là mạng chính. Có thể thấy rằng chuỗi dịch vụ giữ niềm tin vào chuỗi chính, không được tự do giao tiếp giữa chuỗi chính và chuỗi dịch vụ và chỉ có thể sử dụng các giao dịch hạn chế. Ngoài ra, việc truyền KLAY sẽ chỉ được phép khi có những hạn chế sau này.

Nói cách khác, chuỗi dịch vụ xây dựng một không gian dịch vụ riêng biệt và khóa niềm tin trên mạng chính khi cần. Các nền tảng blockchain khác cũng đang chuyển sang áp dụng các công nghệ như chuỗi dịch vụ. Trong trường hợp của Ethereum, tôi cảm thấy những hạn chế của mạng chính về năng lực và tốc độ. Người ta biết rằng Crypto Kitty, nơi từng tạo ra sự bùng nổ lớn đã làm chậm mạng chính Ethereum. Vì vậy, về phía Ethereum, họ đã đưa ra một khái niệm dựa trên công nghệ sidechain có tên Plasma, nếu được thực hiện đúng cách sẽ giảm bớt gánh nặng cho chuỗi chính và cho phép xử lý nhiều giao dịch hơn mỗi giây. Nhưng nó vẫn không ra.

Nhân tiện, trong chuỗi dịch vụ của Klaytn, bạn có thể đặt phí xăng bằng không cho tất cả các giao dịch. Điều đó có nghĩa là các nhà phát triển hoặc nhà cung cấp dịch vụ BApp có thể xây dựng môi trường của riêng họ và cung cấp dịch vụ cho người dùng trong chuỗi dịch vụ. Vâng, tôi đã nói về chuỗi dịch vụ của Klaytn là gì.

3.6 Sự khác biệt giữa Klaytn và Ethereum - Vai trò khác nhau của các nút

Hãy nói ngắn gọn về sự khác biệt giữa Ethereum và Klaytn.

Ethereum là một mạng duy nhất. Không có sự phân biệt giữa các thành viên mạng. Bất cứ ai cũng có thể tạo một khối, nhưng khi nói đến việc tạo một khối, một người cần phải là người đầu tiên thông báo rằng họ đã tạo ra nó trước, và nó phải được biết đến ở nhiều nơi. Vì vậy, nếu bạn thêm một khối vào một blockchain, bạn sẽ nhận được một khoản bồi thường. Đây là PoW, một phương pháp chứng minh công việc được Ethereum sử dụng làm giao thức đồng thuận.

Trong Ethereum, bạn cần bám vào càng nhiều nút càng tốt vì bạn không biết ai sẽ là nút khai thác khối. Nói cách khác, các nút viết các khối có thông tin cập nhật. Vì vậy, tôi muốn nhận thông tin nhanh chóng nhưng tôi không biết nút này ở đâu. Nếu bạn biết rằng nút A luôn nhanh nhất khi viết một khối trên nút, bạn chỉ cần bám vào nút A này, thì bạn có thể nhận thông tin nhanh nhất.

Tuy nhiên, vì Ethereum luôn thay đổi nút của nó, bạn phải bám vào càng nhiều càng tốt, do đó, được đồn thổi đến càng nhiều nút càng tốt.

Sau đó, điều này sẽ cung cấp cho bạn một cơ hội để có được thông tin mới nhất. Vì bất kỳ nút nào cũng có thể viết và truyền các khối, bạn cần kết nối với càng nhiều nút càng tốt để có được dữ liệu mới nhất.

Klaytn, mặt khác, không phải là một mạng đơn lẻ, mà là một mạng có hai lớp. Tôi đã nói rằng một trong những nút đồng thuận trong mạng di động lõi sẽ được coi là một người đề xuất và đóng vai trò viết khối mỗi vòng. Vậy làm thế nào để bạn có được thông tin mới nhất? Tôi nên bám xung quanh. Các nút điểm cuối bị mắc kẹt vào ô lõi biết rằng các nút đồng thuận là các khối xây dựng, vì vậy chúng được gắn bên cạnh CN.

Bằng cách đó bạn có thể tải hoặc viết thông tin đáng tin cậy. Khi chúng tôi tạo một ứng dụng, chúng tôi xây dựng các máy chủ được hiển thị ở đây. Bạn có thể triển khai Java hoặc SQL DB lên đám mây hoặc máy chủ riêng như Azure hoặc AWS. Tuy nhiên, vì máy chủ này không thể được liên kết trực tiếp với ô lõi, trước tiên bạn phải kết nối với nút điểm cuối để truy cập dữ liệu blockchain. Bạn có thể kết nối máy tính của mình với một nút điểm cuối hoặc sử dụng nó để kết nối với một nút điểm cuối khác. Tuy nhiên, chạy cá nhân nút điểm cuối này là không dễ dàng. Vì hệ thống blockchain cần đồng bộ hóa tất cả các nút khi vận hành một nút, nên nó cần được đồng bộ hóa mỗi khi các khối mới được thêm vào để viết đúng.

Ngoài ra, cũng có một lo ngại rằng máy tính có thể bị hỏng do một cuộc tấn công. Do những vấn đề này, bạn có thể kết nối với một nút bên ngoài đáng tin cậy, chẳng hạn như nút cơ sở hạ tầng Ethereum. Ví dụ, bạn có một nhà phát triển web ở đây. Anh ta muốn kết nối với Klaytn và chỉ cần đọc dữ liệu. Sau đó, nó tốt hơn để kết nối với nút bên ngoài, công khai và sử dụng nó để làm cho nó dễ dàng hơn và ít tốn thời gian hơn so với chạy nút điểm cuối cá nhân.

Cuối cùng, không giống như Ethereum, có một chuỗi dịch vụ có thể giao tiếp một phần với mạng chính ở bên phải và xây dựng một không gian dịch vụ riêng biệt. Tóm lại, Klaytn là một mạng trong đó hai lớp tin tưởng lẫn nhau và khi truy cập vào một blockchain nội bộ, nút điểm cuối có thể kết nối với mạng di động lõi và ghi hoặc nhận dữ liệu nhanh chóng.
