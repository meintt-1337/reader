# 📖 Góc đọc sách

Trình đọc EPUB chạy hoàn toàn trên trình duyệt, chỉ gồm **một file HTML duy nhất**. Không cần cài đặt, không cần server, không tải sách lên đâu cả.

🔗 **Dùng thử:** https://meintt-1337.github.io/reader/

## Tính năng

- **Mở sách:** chọn file `.epub` hoặc kéo thả vào trang.
- **Hai chế độ đọc:** Cuộn liên tục hoặc Lật trang (hiện 2 trang trên màn hình rộng).
- **Mục lục:** hiển thị theo cấu trúc chương/mục của sách, bấm để nhảy tới.
- **Tìm trong sách:** hỗ trợ gõ **không dấu** (`bao hiem` sẽ ra `bảo hiểm`), bấm kết quả để nhảy đúng chỗ và tô sáng.
- **Thanh tiến độ:** hiển thị `Chương x/xx · xx% · tên mục`.
- **Giao diện:** nền Tự động / Sáng / Vàng / Tối; chữ Có chân (Literata) hoặc Không chân.
- **Tùy chỉnh:** cỡ chữ và độ rộng khối chữ (100% là mặc định), căn đều hai bên.
- **Tự nhớ:** vị trí đang đọc của từng sách và các cài đặt giao diện (lưu trong `localStorage` của trình duyệt).

## Cách dùng

1. Mở trang, bấm biểu tượng thư mục (hoặc kéo file `.epub` vào).
2. Dùng các nút trên thanh đầu: Mục lục, Mở sách, Tìm kiếm, Giao diện.
3. Chuyển trang bằng nút **‹ Trước / Sau ›** hoặc phím tắt.

### Phím tắt

| Phím | Chức năng |
|------|-----------|
| `←` / `→` | Trang hoặc phần trước / sau |
| `T` | Mở / đóng Mục lục |
| `S` | Mở / đóng Giao diện |
| `/` | Mở ô Tìm kiếm |
| `Esc` | Đóng các bảng đang mở |

## Chạy tại máy

Chỉ cần tải file `index.html` về và mở bằng trình duyệt. Cần có mạng để tải font Literata từ Google Fonts (không có mạng sẽ tự dùng Noto Serif).

## Triển khai

Đặt file `index.html` lên bất kỳ dịch vụ host tĩnh nào (GitHub Pages, Netlify, Cloudflare Pages, Vercel…).

## Bảo mật

- Sách được hiển thị trong iframe **sandbox**, script bên trong EPUB không thể chạy.
- Có **Content-Security-Policy** chặn sách tải ảnh/font/CSS từ internet hoặc gọi ra ngoài.
- Kiểm tra định dạng và giới hạn dung lượng file (tối đa 150 MB) trước khi mở.
- Mọi xử lý diễn ra tại máy người dùng, không có dữ liệu nào được gửi đi.
- Khi deploy trên Netlify / Cloudflare Pages / Vercel, nên thêm header bảo mật (`frame-ancestors`, `X-Content-Type-Options`, …).

## Hạn chế đã biết

- Chỉ hỗ trợ EPUB **không bị khóa DRM**.
- Khi đổi cỡ chữ hoặc độ rộng khối chữ, trang có thể nháy nhẹ do dàn lại.
- Tìm kiếm không khớp được cụm từ bị cắt ngang bởi thẻ định dạng (ví dụ nửa chữ thường, nửa chữ nghiêng).

## Công nghệ

- [epub.js](https://github.com/futurepress/epub.js) – đọc và hiển thị EPUB
- [JSZip](https://stuk.github.io/jszip/) – giải nén EPUB
- [Literata](https://fonts.google.com/specimen/Literata) – font đọc chính
- HTML, CSS, JavaScript thuần, không framework

## Giấy phép

Tự chọn giấy phép phù hợp (ví dụ MIT). Lưu ý epub.js (BSD-2-Clause) và JSZip (MIT hoặc GPLv3) có điều khoản riêng.