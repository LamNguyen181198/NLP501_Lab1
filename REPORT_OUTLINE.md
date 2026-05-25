# Dan Bai Bao Cao - NLP501 Exercise 1

## 1. Gioi thieu
- De tai: Phan tich cam xuc va khong gian vector cho du lieu tweet.
- Muc tieu:
  - Part 1: Phan loai cam xuc.
  - Part 2: Xay dung word vectors va danh gia tuong dong.
  - Part 3: Xay dung he tim kiem tai lieu don gian.

## 2. Du lieu va tien xu ly
### 2.1 Nguon du lieu
- Dataset su dung: Twitter Entity Sentiment Analysis (Kaggle).
- File:
  - twitter_training.csv
  - twitter_validation.csv

### 2.2 Cach tai su dung du lieu giua cac phan
- Part 1 su dung train + validation de preprocess va train/evaluate classifier.
- Part 2 tai su dung clean_text tu Part 1 de tao corpus, co-occurrence, PCA va analogy.
- Part 3 tai su dung clean_text, sentiment, entity tu Part 1-2 de lap chi muc tim kiem TF-IDF.

### 2.3 Tien xu ly chinh
- Bo null/rong.
- Chuan hoa lowercase.
- Loai URL, mention, ky tu dac biet.
- Xu ly hashtag, emoji, slang, punctuation.
- Tokenization.

## 3. Part 1 - Sentiment Classification
### 3.1 Bai toan va thiet lap
- Bai toan 3 lop: Negative, Neutral, Positive.
- Chia train/test: 80/20 (stratify).

### 3.2 Trich xuat dac trung va mo hinh
- So sanh 2 kieu dac trung:
  - CountVectorizer (tan suat tu)
  - TF-IDF
- So sanh 2 mo hinh:
  - Logistic Regression
  - Multinomial Naive Bayes

### 3.3 Ket qua chinh (tu output notebook)
- Bang so sanh setup cho thay:
  - LogReg + CountVectorizer: Accuracy 0.8548, F1(weighted) 0.8545
  - LogReg + TF-IDF: Accuracy 0.8192, F1(weighted) 0.8186
  - MNB + CountVectorizer: Accuracy 0.7864, F1(weighted) 0.7835
  - MNB + TF-IDF: Accuracy 0.7802, F1(weighted) 0.7742
- Confusion matrix va error analysis:
  - Loi tap trung nhieu o lop Neutral, de nham sang Positive/Negative.

### 3.4 Nhan xet Part 1
- Tren dataset nay, CountVectorizer + Logistic Regression cho ket qua tot nhat.
- Lua chon dac trung can dua vao thuc nghiem cu the, khong mac dinh TF-IDF luon toi uu.

## 4. Part 2 - Word Vectors & Similarity
### 4.1 Co-occurrence va stopword filtering
- Co-occurrence matrix duoc xay voi window_size = 5 va sparse matrix.
- Sau khi loc stopwords:
  - Non-zero entries: 1,178,668 -> 947,594
  - Density: 0.047147 -> 0.037904
- Nhan xet: ma tran gon hon, giam nhieu tu chuc nang.

### 4.2 Giam chieu va tuong dong
- PCA 50D cho tinh toan, PCA 2D cho truc quan.
- Cosine similarity cho cac cap tu trong domain dat muc kha.

### 4.3 Analogy test
- So luong test: 10 cap quan he (random moi lan chay).
- Ket qua analogy dao dong giua cac lan chay va nhin chung con thap.

### 4.4 Nhan xet Part 2
- Pipeline co-occurrence + stopword filtering + PCA phu hop de phan tich tuong dong co ban.
- Chua du manh cho suy luan analogy phuc tap.

## 5. Part 3 - Document Retrieval
### 5.1 Muc tieu
- Tim kiem van ban bang TF-IDF + cosine similarity.

### 5.2 Thiet lap he thong
- Moi tweet duoc xem nhu 1 document.
- Xay index TF-IDF voi:
  - So documents: 61,689
  - Kich thuoc ma tran: (61,689, 20,000)
- Trien khai ham search_documents(query, top_k) de xep hang theo cosine score.

### 5.3 Danh gia truy van mau
- Truy van mau: xbox game update, love this game, server issue fix, bad customer support, new phone release.
- Danh gia nhanh Precision@5 (keyword rule): Mean Precision@5 = 1.0.

### 5.4 Nhan xet Part 3
- He thong retrieval chay on dinh va tra ve ket qua lien quan cho query ngan.
- Can bo sung thiet ke danh gia chat hon (human relevance labels) de ket qua co tinh hoc thuat cao hon.

## 6. Tong ket toan bai
- Da hoan thanh 3 phan theo dung yeu cau de bai:
  - Sentiment classification
  - Word vectors & similarity
  - Document retrieval
- Ket qua noi bat:
  - Setup tot nhat Part 1: LogReg + CountVectorizer
  - Part 2 giam nhieu sau loc stopwords
  - Part 3 tim kiem va xep hang duoc theo do lien quan

## 7. Han che va huong phat trien
- Han che:
  - Du lieu tweet ngan, nhieu noise va context mong.
  - Analogy score con thap va dao dong.
  - Danh gia retrieval hien tai con don gian.
- Huong phat trien:
  - Thu BM25 hoac query expansion cho retrieval.
  - Bo sung bo nhan relevance de danh gia retrieval bai ban hon.
  - Thu mo hinh contextual embeddings (chi de tham khao mo rong, khong thay cho phan yeu cau co ban).

## 8. Phu luc de kem
- Hinh confusion matrix.
- Hinh embedding 2D.
- Bang so sanh metric theo setup.
- Bang ket qua query retrieval mau.
