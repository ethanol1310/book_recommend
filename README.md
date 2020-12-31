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

Tập dữ liệu có 463979 dòng và 5 cột với 27047 user đã đánh giá trên 150060 đầu sách.

### Ý nghĩa cột dữ liệu

- **book_title**: Tên cuốn sách.
- **url_book**: Url của cuốn sách.
- **username**: Tên của user đó.
- **user_url**: Url của user.
- **user_rating**: Điểm đánh giá của user đối với tựa sách.

# Đánh giá đồ án

### Rating Prediction

Kết quả đạt được:
- KNN-based collaborative filtering (CF): 0.9025 (RMSE)
- Matrix factorization & Deep learning (MF): 0.7888 (RMSE)

Nhìn chung kết quả này là chấp nhận được đối với một tập dữ liệu khá khiêm tốn cũng như chưa mang tính tổng quát mà nhóm tự crawl.

Bên cạnh đó, ta thấy MF tỏ ra vượt trội hơn so với CF về độ chính xác. Tuy nhiên, chi phí tính toán của MF khá cao hơn CF, do đó tuỳ tình huống mà ta có thể chọn lựa giải pháp phù hợp.

### Book Recommendation

Ở đây, nhóm cũng sử dụng hai giải pháp tương ứng với hai giải pháp dự đoán rating. Cả hai đều trả về một danh sách gợi ý tương đối tốt, tuy nhiên chúng cũng có những ưu, nhược điểm sau:
- Collaborative filtering (CF) based:
    + CF đưa ra gợi ý dựa vào sự tương đồng về mặt rating của mỗi cuốn sách, nên CF có thể gợi ý cho người đọc những cuốn sách mới nằm ngoài những chủ đề, nội dung mà họ hay đọc.
    + Tuy nhiên điều này cũng mang lại một nhược điểm: những cuốn sách mới, có ít lượt rating sẽ gần như hiếm khi được gợi ý do không đủ dữ liệu (cold start problem).

- Content based:
    + Trái với CF, giải pháp này gợi ý cho người đọc dựa trên sự tương đồng về mặt chủ đề, thể loại, nội dung của sách. Do đó, các cuốn sách mới có ít lượt rating vẫn có thể được gợi ý bình thường.
    + Tuy nhiên, đây cũng là một nhược điểm khi hệ thống chỉ gợi ý các cuốn sách tương đồng mà không giới thiệu các chủ đề hay thể loại khác. Mặt khác, việc gán nhãn chủ đề, nội dung cho sách cũng ảnh hưởng rất lớn đến độ hiệu quả của giải pháp này.

### Thiếu sót và hướng phát triển

- Bộ dữ liệu chưa thật sự tốt, còn khá ít cũng như chưa mang tính bao quát

&#8594;  Dành nhiều thời gian hơn cho việc thu thập và xử lý dữ liệu, kết hợp tìm thêm các nguồn chính thống

- Cả 2 giải pháp đều có những ưu, nhược điểm riêng, để áp dụng thực tế vẫn cần cải tiến nhiều hơn

&#8594; Sử dụng các giải pháp hybrid, kết hợp cả content-based và collaborative filering based để đạt hiệu quả cao hơn cho hệ thống gợi ý

# Hướng dẫn 

## Hướng dẫn crawl dữ liệu

#### 1. Thu thập url thư viện sách

- Trong notebook, việc thu thập url thư viện sách được chia ra làm 4 phương hướng chính:
- **Lựa chọn theo thể loại (genre)**: Có tổng cộng 21 thể loại khác nhau trong goodreads. Ví dụ url mẫu: https://www.goodreads.com/shelf/show/art
- **Lựa chọn theo Thời gian (Tháng, năm)**: Được crawl trong khoảng thời gian Jan-2019 -> Dec-2021. Ví dụ url mẫu: https://www.goodreads.com/book/popular_by_date/2020/12?ref=nav_brws_newrels
- **Lựa chọn theo Album**: Được crawl theo album được chọn trước. Ví dụ: https://www.goodreads.com/list/show/264.Books_That_Everyone_Should_Read_At_Least_Once
- **Lựa chọn theo Tác giả**: Được crawl theo đường link của mỗi tác giả để lấy danh sách booksl, danh sách tác giả đã được có trong quá trình crawl 3 phần trước. Ví dụ: https://www.goodreads.com/author/list/1825.Harper_Lee



#### 2. Lấy dữ liệu sách từ url đã thu thập được ở bước 1

```
run crawl_info_book_detail.py --min_index <index_range_min> --max_index <index_range_max>

```

Trong đó:

- `<index_range_min` và `<index_range_max>` là index của sách ở tập dữ liệu bước 1 `Info_Book_Url.csv`


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

- Cài đặt thư viện surprise cho KNN-based collaborative filtering: ```pip install scikit-surprise```

- Copy 2 file ```info_book_detail_per_30.csv``` và ```user_rating_book_filter_per_30.csv``` vào cùng thư mục với file notebook ```Goodreads-Model.ipynb```

- Phần model đã được trình bày cụ thể trong file notebook

# Tham khảo

[1] https://realpython.com/build-recommendation-engine-collaborative-filtering/#what-is-collaborative-filtering

[2] https://towardsdatascience.com/prototyping-a-recommender-system-step-by-step-part-1-knn-item-based-collaborative-filtering-637969614ea

[3] https://towardsdatascience.com/creating-a-hybrid-content-collaborative-movie-recommender-using-deep-learning-cc8b431618af

[4] https://calvinfeng.gitbook.io/machine-learning-notebook/supervised-learning/recommender/neural_collaborative_filtering

[5] https://calvinfeng.gitbook.io/machine-learning-notebook/supervised-learning/recommender/neural_collaborative_filtering

[6] https://towardsdatascience.com/building-a-content-based-book-recommendation-engine-9fd4d57a4da
