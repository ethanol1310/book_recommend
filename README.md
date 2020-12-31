# ĐỒ ÁN CUỐI KỲ

## Chủ đề đồ án

- **Dự đoán điểm rating của các cuốn sách.**

- **Gợi ý sách cho người đọc.**

## Thông tin nhóm và phân công

| Họ và tên          | MSSV    | Phân công                                                    |
| ------------------ | ------- | ------------------------------------------------------------ |
| Nguyễn Hoàng Linh  | 1712559 | Thu thập dữ liệu.<br /> Hỗ trợ xây dựng mô hình cho bài toán. |
| Huỳnh Ngọc Quân    | 1712689 | Thu thập và phân tích dữ liệu, đặt vấn đề và trả lời câu hỏi.<br /> Viết báo cáo và phân công. |
| Huỳnh Lê Minh Nhật | 1712632 | Tiền xử lý.<br /> Xây dựng mô hình cho bài toán.             |

# TỔ CHỨC THƯ MỤC 

Gồm có các Folder:

- `data`: chứa dữ liệu đã được crawl.
- `model`: chứa mô hình đã được huấn luyện.
- `source`: chứa source code dùng để crawl và các file notebook.

# NỘI DUNG 

## Đặt vấn đề

Chúng ta sẽ dựa vào bộ dữ liệu thư viện sách cùng với đánh giá của người đọc để tạo ra một mô hình có thể gợi ý sách cho người đọc và dự đoán điểm đánh giá của các đầu sách mới.

Với mô hình gợi ý sách cho người đọc vừa tiết kiệm được thời gian tìm sách, vừa tăng được khả năng mua sách của các độc giả trong thời kỳ thương mại điện tử phát triển.

Với mô hình dự đoán điểm đánh giá của các đầu sách mới sẽ giúp cho các tác giả cân nhắc được chủ đề, nội dung sáng tác trước khi bắt đầu viết một tác phẩm.

## Thu thập dữ liệu

### Nguồn dữ liệu

- Bộ dữ liệu được thu thập từ `goodreads`, thư viện đánh giá sách hàng đầu trên thế giới.

### Các bước thu thập dữ liệu

#### 1. Thu thập url thư viện sách

#### 2. Lấy dữ liệu sách từ url đã thu thập được ở bước 1

#### 3. Lấy url và đánh giá của user từ comment của mỗi url ở bước 1

#### 4. Lấy dữ liệu chi tiết của user từ url ở bước 3



# Tổng quan dữ liệu

## Tập dữ liệu info_book_detail.csv

### Ý nghĩa dòng dữ liệu

Mỗi dòng mô tả thông tin về một cuốn sách trên goodreads với các thông tin chi tiết về tựa đề, tác giả, mô tả, điểm đánh giá, ngày ra mắt...

**Tổng quan**

Dữ liệu gồm 94525 dòng và 14 cột:

- Có 90921 tựa sách, chứng tỏ có dữ liệu bị trùng lặp.
- Các cột có chứa giá trị null: Description, Num_pages, Book_Format, Time_publish, Publisher, ISBN, Language, Genres
- Tổng số tác giả là: 18856.
- Tổng số định dạng xuất bản là: 327.
- Có 17265 nhà xuất bản.
- Dữ liệu chứa các cuốn sách đến từ 87 ngôn ngữ.

### Ý nghĩa các cột dữ liệu

- **Book_Title**: Tên cuốn sách.
- **Author_Name**: Tác giả.
- **Description**: Mô tả cuốn sách.
- **Rating**: Rating của cuốn sách, được đánh giá bởi người đọc.
- **Rating_Counts**: Tổng số rating.
- **Reviews_Counts**: Tổng số đánh giá. 
- **Num_pages**: Tổng số trang của sách.
- **Book_Format**: Hình thức xuất bản cuốn sách.
- **Time_publish**: Thời gian sách được ra mắt.
- **Publisher**: Nhà xuất bản sách.
- **ISBN**: Mã số tiêu chuẩn của sách.
- **Language**: Ngôn ngữ cuốn sách.
- **Genres**: Thể loại của sách.
- **Book_Url**: Url sách.

**Cột cần dự đoán là Rating**

## Tập dữ liệu user_rating_book.csv

### Ý nghĩa dòng dữ liệu

Mỗi dòng mô tả thông tin user và điểm đánh giá của user đối với một tựa sách. 

Tập dữ liệu này được dùng để hỗ trợ cho mô hình gợi ý sách.

Tập dữ liệu có 157971 dòng và 5 cột với 28274 user đã đánh giá trên 5006 đầu sách.

### Ý nghĩa cột dữ liệu

- **book_title**: Tên cuốn sách.
- **url_book**: Url của cuốn sách.
- **username**: Tên của user đó.
- **user_url**: Url của user.
- **user_rating**: Điểm đánh giá của user đối với tựa sách.

# Đánh giá đồ án

## Kết quả đã đạt được

## Ý tưởng có thể phát triển thêm



# Hướng dẫn 

## Hướng dẫn crawl dữ liệu

#### 1. Thu thập url thư viện sách

```

```



#### 2. Lấy dữ liệu sách từ url đã thu thập được ở bước 1

```

```



#### 3. Lấy url và đánh giá của user từ comment của mỗi url ở bước 1

```
python crawl_user.py --min_index <index_range_min> --max_index <index_range_max>
```

Trong đó:

- `<index_range_min` và `<index_range_max>` là index của sách ở tập dữ liệu bước 1 `Info_Book_Url.csv`



#### 4. Lấy dữ liệu chi tiết của user từ url ở bước 3

```

```



## Hướng dẫn sử dụng model



