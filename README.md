# Kapi House Shared 🐦🏠

Website: Kapi Shared dùng **Firebase Firestore** để lưu hồ sơ phòng và **GitHub Pages** để hiển thị giao diện.

## Quyền truy cập
- **Khách không đăng nhập:** đọc collection `publicRooms` chỉ chứa dữ liệu tổng quan (không có địa chỉ chi tiết, SĐT, ghi chú, nguồn liên hệ, đường link hoặc phản hồi).
- **Tài khoản có quyền:** đọc/ghi collection `rooms`; khi lưu ứng dụng đồng thời ghi một bản dữ liệu được rút gọn vào `publicRooms`.
- Dữ liệu trước khi cập nhật bản web có thể chưa có bản sao công khai: cần mở một phòng bằng tài khoản quản trị và lưu lại để hiện trong chế độ khách.
- Bất kỳ ai cũng có thể nhìn thấy dữ liệu công khai; đừng nhập thông tin nhạy cảm vào các trường hiển thị công khai.

## 1. Bật GitHub Pages
Repository → Settings → Pages → Build and deployment → **Deploy from a branch**, `main`, `/(root)` → Save.

Trang dự kiến: https://vand21130-oss.github.io/kapi-house-shared/

## 2. Firebase Authentication
Authentication → Settings → Authorized domains → thêm `vand21130-oss.github.io` để người quản trị đăng nhập Google trên domain GitHub Pages.

## 3. Firestore Security Rules
**KHÔNG thay thế toàn bộ Rules đang chạy bằng file ví dụ.**
Giữ nguyên hàm `familyMember()`, rule `match /rooms/{roomId}` và rule chặn cuối cùng. Chỉ chèn đoạn `match /publicRooms/{roomId}` từ `PUBLIC_RULES_SNIPPET.txt` vào trước dòng `match /{document=**}`.

Đoạn mới cho phép khách chỉ đọc dữ liệu công khai, còn chỉnh sửa vẫn yêu cầu tài khoản trong `familyMember()`. Chỉ tài khoản được cấp quyền mới được thêm phòng.

## 4. Kiểm thử trước khi gửi link
1. Mở website ở cửa sổ ẩn danh: phải thấy danh sách tổng quan, không yêu cầu Gmail.
2. Đăng nhập Google bằng tài khoản quản trị: phải thấy dữ liệu đầy đủ và nút Thêm phòng.
3. Thêm một phòng mẫu; kiểm tra sau khi tải lại.
4. Mở lại ẩn danh: phải thấy bản tổng quan, tuyệt đối không thấy số điện thoại, địa chỉ chi tiết hoặc ghi chú.
5. Nếu chưa đạt, không sử dụng để nhập phòng thật.

Không cần Node.js hay Apps Script. GitHub Pages chỉ host mã nguồn web; Firebase giữ dữ liệu.
