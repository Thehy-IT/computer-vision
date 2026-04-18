# BÁO CÁO THỰC HÀNH: PHÁT HIỆN ĐẶC TRƯNG VÀ ĐỐI SÁNH ẢNH
## Bài 4: So sánh sự tương đồng của các hình ảnh sử dụng Wavelet

**Thông tin nhóm thực hiện:**

| STT | Họ và Tên | MSSV | Vai trò/Đánh giá |
|-----|-----------|------|------------------|
| 1 | **Huỳnh Thế Hy** | 051205009083 | Nhóm trưởng |
| 2 | Nghiêm Đức Thuận | 060205003756 | Thành viên |
| 3 | Đào Thiện Nhân | 052205008343 | Thành viên |
| 4 | Tạ Nguyễn Quốc Triệu | 051205004949 | Thành viên |
| 5 | Hoàng Phú | 2251120373 | Thành viên |
| 6 | Thanh Tân | | Thành viên |

---

## I. MỤC TIÊU BÀI TẬP
1. Hiểu và ứng dụng biến đổi Wavelet rời rạc (DWT) để trích xuất thông tin đặc trưng của ảnh.
2. Xây dựng thuật toán tạo mã băm (Image Hashing) từ các hệ số Wavelet để giảm chiều dữ liệu.
3. Sử dụng khoảng cách Hamming để định lượng mức độ tương đồng giữa các hình ảnh.
4. Đánh giá hiệu quả của mô hình qua các chỉ số: Accuracy, Recall, Specificity và đường cong ROC.

---

## II. CƠ SỞ LÝ THUYẾT
### 1. Biến đổi Wavelet rời rạc (DWT)
DWT phân tách tín hiệu ảnh thành các dải tần số khác nhau. Trong xử lý ảnh 2D, một mức phân tách tạo ra 4 thành phần:
- **LL (Low-Low)**: Thành phần xấp xỉ, chứa cấu trúc chính của ảnh.
- **LH, HL, HH**: Các thành phần chi tiết chứa thông tin cạnh (ngang, dọc, chéo).

### 2. Wavelet Hashing
Sử dụng thành phần tần số thấp (LL) để tạo mã băm vì nó giữ được đặc điểm nhận dạng cốt lõi và ít nhạy cảm với nhiễu.

### 3. Khoảng cách Hamming
Đo lường số lượng bit khác nhau giữa hai chuỗi nhị phân có cùng độ dài. Tỷ lệ sai biệt càng thấp, độ tương đồng của ảnh càng cao.

---

## III. QUY TRÌNH THỰC HIỆN
1. **Tiền xử lý**: Chuyển ảnh về mức xám (Grayscale) và chuẩn hóa kích thước (Resize).
2. **Biến đổi DWT**: Sử dụng Wavelet Haar để trích xuất ma trận LL.
3. **Tạo mã băm**: 
   - Chuẩn hóa ma trận LL về đoạn [0, 1].
   - Lượng tử hóa dựa trên giá trị trung bình để chuyển về dạng nhị phân.
4. **Tính toán**: Tính khoảng cách Hamming giữa các cặp mã băm.
5. **Đánh giá**: So sánh với ngưỡng (Threshold) để đưa ra kết luận SIMILAR hoặc DIFFERENT.

---

## IV. KẾT QUẢ VÀ THẢO LUẬN

### 1. Dữ liệu thực nghiệm
Nhóm sử dụng các cặp ảnh tương đồng (cùng đối tượng nhưng thay đổi nhẹ về góc độ/ánh sáng) và các ảnh hoàn toàn khác biệt.

![Hình 1: Các ảnh đầu vào](../data/final_reports/hinh1_anh_goc.png)

### 2. Phân tích thành phần Wavelet
Thành phần LL được trích xuất cho thấy hình ảnh thu nhỏ nhưng vẫn giữ nguyên cấu trúc vật thể, trong khi các thành phần detail (LH, HL, HH) tập trung vào các đường biên.

![Hình 3: Các thành phần Wavelet](../data/final_reports/hinh3_wavelet_components.png)

### 3. Ma trận băm nhị phân
Quy trình chuyển đổi từ ảnh xám sang ma trận băm giúp tối ưu hóa không gian lưu trữ và tốc độ đối sánh.

![Hình 4: Quy trình trích xuất băm](../data/final_reports/hinh4_quy_trinh_hash.png)

### 4. Đánh giá khoảng cách Hamming
Kết quả thực nghiệm cho thấy sự phân hóa rõ rệt giữa nhóm ảnh tương đồng và khác biệt.

![Hình 6: Phân tích khoảng cách Hamming](../data/final_reports/hinh6_hamming_distance.png)

---

## V. ĐÁNH GIÁ HIỆU NĂNG

Dựa trên tập dữ liệu thực nghiệm, mô hình đạt được các chỉ số sau:

- **Accuracy (Độ chính xác)**: Phản ánh tỷ lệ dự đoán đúng trên tổng số cặp thử nghiệm.
- **Recall (Độ nhạy)**: Khả năng phát hiện chính xác các cặp ảnh thực sự tương đồng.
- **Specificity (Độ đặc hiệu)**: Khả năng nhận diện chính xác các cặp ảnh khác biệt.

![Hình 7: Dashboard chỉ số](../data/final_reports/hinh7_dashboard_metrics.png)
![Hình 9: Đường cong ROC](../data/final_reports/hinh9_roc_curve.png)

---

## VI. KẾT LUẬN
1. Phương pháp Wavelet Hash hoạt động hiệu quả cho bài toán đối sánh ảnh mức độ cơ bản.
2. Khoảng cách Hamming cung cấp tốc độ xử lý nhanh, phù hợp cho các ứng dụng tìm kiếm ảnh lớn.
3. Hệ thống có độ ổn định cao với các thay đổi nhỏ về cường độ sáng nhưng cần cải thiện thêm khả năng kháng các biến đổi hình học mạnh (xoay, lật).

---
*Ngày hoàn thành: 18/04/2026*
*Người báo cáo: Huỳnh Thế Hy*
