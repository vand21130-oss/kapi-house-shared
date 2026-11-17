# Kapi House Shared 🏠🐦

Trang quản lý phòng trọ Bách Khoa dành cho hai chị em, lưu chung trên **Firebase Firestore** và đăng nhập bằng **Google Authentication**.

## Trạng thái
Đây là mã giao diện tĩnh. Cần bật **GitHub Pages** và thêm domain GitHub Pages vào **Firebase Authentication → Settings → Authorized domains** trước khi đăng nhập trên web.

## Bật GitHub Pages
1. GitHub repository → **Settings → Pages**.
2. Ở **Build and deployment**, chọn **Deploy from a branch**.
3. Branch: **main**, folder: **/(root)** → **Save**.
4. Website dự kiến: https://vand21130-oss.github.io/kapi-house-shared/

## Bảo vệ dữ liệu
Mã nguồn repo là public. Thông tin cấu hình Firebase phía client (apiKey, projectId, v.v.) không phải khóa quản trị. **Không đưa dữ liệu phòng trọ, mật khẩu, token, khóa dịch vụ hoặc email riêng lên repository**.
Cần giữ **Firestore Security Rules** giới hạn hai tài khoản được phép truy cập. Google Login chỉ xác thực danh tính, không tự phân quyền.

## Khi nào có thể dùng thật?
Chỉ sau khi thử thành công: đăng nhập tài khoản được phép, thêm một phòng mẫu, tải lại vẫn thấy dữ liệu, sửa phòng và kiểm tra trên thiết bị thứ hai.
Cần thêm email Google của chị vào Firestore Rules sau khi được chị cung cấp.

## Lưu ý
- Hiện chưa kiểm chứng Pages đã bật hay việc đăng nhập/lưu trên dự án Firebase thực tế.
- Dữ liệu lưu trên Firestore, không phải trên GitHub.
- Có nút xuất JSON dự phòng trong ứng dụng.
