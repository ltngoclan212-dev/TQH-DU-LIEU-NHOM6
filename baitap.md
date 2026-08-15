### Họ và tên: Trần Khánh Duyên

### MSSV: 066306018832

# BÀI TẬP: PHÂN LỚP DỮ LIỆU (DATA CLASSIFICATION)

## Câu 1. Mô tả bài toán phân lớp dữ liệu và quy trình giải quyết bài toán phân lớp

### 1.1. Bài toán phân lớp là gì

Phân lớp dữ liệu (Classification) thuộc nhóm học có giám sát (Supervised Learning), có nghĩa = là học một mô hình từ dữ liệu đã có nhãn để dự đoán nhãn cho dữ liệu mới. Đây là hai nhánh chính hay được đặt cạnh nhau để phân biệt:

1. Supervised Learning: học mô hình từ dữ liệu có nhãn. Phân lớp và hồi quy là hai bài toán điển hình.
2. Unsupervised Learning: học cấu trúc từ dữ liệu không có nhãn. Gom cụm (Clustering) và luật kết hợp (Association Rules) là hai ví dụ điển hình.
3. Semi supervised Learning: học mô hình bằng cách kết hợp cả dữ liệu có nhãn và không có nhãn.

Trong phân lớp, đầu vào là một tập thuộc tính mô tả đối tượng, đầu ra là một nhãn lớp thuộc tập giá trị rời rạc, định danh trước. Mô hình được huấn luyện trên tập dữ liệu đã biết nhãn, sau đó dùng để dự đoán nhãn cho các đối tượng chưa biết nhãn.

### 1.2. Quy trình giải quyết bài toán phân lớp (Supervised Learning Steps)

Quy trình gồm năm bước chính.

1. Mô hình hóa bài toán: xác định rõ điều cần dự đoán là gì, cần một hàm tối ưu hóa dạng nào, đầu ra cần là nhãn lớp cụ thể hay là xác suất thuộc lớp.

2. Trích xuất đặc trưng: tìm những thuộc tính giúp phân biệt tốt giữa các lớp. Đây thường là bước tốn công sức nhất nhưng cũng quan trọng nhất, vì càng nhiều đặc trưng thì càng cần nhiều dữ liệu huấn luyện để mô hình học tốt.

3. Thu thập dữ liệu huấn luyện: cần một tập dữ liệu đã gán nhãn đủ lớn, đủ chính xác và đủ đại diện, đảm bảo các lớp đều được thể hiện đầy đủ trong dữ liệu.

4. Lựa chọn kỹ thuật phù hợp: tùy theo đặc điểm của bài toán như có cần ước lượng xác suất không, các lớp có phân tách tuyến tính không, giả định độc lập giữa các thuộc tính có hợp lý không, từ đó chọn thuật toán phân lớp phù hợp.

5. Áp dụng vào thực tế: kiểm tra khả năng huấn luyện với dữ liệu quy mô lớn, cách kiểm thử mô hình khi đang vận hành, và cách cải thiện mô hình theo thời gian khi dữ liệu thực tế thay đổi.

## Câu 2. Phân biệt Overfitting và Underfitting

### 2.1. Khái niệm

Underfitting là hiện tượng mô hình quá đơn giản, chưa học được đầy đủ các quy luật ẩn trong dữ liệu huấn luyện. Kết quả là độ chính xác thấp trên cả tập huấn luyện lẫn tập kiểm tra.

Overfitting là hiện tượng mô hình quá phức tạp, học thuộc lòng cả những chi tiết đặc thù và nhiễu của tập huấn luyện. Kết quả là độ chính xác rất cao trên tập huấn luyện nhưng giảm mạnh trên tập kiểm tra, vì mô hình không tổng quát hóa tốt cho dữ liệu chưa từng thấy.

Nói theo góc độ độ lệch và phương sai, underfitting ứng với độ lệch (bias) cao và phương sai (variance) thấp, còn overfitting ứng với độ lệch thấp và phương sai cao.

### 2.2. Ví dụ minh họa

Xét bài toán dùng cây quyết định để dự đoán khách hàng có mua sản phẩm hay không.

Trường hợp underfitting: giới hạn cây chỉ có độ sâu bằng một, tức chỉ dùng đúng một thuộc tính để ra quyết định, ví dụ chỉ dựa vào thu nhập. Cây quá đơn giản nên bỏ sót các yếu tố quan trọng khác như tuổi, nghề nghiệp, lịch sử mua hàng, dẫn đến dự đoán sai nhiều ở cả hai tập dữ liệu.

Trường hợp overfitting: cho phép cây phát triển đến độ sâu tối đa, phân nhánh cho tới khi mỗi lá chỉ chứa đúng một bản ghi. Cây sẽ khớp chính xác một trăm phần trăm với tập huấn luyện, kể cả những điểm nhiễu ngẫu nhiên, nhưng khi gặp khách hàng mới thì dự đoán sai nhiều vì đã học cả những đặc điểm không mang tính quy luật chung.

### 2.3. Hướng khắc phục

Với underfitting nên tăng độ phức tạp của mô hình, bổ sung thêm thuộc tính, huấn luyện lâu hơn hoặc giảm bớt các ràng buộc lên mô hình.

Với overfitting nên cắt tỉa cây quyết định, áp dụng các kỹ thuật điều chuẩn như L1 hoặc L2, tăng lượng dữ liệu huấn luyện, dùng kiểm định chéo, dừng huấn luyện sớm, hoặc dùng các phương pháp tổng hợp nhiều mô hình như Random Forest.

## Câu 3. Các phương pháp phân lớp và ý tưởng chính, nhận xét ưu nhược điểm

Bốn phương pháp phân lớp thường:

### 3.1. k Nearest Neighbor (KNN)

Ý tưởng chính: lưu lại toàn bộ tập bản ghi huấn luyện. Khi cần phân lớp một bản ghi mới, tính khoảng cách từ bản ghi đó tới các bản ghi huấn luyện, chọn ra k bản ghi gần nhất, rồi lấy nhãn theo đa số trong số k bản ghi đó.

Ưu điểm: cách làm đơn giản, dễ hiểu, không cần xây dựng mô hình trước khi phân lớp, phù hợp với ranh giới lớp phức tạp không tuyến tính.

Nhược điểm: nếu k quá nhỏ thì mô hình nhạy cảm với nhiễu, nếu k quá lớn thì vùng lân cận có thể lẫn các điểm thuộc lớp khác. Các thuộc tính cần được chuẩn hóa vì đơn vị đo khác nhau sẽ làm sai lệch khoảng cách. Với dữ liệu nhiều chiều dễ gặp hiện tượng chiều cao gây phản trực giác trong đo khoảng cách. Việc phân lớp bản ghi mới tốn chi phí tính toán khá lớn vì phải so sánh với toàn bộ tập huấn luyện.

### 3.2. Support Vector Machine (SVM)

Ý tưởng chính: tìm một siêu phẳng tuyến tính phân tách hai lớp sao cho khoảng cách lề giữa các điểm gần nhất của mỗi lớp và siêu phẳng là lớn nhất, đưa về một bài toán tối ưu hóa có ràng buộc.

Ưu điểm: có nền tảng toán học chặt chẽ nhờ việc tối đa hóa margin. Khi dữ liệu không phân tách tuyến tính, có thể dùng biến nới lỏng hoặc phép biến đổi kernel để ánh xạ dữ liệu sang không gian nhiều chiều hơn, từ đó vẫn tìm được ranh giới phân tách phù hợp.

Nhược điểm: bài toán tối ưu khá phức tạp, cần các phương pháp số để giải như quy hoạch toàn phương. Việc xử lý dữ liệu không phân tách tuyến tính đòi hỏi thêm bước lựa chọn kernel phù hợp.

### 3.3. Logistic Regression

Ý tưởng chính: thay vì chỉ dự đoán nhãn lớp, mô hình dự đoán xác suất thuộc về một lớp cho trước, thông qua hàm logistic áp dụng lên tổ hợp tuyến tính của các thuộc tính, giúp giá trị đầu ra luôn nằm trong khoảng từ không đến một.

Ưu điểm: cho ra ước lượng xác suất thuộc lớp, điều này rất hữu ích trong nhiều ứng dụng thực tế. Các trọng số học được giúp hiểu mức độ quan trọng của từng đặc trưng. Mô hình hoạt động tốt với tập dữ liệu tương đối lớn và có tốc độ dự đoán nhanh.

Nhược điểm: đây là mô hình phân biệt (discriminative), giả định ranh giới quyết định có dạng tuyến tính trên không gian log odds, nên hiệu quả sẽ giảm nếu ranh giới thực tế phức tạp hơn nhiều.

### 3.4. Naïve Bayes Classifier

Ý tưởng chính: áp dụng định lý Bayes để tính xác suất một bản ghi thuộc về từng lớp, với giả định ngây thơ là các thuộc tính độc lập có điều kiện với nhau khi biết trước lớp.

Ưu điểm: bền vững với các điểm nhiễu đơn lẻ. Có thể xử lý giá trị thiếu bằng cách bỏ qua thuộc tính đó khi tính xác suất. Ít bị ảnh hưởng bởi các thuộc tính không liên quan.

**Nhược điểm:** giả định độc lập giữa các thuộc tính thường không đúng hoàn toàn trong thực tế, có thể khắc phục bằng các mô hình phức tạp hơn như mạng Bayes. Xác suất ước lượng ra thường bị lệch, nên nếu mục tiêu chính là có được một ước lượng xác suất chính xác thì Logistic Regression thường cho kết quả tốt hơn.

### 3.5. Nhận xét chung

Naïve Bayes thuộc nhóm mô hình sinh (generative), có nghĩa là học phân phối xác suất của dữ liệu trong từng lớp rồi từ đó suy ra xác suất thuộc lớp. Logistic Regression và SVM thuộc nhóm mô hình phân biệt (discriminative), có nghĩa là học trực tiếp ranh giới phân tách giữa các lớp mà không cần mô hình hóa cách dữ liệu được sinh ra.

Việc lựa chọn phương pháp phù hợp phụ thuộc vào yêu cầu cụ thể của bài toán, ví dụ có cần ước lượng xác suất hay không, các lớp có phân tách tuyến tính hay không, và giả định độc lập giữa các thuộc tính có hợp lý với dữ liệu thực tế hay không.
