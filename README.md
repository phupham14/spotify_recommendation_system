# recommendation_system
1. Phương pháp và thuật toán sử dụng
Tính toán tương đồng:
Dữ liệu các bài hát được biểu diễn thành các vector sử dụng phương pháp TF-IDF (Term Frequency-Inverse Document Frequency). Tính toán ma trận tương đồng cosine giữa các vector biểu diễn của các bài hát. Ma trận này chứa thông tin về mức độ tương đồng giữa mỗi cặp bài hát trong tập dữ liệu.
Gợi ý âm nhạc:
Khi người dùng chọn một bài hát từ giao diện, hệ thống sẽ tìm kiếm index của bài hát đó trong dataframe.
Sau đó, hệ thống sẽ sắp xếp các bài hát khác dựa trên mức độ tương đồng với bài hát đã chọn. Mức độ tương đồng cao hơn sẽ đưa các bài hát đó lên phía trên trong danh sách gợi ý.
Bốn bước tiếp theo sau khi tìm kiếm index của bài hát đó trong dataframe là để lấy thông tin về nghệ sĩ và ảnh bìa album của các bài hát được gợi ý, thông qua API của Spotify.
Tải dữ liệu và tiền xử lý:
Chuỗi văn bản trong cột 'text' được chuyển thành chữ thường để đảm bảo tính nhất quán, các ký tự khôgn phải là chữ cái hoặc số và các ký tự xuống dòng được loại bỏ để làm sạch dữ liệu
Tách từ (Tokenization) và Stemming:
Sử dụng thư viện NLTK (Natural Language Toolkit) để tách chuỗi văn bản thành các từ riêng lẻ (Tokenization).
Sau đó, các từ này được chuyển về dạng gốc (Stemming) bằng cách sử dụng thuật toán PorterStemmer trong NLTK.
Quá trình này giúp làm giảm kích thước của từ vựng và chuẩn hóa các từ, từ đó cải thiện khả năng hiểu và xử lý của mô hình.
Tính toán độ tương đồng:
Sử dụng cosine_similarity từ scikit-learn để tính toán độ tương đồng cosine giữa các vector biểu diễn văn bản. Độ tương đồng cosine đo lường sự tương đồng giữa các mục văn bản dựa trên nội dung của chúng.
