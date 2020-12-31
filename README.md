# ĐỒ ÁN CUỐI KỲ

## Chủ đề đồ án

- **Dự đoán điểm rating của các cuốn sách.**

- **Gợi ý sách cho người đọc.**

## Thông tin nhóm và phân công

| Họ và tên          | MSSV    | Phân công                                                    |
| ------------------ | ------- | ------------------------------------------------------------ |
| Nguyễn Hoàng Linh  | 1712559 | Thu thập dữ liệu.<br /> Hỗ trợ xây dựng mô hình cho bài toán. |
| Huỳnh Ngọc Quân    | 1712689 | Thu thập và phân tích dữ liệu.<br /> Viết báo cáo và phân công. |
| Huỳnh Lê Minh Nhật | 1712632 | Tiền xử lý.<br /> Xây dựng mô hình cho bài toán.             |



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



