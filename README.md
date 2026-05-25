# NLP501 - Checklist Bài Tập 1

## BÀI TẬP 1: Phân Tích Cảm Xúc & Không Gian Vector

## 1. Thông tin chung
- Môn học: NLP501 - Natural Language Processing
- Trọng số: 10% tổng điểm
- Hạn nộp: Sau 2 buổi
- Hình thức: Cá nhân

## 2. Yêu cầu chi tiết

### Phần 1: Phân loại cảm xúc
Mô tả: Xây dựng bộ phân loại cảm xúc (positive/negative) sử dụng Logistic Regression hoặc Naive Bayes.

Yêu cầu:
- [ ] Chọn và tiền xử lý dataset (Twitter Sentiment hoặc IMDB Reviews, hoặc bất kỳ dữ liệu văn bản)
- [ ] Triển khai trích xuất đặc trưng: tần suất từ, đặc trưng TF-IDF
- [ ] Huấn luyện mô hình Logistic Regression HOẶC Naive Bayes
- [ ] Đánh giá với accuracy, precision, recall, F1-score
- [ ] Phân tích confusion matrix và các lỗi phổ biến

Trong đó:
- [ ] Chia train/test set với tỷ lệ 80/20 hoặc 70/30
- [ ] Tiền xử lý: lowercase, remove punctuation, tokenization
- [ ] So sánh ít nhất 2 phương pháp trích xuất đặc trưng

### Phần 2: Word Vectors & Similarity
Mô tả: Xây dựng word vectors từ corpus và tính toán độ tương đồng giữa các từ.

Yêu cầu:
- [ ] Xây dựng co-occurrence matrix từ corpus
- [ ] Áp dụng PCA để giảm chiều word vectors
- [ ] Tính cosine similarity giữa các cặp từ
- [ ] Trực quan hóa word embeddings trong không gian 2D
- [ ] Thực hiện kiểm thử word analogy (king - man + woman = queen)

Trong đó:
- [ ] Sử dụng context window size (3, 5, v.v.)
- [ ] Áp dụng PCA giảm về số chiều nhỏ hơn (30, 50, v.v.)
- [ ] Kiểm thử với ít nhất 10 cặp từ có quan hệ ngữ nghĩa

### Phần 3: Tìm kiếm tài liệu
Mô tả: Triển khai hệ thống tìm kiếm văn bản đơn giản sử dụng TF-IDF.

Nhiệm vụ:
- [ ] Xây dựng TF-IDF vectors cho tập documents
- [ ] Triển khai hàm tìm kiếm với cosine similarity
- [ ] Xếp hạng kết quả theo độ liên quan
- [ ] Tạo giao diện đơn giản (command line hoặc notebook)
- [ ] Đánh giá với các truy vấn mẫu

Dataset gợi ý:
- [ ] AG News Dataset (các bài báo)
- [ ] 20 Newsgroups Dataset
- [ ] Tự tạo corpus từ các bài viết Wikipedia

## 3. Sản phẩm nộp
- Jupyter Notebook (.ipynb) với đầy đủ code và giải thích
- Báo cáo ngắn (PDF/Docs) gồm: phương pháp, kết quả, phân tích

## 4. Lưu ý
- Được phép sử dụng thư viện: numpy, pandas, sklearn, nltk, gensim
- Không sử dụng pre-trained embeddings cho Part B
