# Vietnamese-NLP-Toolkit
1. Mục tiêu dự án
Xây dựng một hệ thống hoàn chỉnh có khả năng tự động trích xuất các Cụm động từ (Verb Phrase) từ văn bản tiếng Việt. Việc xác định được các cụm từ chỉ hành động này là một bài toán quan trọng, làm tiền đề cho các ứng dụng NLP nâng cao hơn như phân tích cú pháp, tóm tắt văn bản, và hệ thống hỏi đáp.

Dự án được xây dựng theo một pipeline (quy trình) gồm nhiều giai đoạn, trong đó kết quả của bước trước là đầu vào cho bước sau.

2. Quy trình hệ thống
Bước 1: Tách từ (Word Segmentation) - Bước tiền xử lý

Để máy tính có thể hiểu được văn bản, bước đầu tiên là phải tách chuỗi ký tự thành các đơn vị từ có nghĩa. Trong dự án này, thuật toán Longest Matching đã được tự triển khai để thực hiện tác vụ này, dựa trên một bộ từ điển N-gram được xây dựng sẵn.

Bước 2: Gán nhãn Từ loại (POS Tagging) - Bước phân tích cốt lõi

Đây là trái tim của hệ thống. Sau khi có được danh sách các từ, chúng ta cần xác định vai trò ngữ pháp của chúng (danh từ, động từ, tính từ,...).

Phương pháp: Sử dụng mô hình học máy Support Vector Machine (SVM).

Feature Engineering: Để mô hình hoạt động hiệu quả, một bộ đặc trưng chuyên sâu cho từ vựng tiếng Việt đã được thiết kế, bao gồm: hình thái từ (viết hoa), tiền tố, hậu tố, từ láy, các nhãn khả thi trong từ điển, và ngữ cảnh (từ đứng trước/sau).

Kết quả: Mô hình POS Tagging đạt độ chính xác ~73% trên tập dữ liệu kiểm thử, cung cấp thông tin ngữ pháp đủ tin cậy cho bước tiếp theo.

Bước 3: Trích xuất Cụm động từ (Verb Phrase Chunking) - Mục tiêu cuối cùng

Dựa trên kết quả gán nhãn từ loại từ Bước 2, một bộ quy tắc (rule-based) được xây dựng để "chunk" (nhóm) các từ lại với nhau. Hệ thống sẽ tìm các động từ (V) và mở rộng ra các thành phần liền kề như trạng từ (R), bổ ngữ (N, A, E,...) để hình thành một Cụm động từ hoàn chỉnh.

3. Kỹ năng thể hiện
Tư duy hệ thống: Khả năng thiết kế và xây dựng một pipeline NLP gồm nhiều giai đoạn liên kết chặt chẽ với nhau.

Giải quyết bài toán từ gốc: Tự triển khai thuật toán (Longest Matching), tự xây dựng đặc trưng (Feature Engineering) thay vì chỉ phụ thuộc vào thư viện.

Ứng dụng Học máy: Áp dụng thành công mô hình SVM vào một bài toán NLP thực tế và biết cách đánh giá hiệu quả của nó.
