# ĐẠI ÂN XÁ CỨU ĐỘ – THIÊN ĐÌNH TU TẬP V6 Ultra

Website tu tập và suy ngẫm bằng tiếng Việt, được đóng gói dưới dạng một trang HTML tĩnh (`index.html`). Giao diện sử dụng Tailwind CSS CDN và Three.js CDN; trình duyệt cần có kết nối Internet để tải các thư viện này.

## 1. Cấu trúc GitHub

Đặt các tệp theo cấu trúc sau ở thư mục gốc của repository:

```text
.
├── index.html
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml
```

`index.html` là tệp website chính. Không đổi tên tệp nếu chưa cập nhật đường dẫn trong cấu hình triển khai.

## 2. Triển khai GitHub Pages tự động

1. Tạo repository trên GitHub.
2. Tải `index.html`, `README.md` và thư mục `.github/workflows/deploy.yml` lên repository.
3. Đẩy các thay đổi lên nhánh `main`.
4. Mở **Settings → Pages** trong repository.
5. Ở mục **Build and deployment**, chọn **GitHub Actions** làm nguồn triển khai.
6. Mở tab **Actions** để theo dõi workflow `Deploy to GitHub Pages`.
7. Khi workflow chạy thành công, mở đường dẫn GitHub Pages hiển thị trong **Settings → Pages**.

Từ lần sau, mỗi lần cập nhật và push lên `main`, GitHub Actions sẽ tự động triển khai lại website.

## 3. Các tính năng và giới hạn triển khai

- Các chức năng HTML/CSS/JavaScript chạy trực tiếp trong trình duyệt.
- Dữ liệu được lưu trên thiết bị/trình duyệt nếu tính năng tương ứng dùng bộ nhớ cục bộ. Nên xuất bản sao lưu định kỳ nếu website có dữ liệu quan trọng.
- Giao diện tải Tailwind CSS và Three.js từ CDN, vì vậy cần Internet và các CDN phải truy cập được.
- Giọng đọc có sẵn của trình duyệt phụ thuộc thiết bị, trình duyệt và gói giọng nói đã cài.
- Trợ lý AI và giọng nói AI máy chủ gọi các endpoint `/api/chat` và `/api/speech`. GitHub Pages không chạy backend/API server; muốn dùng hai tính năng này cần triển khai backend riêng (ví dụ trên một dịch vụ serverless) và cấu hình địa chỉ API trong website.
- Không đặt `OPENAI_API_KEY` hoặc bất kỳ khóa bí mật nào trong `index.html`, README hay mã JavaScript gửi lên GitHub. Lưu khóa trong phần Environment/Secrets của dịch vụ backend.
- Chức năng PWA/offline cần có các tệp manifest và service worker hợp lệ được triển khai cùng website. Chỉ có `index.html` thì chưa đủ để bảo đảm cài đặt PWA hoặc chạy offline.

## 4. Cập nhật website

Thay nội dung `index.html` bằng phiên bản mới, commit và push lên nhánh `main`. Workflow sẽ tự động xuất bản phiên bản mới. Nếu trình duyệt vẫn hiện bản cũ, thử tải lại trang hoặc xóa cache của website.

## 5. Khắc phục sự cố

- **Workflow không chạy:** kiểm tra tệp có đúng đường dẫn `.github/workflows/deploy.yml` và nhánh đang dùng có phải `main` không.
- **Pages báo chưa cấu hình:** vào **Settings → Pages** và chọn **GitHub Actions**.
- **Trang trắng hoặc nút không hoạt động:** mở trang bằng trình duyệt mới nhất, tải lại trang; kiểm tra lỗi JavaScript trong Developer Tools → Console trên máy tính.
- **AI không phản hồi:** kiểm tra backend, endpoint `/api/chat`, CORS và cấu hình địa chỉ API. GitHub Pages không tự cung cấp endpoint này.
- **Cảnh 3D không hiện:** kiểm tra kết nối CDN, khả năng hỗ trợ WebGL và Console của trình duyệt.

## Giấy phép và nội dung

Chỉ sử dụng hình ảnh, âm thanh, thư viện và nội dung mà bạn có quyền sử dụng. Các bài suy ngẫm trong website không thay thế kinh văn, tư vấn chuyên môn hoặc hướng dẫn trực tiếp từ người hướng dẫn tu học.
