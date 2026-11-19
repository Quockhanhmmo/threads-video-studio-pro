# Threads Video Studio PRO — Mobile Web MVP

Phiên bản khởi đầu chạy trực tiếp trong trình duyệt Android/PC, không cần cài Python. Đây là MVP client-side, chưa phải hệ thống SaaS có backend.

## Chạy thử
- Mở `index.html` bằng Chrome để xem giao diện và thử một số chức năng.
- Để PWA/offline hoạt động, cần chạy qua HTTPS hoặc localhost. Có thể deploy miễn phí lên GitHub Pages, Cloudflare Pages hoặc Netlify bằng cách tải toàn bộ thư mục này lên.
- Trên Android: mở URL HTTPS bằng Chrome → menu ⋮ → **Thêm vào màn hình chính / Install app**.

## Chức năng hiện có
- Nhập/chỉnh sửa/làm sạch văn bản.
- Mở link Threads công khai (không tự scrape hoặc vượt hạn chế).
- Tải video nền và file âm thanh từ điện thoại.
- Xem trước video nền.
- Chọn tỷ lệ 9:16, 1:1, 16:9; 720p/1080p.
- Đọc thử bằng giọng tiếng Việt có sẵn của trình duyệt (phụ thuộc thiết bị).
- Render video bằng Canvas + MediaRecorder, xuất WebM.
- PWA manifest và service worker cơ bản.

## Giới hạn MVP — cần nói rõ
- Không thể tự lấy nội dung Threads ổn định chỉ từ URL do giới hạn truy cập/CORS và thay đổi nền tảng; người dùng có thể dán văn bản.
- Giọng đọc thử của trình duyệt không được ghi vào file video. Để có giọng đọc nằm trong video, hãy tải file giọng đọc/âm thanh lên ô **Nhạc / giọng đọc**.
- Bản xuất hiện tại là WebM, không phải MP4. Chuyển MP4 cần bộ chuyển mã server-side hoặc FFmpeg.wasm; FFmpeg.wasm khá nặng với điện thoại.
- Render dựa trên MediaRecorder; khả năng 1080p, codec và thời lượng phụ thuộc trình duyệt/thiết bị. Giữ tab mở trong lúc render.
- Chưa có đăng nhập, lưu dự án cloud, hàng đợi render hay backend.

## Lộ trình tiếp theo
1. Backend FastAPI + FFmpeg để xuất MP4/H.264.
2. TTS server-side (Edge TTS/FPT.AI/nhà cung cấp có key).
3. Hàng đợi render và cập nhật tiến trình.
4. Lưu dự án/tài nguyên có xác thực.
5. Kiểm tra quyền sử dụng nội dung, video và nhạc trước khi xuất bản.

## Triển khai miễn phí
GitHub Pages / Cloudflare Pages / Netlify có thể host phần frontend tĩnh miễn phí theo điều kiện gói dịch vụ. Các nền tảng này không cung cấp backend render video cho bản này. Không đặt API key bí mật trong frontend.
