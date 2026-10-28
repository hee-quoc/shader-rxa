# Disc Spine

Hệ generative 3D (Three.js r128): các lớp đĩa xếp theo khung xương, gradient halo kiểu cone-focal, màu chảy 0 → 1, upload khung SVG/JSON.

## Chạy thử trên máy
Mở thư mục này bằng một static server bất kỳ, ví dụ:

    npx serve .
    # hoặc
    python3 -m http.server 8080

Rồi vào http://localhost:8080 (mở trực tiếp file index.html bằng file:// cũng chạy được).

## Deploy lên Vercel
1. Đẩy thư mục này lên một repo GitHub.
2. Trên Vercel: New Project → chọn repo → Framework Preset: **Other**, Build Command để trống, Output Directory: `.`
3. Deploy. Không cần bước build nào khác.

Hoặc dùng CLI: `npx vercel --prod` ngay trong thư mục.

## Cấu trúc
- `index.html` — toàn bộ app (UI, shader, logic)
- `vendor/three.min.js` — Three.js r128, đóng gói sẵn để không phụ thuộc CDN
- Font tải từ Google Fonts; nếu offline sẽ dùng font hệ thống.
