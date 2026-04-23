# Hướng dẫn chi tiết Bài thực hành Lab 3.2: Nhận diện khuôn mặt thời gian thực

Hướng dẫn này dành cho các thành viên mới để triển khai hệ thống nhận diện khuôn mặt sử dụng **MTCNN** (phát hiện) và **FaceNet** (trích xuất đặc trưng).

## 1. Chuẩn bị môi trường

Trước khi bắt đầu, hãy đảm bảo bạn đã cài đặt Python (khuyên dùng 3.10.12) và môi trường ảo.

### Cài đặt thư viện

Mở Terminal tại thư mục dự án và chạy:

```bash
pip install opencv-python mtcnn keras-facenet scikit-learn Pillow numpy matplotlib tensorflow pandas
```

*Lưu ý: Nếu bạn sử dụng Notebook, bạn có thể bỏ comment và chạy cell số 2 trong `Lab3.2.ipynb`.*

## 2. Cấu trúc thư mục dữ liệu

Để hệ thống hoạt động, bạn cần chuẩn bị dữ liệu tại đường dẫn `data/`:

```text
computer-vision/
├── data/
│   ├── registered_faces/        # Nơi lưu trữ database (tự động tạo)
│   └── faceID/                  # Nơi chứa ảnh để import hàng loạt (tùy chọn)
│       ├── Hoang_Phu/           # Thư mục con mang tên người
│       │   └── img1.jpg
│       └── The_Hy/
│           └── img1.jpg
└── notebooks/
    └── Lab3.2.ipynb
```

## 3. Các bước thực hiện trong Notebook

Mở `notebooks/Lab3.2.ipynb` và chạy tuần tự các bước:

### Bước 1: Khởi tạo (Cell 3, 4)

* Nhập các thư viện cần thiết.
* Tải mô hình MTCNN và FaceNet. Việc này có thể mất chút thời gian ở lần chạy đầu tiên để tải weights từ internet.

### Bước 2: Kiểm tra Camera (Cell 5)

* Đảm bảo Webcam của bạn đang hoạt động. Nếu báo "Không tìm thấy Camera", hãy kiểm tra quyền truy cập hoặc thay đổi `CAMERA_INDEX = 0` thành `1` hoặc `2`.

### Bước 3: Xây dựng Database (Cell 7)

* Hệ thống sẽ quét thư mục `data/registered_faces`.
* Nếu là lần đầu, nó sẽ tạo file `face_database.pkl` để lưu trữ vector đặc trưng (embeddings).

### Bước 4: Import dữ liệu có sẵn (Cell 9.1) - *Tùy chọn*

* Nếu bạn đã có ảnh trong thư mục `data/faceID/`, chạy cell này để hệ thống tự động trích xuất và đưa vào danh sách nhận diện.

### Bước 5: Chạy nhận diện thời gian thực (Cell 10)

* Một cửa sổ camera sẽ hiện lên.
* **Q**: Nhấn phím 'q' trên cửa sổ camera để thoát.
* **S**: Nhấn phím 's' để đăng ký khuôn mặt đang hiện trên màn hình. Sau khi nhấn 's', bạn cần quay lại giao diện Jupyter Notebook để nhập tên.

## 4. Xem kết quả điểm danh

Sau khi chạy nhận diện, thông tin sẽ được lưu vào file:
`data/registered_faces/attendance_log.csv`

Bạn có thể chạy **Cell 11** để xem danh sách những người đã được nhận diện kèm thời gian cụ thể.

## 5. Lưu ý quan trọng

* **Ánh sáng**: Đảm bảo khuôn mặt đủ sáng để MTCNN có thể phát hiện chính xác.
* **Góc độ**: FaceNet hoạt động tốt nhất với góc nhìn thẳng.
* **Lỗi thư viện**: Nếu gặp lỗi `AttributeError: module 'keras.utils' has no attribute 'get_file'`, hãy kiểm tra lại phiên bản `tensorflow` và `keras-facenet`.
