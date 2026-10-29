# 236496_lamtranNhutKhoi

## 1. Giới thiệu dự án

**Food Management System** là ứng dụng quản lý món ăn, cho phép người dùng xem danh sách, xem chi tiết, thêm, cập nhật, xóa và tìm kiếm món ăn.

Dự án được xây dựng nhằm thực hành phát triển ứng dụng web full-stack và triển khai trên nền tảng đám mây.

## 2. Công nghệ sử dụng

- **Frontend:** React, Vite
- **Backend:** Node.js, Express
- **Database:** MongoDB Atlas
- **ODM:** Mongoose
- **Container:** Docker
- **Container Registry:** Docker Hub
- **Deployment:** Render
- **Source Control:** Git và GitHub

## 3. Cấu trúc dự án

```text
236496_lamtranNhutKhoi/
├── backend/
│   ├── models/
│   └── routes/
├── frontend/
├── .gitignore
└── README.md
```

## 4. Chức năng dự kiến

- Hiển thị danh sách món ăn.
- Xem chi tiết món ăn.
- Thêm món ăn mới.
- Cập nhật thông tin món ăn.
- Xóa món ăn.
- Tìm kiếm món ăn theo tên, loại món hoặc vùng miền.
- Kết nối cơ sở dữ liệu MongoDB Atlas.
- Đóng gói frontend và backend bằng Docker.
- Triển khai ứng dụng trên Render.

## 5. Cài đặt và chạy chương trình

Hướng dẫn cài đặt và chạy frontend, backend sẽ được cập nhật sau khi hoàn thiện mã nguồn.

## 6. Liên kết dự án

- **GitHub:** cập nhật sau.
- **Docker Hub Backend:** cập nhật sau.
- **Docker Hub Frontend:** cập nhật sau.
- **Frontend Render:** cập nhật sau.
- **Backend API Render:** cập nhật sau.

## 7. Bảo mật

Không đưa mật khẩu, access token hoặc chuỗi kết nối MongoDB có thông tin xác thực lên repository công khai. Sử dụng biến môi trường để cấu hình ứng dụng.
## Câu 5: Đóng gói Backend bằng Docker

### 1. Thông tin Docker Image

- Docker Hub Username: `nhutkhoi236496`
- Docker Image: `nhutkhoi236496/backend:1.0`
- Docker Hub URL: https://hub.docker.com/r/nhutkhoi236496/backend

### 2. Build Docker Image

Tại thư mục gốc dự án, chạy:

```bash
docker build -t nhutkhoi236496/backend:1.0 ./backend
```

### 3. Chạy Docker Container

Tạo file `backend/.env` với các biến môi trường cần thiết.

```bash
docker run -d --name backend-cau5-test -p 5001:5000 --env-file ./backend/.env nhutkhoi236496/backend:1.0
```

### 4. Kiểm tra Backend

```bash
docker ps
docker logs backend-cau5-test
curl -i http://localhost:5001/health
```

Kết quả đã kiểm thử:

- Backend chạy tại cổng `5000` trong container.
- MongoDB Atlas kết nối thành công.
- API `/health` trả về HTTP `200 OK`.

### 5. Bảo mật

- Không đưa file `.env` vào Docker Image.
- Không đưa thông tin đăng nhập MongoDB lên GitHub.
- Sử dụng `--env-file` để truyền biến môi trường khi chạy container.
## Câu 6: Đóng gói Frontend bằng Docker

### Docker Image
- Image: `nhutkhoi236496/frontend:1.0`
- Docker Hub: https://hub.docker.com/r/nhutkhoi236496/frontend

### Build Frontend

```bash
docker build -t nhutkhoi236496/frontend:1.0 ./frontend
```

### Chạy Frontend

```bash
docker run -d \
  --name frontend-cau6-test \
  -p 5175:80 \
  --add-host=host.docker.internal:host-gateway \
  nhutkhoi236496/frontend:1.0
```

### Kiểm tra ứng dụng

```bash
docker ps
curl -I http://localhost:5175/
curl -i http://localhost:5175/api/foods
```

Frontend sử dụng React, Vite và Nginx. Nginx phục vụ giao diện trên cổng 80 và chuyển tiếp yêu cầu API tới Backend.

### Bảo mật
- Không đưa file `.env` vào Docker Image.
- Không đưa mật khẩu hoặc thông tin nhạy cảm lên GitHub.