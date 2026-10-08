# Bài 3: Dockerfile đóng gói trang Web HTML tĩnh

## Mô tả

Đóng gói một trang HTML tĩnh vào Nginx Alpine image bằng Dockerfile siêu ngắn gọn.

## Cấu trúc thư mục

```
Bai3/
├── Dockerfile
├── index.html
└── README.md
```

## Nội dung file

### index.html
```html
<h1>Hello Docker Session 09!</h1>
```

### Dockerfile
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

## Hướng dẫn chạy

### 1. Build Docker image

```bash
docker build -t my-html-app:v1 .
```

### 2. Khởi chạy container

```bash
docker run -d -p 8081:80 --name html-app my-html-app:v1
```

### 3. Kiểm tra kết quả

```bash
curl http://localhost:8081
```

## Kết quả mong đợi

```
<h1>Hello Docker Session 09!</h1>
```

## Giải thích

| Lệnh | Ý nghĩa |
|------|---------|
| `FROM nginx:alpine` | Dùng Nginx trên Alpine Linux làm base image (nhẹ, bảo mật) |
| `COPY index.html /usr/share/nginx/html/index.html` | Sao chép file HTML vào thư mục mặc định của Nginx |
| `-p 8081:80` | Map cổng 8081 của host vào cổng 80 của container |
