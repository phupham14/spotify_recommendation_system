# 🎵 **HỆ THỐNG GỢI Ý ÂM NHẠC DỰA TRÊN TƯƠNG ĐỒNG NỘI DUNG**

## 📌 **1. Phương pháp và thuật toán sử dụng**

### 🔹 **Tính toán tương đồng**

- Dữ liệu bài hát được biểu diễn dưới dạng vector bằng phương pháp **TF-IDF (Term Frequency-Inverse Document Frequency)**.
- Tính toán **ma trận tương đồng cosine** giữa các vector bài hát để đo mức độ tương đồng giữa từng cặp bài hát.

### 🔹 **Gợi ý âm nhạc**

- Khi người dùng chọn một bài hát từ giao diện:
  - Tìm **index** của bài hát trong `DataFrame`.
  - Sắp xếp các bài hát khác theo mức độ tương đồng giảm dần (độ tương đồng cao hơn sẽ được ưu tiên).
  - Lấy thông tin về **nghệ sĩ** và **ảnh bìa album** của các bài hát gợi ý bằng cách gọi **Spotify API**.

## 🧹 **2. Tải dữ liệu và tiền xử lý**

- **Chuyển tất cả văn bản thành chữ thường** để thống nhất định dạng.
- **Loại bỏ** các ký tự không phải chữ cái hoặc số, và các ký tự xuống dòng.
- **Tách từ (Tokenization)** bằng thư viện **NLTK**.
- **Stemming** sử dụng **PorterStemmer** để đưa từ về dạng gốc.
- Mục tiêu của bước này là **giảm kích thước từ vựng** và **chuẩn hóa nội dung**.

## 🔍 **3. Tính toán độ tương đồng**

- Sử dụng `cosine_similarity` từ thư viện **scikit-learn** để đo độ tương đồng giữa các vector.
- Độ tương đồng cosine phản ánh mức độ giống nhau về **nội dung** giữa các bài hát.

## ⚠️ **4. Các khó khăn cần tiếp tục giải quyết**

### ❗ **Xử lý dữ liệu không chuẩn**

- Dữ liệu có thể chứa:
  - Ký tự đặc biệt
  - Dấu câu
  - Ký tự lỗi
- Cần làm sạch dữ liệu kỹ lưỡng trước khi xử lý văn bản.

### ❗ **Hiệu suất tính toán**

- Các bước xử lý (TF-IDF, cosine similarity) có thể tiêu tốn nhiều **thời gian** và **tài nguyên** trên dữ liệu lớn.
- Cần tối ưu mã hoặc dùng các phương pháp như:
  - **Sparse matrix**
  - **Approximate Nearest Neighbors (ANN)**

### ❗ **Xử lý lỗi và ngoại lệ**

- Cần bắt và xử lý các trường hợp như:
  - Dữ liệu không hợp lệ từ **Spotify API**
  - Lỗi trong lúc tính toán
  - Lỗi khi tải hoặc đọc dữ liệu

### ❗ **Tối ưu hóa gợi ý**

- Thuật toán gợi ý hiện tại đơn giản, dựa trên nội dung.
- Có thể cải thiện bằng cách:
  - Kết hợp **dữ liệu người dùng (user-based filtering)**
  - Hoặc thêm các yếu tố như **thể loại**, **tempo**, **ngữ cảnh nghe nhạc**
