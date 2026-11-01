# Disc Spine

Hệ generative 3D (Three.js r128): các lớp đĩa xếp dọc theo một khung xương, đổ màu bằng shader gradient, chảy liên tục theo thời gian. Toàn bộ app nằm trong một file `index.html`, không cần build.

## Chạy trên máy

Mở thư mục bằng một static server bất kỳ:

    npx serve .
    # hoặc
    python3 -m http.server 8080

Rồi vào http://localhost:8080 (mở thẳng `index.html` bằng file:// cũng chạy).

## Deploy

Repo đã nối với Vercel: push lên `main` là tự deploy. Cấu hình Vercel: Framework **Other**, Build Command để trống, Output Directory `.`.
Deploy tay: `npx vercel --prod` trong thư mục.

## Tính năng

- **Preset**: Rồng Vảy (mặc định), Rồng Bay, Rồng Cuộn, Vòng Cung, Quạt, Vảy, Xích Chroma, Rồng Nhiệt, Vòng Holo. Lưu preset riêng trên trình duyệt, dán / mở / tải settings dạng JSON.
- **Khung xương**: các khung có sẵn hoặc upload SVG / JSON.
  - SVG: lấy mọi nét theo đúng thứ tự và chiều vẽ, điểm đầu nét là đầu. Có nút đảo đầu ↔ đuôi, khép kín, làm mượt.
  - Độ sâu Z: theo độ cong (mỗi vòng trên hình vẽ nâng lên một nấc), sóng đều, hoặc giữ Z gốc của file JSON. Nhìn thẳng luôn giữ đúng nét gốc.
- **Lớp**: shape Tròn / Phiến / Vảy cá, số lớp, cỡ, thon dần, cỡ đầu / đuôi, shape mới ở đầu hiện dần (mượt, không giật), chống lồng vào nhau.
- **Kiểu đi màu**: Holo 3D, Sóng chảy, Đơn sắc blend, Cổ điển, Chroma Chain (gradient OKLab vòng lặp), Thermal (bản đồ nhiệt + blur + fringe). Màu lấy theo palette, sửa được từng màu.
- **Viền**: màu cố định hoặc chạy theo gradient.
- **Xuất**: PNG và video ở 2K (cạnh dài 2048px). Bật **Tách nền** để xuất PNG nền trong suốt; video khi tách nền lưu WebM VP9 có alpha (MP4 không chứa được alpha).
- Nếu trình duyệt không bật được WebGL, app hiện thông báo kèm cách khắc phục ngay trên khung hình.

## Cấu trúc

- `index.html`: toàn bộ app (UI, shader, logic).
- `vendor/three.min.js`: Three.js r128, đóng gói sẵn để không phụ thuộc CDN.
- `vercel.json`: clean URLs và cache cho `vendor/`.
- Font tải từ Google Fonts; offline thì dùng font hệ thống.
