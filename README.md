# Xử lý ảnh và Thị giác máy tính (Computer Vision)

Dự án thực hành môn học **Xử lý ảnh và thị giác máy tính**. Dự án bao gồm các bài tập về xử lý ảnh sử dụng Python, OpenCV, PyWavelets và các thư viện hỗ trợ khác trong môi trường Jupyter Notebook.

## 👨‍🎓 Thông Tin Sinh Viên
- **Họ và tên:** Huỳnh Thế Hy  
- **MSSV:** 051205009083

## 📂 Cấu trúc thư mục dự án
Dự án được tổ chức theo chuẩn nghiên cứu và phát triển phần mềm:

```text
computer-vision/
├── data/                 # Dữ liệu hình ảnh
│   ├── input/            # Ảnh mẫu đầu vào (raw images)
│   ├── processed/        # Kết quả sau khi xử lý (output)
│   └── final_reports/    # Ảnh chất lượng cao dùng cho báo cáo
├── docs/                 # Tài liệu bài giảng & lý thuyết (PDF Chapters)
├── notebooks/            # Các bài thực hành (Jupyter Notebooks)
│   ├── Lab1.ipynb        # Xử lý cơ bản, không gian màu
│   ├── Lab2.1.ipynb      # Lọc nhiễu & tăng cường ảnh
│   ├── Lab2.2.ipynb      # Canny, Hough Transform
│   ├── Lab3.1.ipynb      # So sánh tương đồng bằng Wavelet (DWT)
│   └── Lab3.2.ipynb      # Các kỹ thuật trích xuất đặc trưng khác
├── src/                  # Mã nguồn Python mở rộng (.py)
├── requirements.txt      # Danh sách thư viện cần thiết
└── README.md             # Giới thiệu dự án
```

## 🛠️ Cài đặt & Sử dụng

### 1. Tạo môi trường ảo (Khuyên dùng)
```powershell
python -m venv .venv
```

### 2. Kích hoạt môi trường ảo
Trên Windows:
```powershell
.\.venv\Scripts\activate
```

### 3. Cài đặt các thư viện phụ thuộc
```powershell
pip install -r requirements.txt
```

### 4. Chạy Jupyter Notebook
```powershell
jupyter notebook
```
Sau đó, điều hướng vào thư mục `notebooks/` để mở các bài thực hành.

## 🧪 Các nội dung trọng tâm
- **Biến đổi không gian màu:** RGB, HSV, Grayscale.
- **Lọc và tăng cường:** Gaussian, Median, Sobel, Canny.
- **Biến đổi Wavelet (DWT):** Sử dụng `PyWavelets` để phân tích tần số ảnh.
- **Đánh giá hiệu năng:** Tính toán khoảng cách Hamming, vẽ đường cong ROC và chỉ số AUC.

---
*Chúc bạn học tập và nghiên cứu tốt!*
