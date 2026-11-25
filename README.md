# Kim Anh – web bán túi (GitHub Pages + Google Sheet)

Cấu trúc: trang web nằm trên GitHub, dữ liệu (sản phẩm, đơn hàng) vẫn nằm trong Google Sheet qua Apps Script.

## Bước 1 – Apps Script (một lần)
1. Mở Google Sheet cũ > Extensions > Apps Script.
2. Dán toàn bộ nội dung `Code.gs` mới đè lên file Code cũ. Lưu.
3. Deploy > New deployment > loại **Web app**: Execute as **Me**, Who has access **Anyone**. Bấm Deploy, cho phép quyền.
4. Chép đường dẫn Web app (kết thúc bằng `/exec`).
5. Mỗi lần sửa Code.gs sau này: Deploy > Manage deployments > Edit > New version.
(File Index/Admin cũ trong Apps Script không còn cần, có thể để nguyên.)

## Bước 2 – config.js
Mở `config.js`, thay `API_URL` bằng đường dẫn `/exec` vừa chép.

## Bước 3 – GitHub
1. Tạo repo mới (Public).
2. Upload: `index.html`, `admin.html`, `config.js`, thư mục `images/` (Add file > Upload files, kéo cả thư mục).
3. Settings > Pages > Deploy from a branch > `main` / root > Save.
4. Web khách: `https://TEN.github.io/REPO/`  ·  Quản trị: `.../admin.html`

## Ảnh sản phẩm
- Để trống cột `img` trong sheet Products: web tự dùng `images/<id>.jpg` (p01.jpg ... p16.jpg đã có sẵn).
- Hoặc ghi tên file (vd `p03.jpg`), link http, hoặc ID file Drive như trước.
- Ảnh mới: tải vào thư mục `images/` rồi ghi tên file vào cột `img`.

## Khác biệt so với bản cũ
- Giỏ hàng và Đơn đã đặt là 2 tab riêng trong ngăn kéo; giỏ hàng chia 3 khối: sản phẩm, thông tin nhận hàng, xác nhận.
- Đơn đã đặt được lưu trên máy khách (có thể cập nhật trạng thái, nhắn Zalo, tra cứu thêm).
- Chống tạo đơn trùng khi mất mạng.
- Mã admin vẫn đặt ở Apps Script: Project Settings > Script properties > ADMIN_KEY.
