# Hướng dẫn Cài đặt Hệ thống Điểm danh

## Phần 1: Cấu hình Backend (Google Sheets)

1. Mở file Google Sheet "ĐIỂM DANH-BTVN-K7" của bạn.
2. Vào menu **Tiện ích mở rộng (Extensions)** > **Apps Script**.
3. Xóa hết mã cũ trong file `Mã.gs` (hoặc `Code.gs`) và copy toàn bộ nội dung từ file `apps_script.js` vào đó.
4. **Quan trọng**: 
   - Điền ID của Google Sheet vào biến `SHEET_ID` ở dòng đầu tiên của script.
   - Kiểm tra tên Sheet `SHEET_NAME` có đúng là `"ĐIỂM DANH-BTVN-K7"` không.
   - Kiểm tra lại các cột `Điểm danh B1`... trong Sheet có khớp với cấu hình trong code không.
5. Nhấn nút **Lưu** (biểu tượng đĩa mềm).
6. Nhấn nút **Triển khai (Deploy)** (góc trên bên phải) > **Tùy chọn triển khai mới (New deployment)**.
7. Chọn loại: **Ứng dụng Web (Web app)**.
   - Mô tả: "Điểm danh API".
   - Thực thi dưới dạng: **Tôi (Me)**.
   - Ai có quyền truy cập: **Bất kỳ ai (Anyone)** (Rất quan trọng để frontend có thể gọi được).
8. Nhấn **Triển khai**.
9. Copy **URL ứng dụng web (Web App URL)** (có dạng `https://script.google.com/macros/s/.../exec`).

## Phần 2: Cấu hình Frontend

1. Mở file `index.html` bằng trình duyệt web để kiểm tra giao diện.
2. Nhấn vào biểu tượng **Cài đặt (Bánh răng)** ở góc trên bên phải.
3. Dán **URL ứng dụng web** bạn vừa copy ở bước trên vào ô trống.
4. Nhấn **Lưu**.

## Phần 3: Đưa lên GitHub (Để mọi người truy cập)

1. Upload file `index.html` lên kho lưu trữ GitHub của bạn.
2. Vào **Settings** của repository > Chọn mục **Pages** ở menu bên trái.
3. Tại mục **Branch**, chọn `main` (hoặc `master`) và folder `/ (root)`. Nhấn **Save**.
4. Chờ khoảng 1-2 phút, GitHub sẽ cung cấp cho bạn một đường link trang web (ví dụ: `https://username.github.io/repo-name/`).
5. Gửi link này cho học viên.

## Lưu ý vận hành

- Hệ thống chỉ cho phép điểm danh từ **19:00 đến 21:30** vào các ngày học quy định.
- Nếu muốn test thử ngoài giờ:
  - Sửa giờ trên máy tính? Không được, vì giờ lấy từ server Google.
  - Sửa code Apps Script: Tìm đoạn `if (timeString < "19:00")` và comment lại hoặc sửa giờ để test.
  - Sửa ngày trong biến `SESSIONS` thành ngày hôm nay để test logic nhận diện buổi học.
