# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Hoàng Minh Tiến
- **MSSV:** 125002158
- **Tên đề tài Website:** MangaRealm - Website Đọc Truyện Tranh Kỹ Thuật Số (Trang Chủ)
- **Công cụ AI đã sử dụng:** Gemini / Antigravity AI Assistant

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> *Ghi lại prompt tổng quan ban đầu bạn dùng để khởi tạo khung website.*

```text
Đóng vai lập trình viên frontend, hãy viết cho tôi mã nguồn HTML5 và CSS cơ bản cho một trang web đọc truyện (Trang chủ). Yêu cầu kỹ thuật bắt buộc:
1. Sử dụng chuẩn Semantic HTML5: <header>, <nav>, <main>, <section>, <article>, <footer>.
2. Trong CSS, bắt buộc khai báo :root chứa các CSS Variables cho màu chủ đạo (--primary-color), màu nền (--bg-color), màu chữ (--text-color) và font chữ.
3. Giao diện gồm: Header (logo + menu tìm kiếm/thể loại), Main (phần banner nổi bật và danh sách card truyện dạng lưới Grid), Footer.
Hãy xuất ra 2 file riêng biệt: index.html và style.css (có chú thích rõ ràng).
```

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML5 & CSS Variables
- **Prompt đã dùng:** Prompt khởi tạo ban đầu ở Mục 1.
- **Kết quả AI tạo ra:**
  - AI sinh ra hai tệp `index.html` và `style.css` với cấu trúc Dark Mode hiện đại.
  - Sử dụng đầy đủ các thẻ ngữ nghĩa: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`.
  - Khai báo đầy đủ `:root` với các biến: `--primary-color: #ff4757`, `--bg-color: #0f1117`, `--text-color: #f1f2f6`, `--font-family: 'Plus Jakarta Sans', ...`.
- **Nhận xét & Tinh chỉnh của SV:**
  - Cấu trúc ban đầu khá chuẩn, phân vùng nội dung rõ nét.
  - Tuy nhiên, khung tìm kiếm ban đầu được AI bọc trong `<form class="search-form">`, các thẻ truyện dùng class `.comic-card` thay vì `.story-card`, và chưa có các thành phần tương tác nâng cao như màn hình chờ, hiệu ứng cuộn trang.

---

### Lần 2: Bổ sung Màn hình chờ (Preloader) thuần HTML & CSS
- **Prompt đã dùng:**
  > *"Hãy bổ sung phần màn hình chờ (Preloader/Loading screen) vào file index.html và style.css hiện tại cho trang web đọc truyện của tôi. Yêu cầu kỹ thuật: Chỉ dùng HTML và CSS thuần (sử dụng CSS @keyframes animation, tuyệt đối không dùng JavaScript hoặc thư viện bên ngoài). Cấu trúc HTML: Thêm một thẻ `<div id="preloader">` nằm ngay sau thẻ `<body>`, bên trong chứa vòng xoay loading `<div class="spinner"></div>`. CSS styling: `#preloader` che kín toàn bộ màn hình, có màu nền trùng với `--bg-color`. `.spinner` tạo hình tròn xoay mượt mà sử dụng border, border-top-color: var(--primary-color) và @keyframes spin. Sử dụng CSS animation: fadeOut ... forwards kết hợp animation-delay để màn hình loading tự mờ dần và ẩn đi (pointer-events: none; opacity: 0;)."*
- **Kết quả AI tạo ra:**
  - Thêm thẻ `<div id="preloader"><div class="spinner"></div></div>` ngay sau thẻ `<body>`.
  - CSS tạo `@keyframes spin` và `@keyframes fadeOut` với `animation: fadeOut 0.6s ease 1.5s forwards`.
- **Thách thức gặp phải:**
  - Sau khi màn hình chờ mờ dần (`opacity: 0`), nếu không xử lý cẩn thận thuộc tính `pointer-events: none` và `visibility: hidden`, lớp phủ vô hình sẽ tiếp tục chặn chuột của người dùng, khiến không thể nhấp vào menu hay card truyện.
- **Cách sửa prompt (Debug prompt):**
  - Đã chỉ đạo AI bắt buộc thêm `pointer-events: none; visibility: hidden;` ở mốc `100%` của `@keyframes fadeOut` và sử dụng `forwards` để giữ nguyên trạng thái kết thúc này.

---

### Lần 3: Tích hợp thư viện Animate.css & AOS (Animate On Scroll)
- **Prompt đã dùng:**
  > *"Hãy cập nhật file index.html và style.css để tích hợp hiệu ứng chuyển động chuyên nghiệp:
  > 1. Nhúng thư viện Animate.css và AOS (Animate On Scroll) qua CDN mới nhất.
  > 2. Áp dụng Animate.css: tiêu đề Hero section có hiệu ứng xuất hiện nhẹ nhàng (animate__fadeInDown), nút CTA có hiệu ứng chú ý (animate__pulse).
  > 3. Áp dụng AOS: các card truyện trong danh sách cuộn trang sẽ xuất hiện so le (data-aos="fade-up", data-aos-delay="...").
  > 4. Khởi tạo script AOS.init() với cấu hình mượt mà (once: true, duration: 800).
  > 5. Bổ sung hiệu ứng CSS thuần :hover và :focus rõ nét cho nút bấm, thanh tìm kiếm và thẻ card truyện."*
- **Kết quả AI tạo ra:**
  - Nhúng CDN của Animate.css v4.1.1 và AOS v2.3.4 vào thẻ `<head>` và script khởi tạo `AOS.init()` trước `</body>`.
  - Tiêu đề Hero gắn class `animate__animated animate__fadeInDown`.
  - Nút CTA gắn class `animate__animated animate__pulse animate__infinite`.
  - 6 thẻ truyện gắn `data-aos="fade-up"` với `data-aos-delay` so le từ 100ms đến 600ms.
- **Thách thức gặp phải:**
  - Quá trình AI viết lại đoạn thẻ card 6 bị lặp lại một khối thẻ HTML dư thừa ở cuối section.
- **Cách sửa prompt (Debug prompt):**
  - Yêu cầu AI kiểm tra lại cú pháp thẻ mở/đóng, loại bỏ thẻ trùng lặp để đảm bảo tính hợp lệ W3C của Semantic HTML5.

---

### Lần 4: Chuẩn hóa theo Thang điểm thi (Search Box, Back-To-Top, Story Card & Badges)
- **Prompt đã dùng:**
  > *"Hãy giúp tôi hoàn thiện mã nguồn index.html và style.css hiện có bằng cách bổ sung thêm các thành phần còn thiếu sau đây để đạt điểm tối đa theo thang điểm:
  > - Header & Thanh tìm kiếm: Thêm một ô tìm kiếm `<div class="search-box">` nằm trong `<header>` bao gồm `<input type="text" placeholder="Tìm kiếm truyện, tác giả...">` và một nút tìm kiếm. Viết CSS có hiệu ứng :focus đổi màu viền theo --primary-color và :hover mượt mà.
  > - Nút Quay về đầu trang: Thêm `<button id="backToTop" class="back-to-top">⬆</button>` ở cuối trang. CSS cố định góc dưới bên phải (position: fixed; bottom: 20px; right: 20px; z-index: 1000;), hover scale(1.1) và thêm scroll-behavior: smooth vào selector html.
  > - Thẻ truyện & Nhãn trạng thái: Trên mỗi `<article class="story-card">`, thêm nhãn trạng thái góc bìa truyện (<span class="badge badge-hot">HOT</span> hoặc <span class="badge badge-full">FULL</span>). Hover vào .story-card sẽ đổ bóng đậm hơn (box-shadow), bìa truyện (img) phóng to nhẹ (transform: scale(1.05)) với overflow: hidden.
  > - Tối ưu Responsive & Chuẩn Semantic HTML5: Sử dụng đúng ngữ nghĩa các thẻ, tối ưu Grid/Flexbox trên Mobile và Desktop."*
- **Kết quả AI tạo ra:**
  - Đồng bộ chuẩn hóa class `.search-box`, `.story-card`, `.back-to-top`.
  - Thêm đầy đủ nhãn `HOT` và `FULL` nổi bật trên từng ảnh bìa truyện.
### Lần 5: Bổ sung Trung tâm Hỗ Trợ Người Dùng & Hỏi Đáp (FAQ & Support)
- **Prompt đã dùng:**
  > *"Tôi muốn bổ sung một phần Hỗ Trợ Người Dùng & Câu Hỏi Thường Gặp (FAQ / Support) cho website đọc truyện của tôi. Hãy viết mã nguồn cho phần này với các yêu cầu kỹ thuật sau:
  > - Cấu trúc Semantic HTML5: Tạo `<section class="support-section" id="support">` gồm 2 khối: Khối FAQ dùng <details> và <summary> và Khối Form Gửi Yêu Cầu Hỗ Trợ (Họ tên, Email, Loại sự cố, Nội dung, Nút gửi).
  > - Kỹ thuật CSS & CSS Variables: Sử dụng lại biến :root, layout 2 cột cân đối bằng Grid/Flexbox, hiệu ứng :hover và :focus rõ nét.
  > - Thư viện hiệu ứng: Tích hợp data-aos="fade-up" mượt mà khi cuộn tới."*
- **Kết quả AI tạo ra:**
  - Tạo cấu trúc semantic chuẩn xác: `<section class="support-section" id="support" data-aos="fade-up">` gồm 2 khối `.faq-col` và `.form-col`.
  - Khối FAQ ứng dụng thẻ `<details>` và `<summary>` chuẩn HTML5, đóng/mở mượt mà không cần dùng đến JavaScript.
  - Khối Form hỗ trợ đầy đủ các trường nhập liệu chuẩn a11y, hiệu ứng focus ring tỏa sáng màu `--primary-color`.
- **Nhận xét & Tinh chỉnh của SV:**
  - Bổ sung thêm liên kết `Hỗ Trợ` vào thanh điều hướng `<nav>` trên Header và Footer để người dùng có thể nhấp chuột nhảy nhanh đến phần hỗ trợ.
  - Tối ưu thêm `@media (max-width: 576px)` để co giãn hợp lý các ô nhập liệu và khoảng cách trên màn hình điện thoại di động.

### Lần 6: Bổ sung Danh mục Thể loại Truyện (Genres Section)
- **Prompt đã dùng:**
  > *"Hãy viết mã nguồn bổ sung phần Danh mục Thể loại Truyện vào trang web với các yêu cầu sau:
  > - Cấu trúc Semantic HTML5: Tạo `<section class="genres-section" id="genres">` chứa tiêu đề và danh sách 8 thẻ thể loại: Tiên Hiệp, Huyền Huyễn, Đô Thị, Khoa Huyễn, Ngôn Tình, Cổ Đại, Mạt Thế, Hệ Thống kèm icon và số lượng truyện.
  > - Kỹ thuật CSS & Biến hệ thống: Tái sử dụng biến :root, dùng CSS Grid/Flexbox tự co giãn linh hoạt.
  > - Tương tác & Hiệu ứng: Hiệu ứng :hover và :focus đổi màu nền sang --primary-color, chữ trắng, transform translateY(-3px) mượt mà 0.3s. Tích hợp data-aos="fade-up"."*
- **Kết quả AI tạo ra:**
  - Tạo cấu trúc `<section class="genres-section" id="genres" data-aos="fade-up">` gồm 8 thẻ `.genre-card` với đầy đủ icon emoji, tên thể loại và số lượng truyện.
  - CSS Grid `grid-template-columns: repeat(auto-fill, minmax(135px, 1fr))` tự động căn chỉnh hoàn hảo.
  - Hiệu ứng `:hover` và `:focus` đổi màu nền sang `--primary-color`, chữ chuyển sang trắng và nhấc nhẹ lên 3px với bóng đổ rực rỡ.
- **Nhận xét & Tinh chỉnh của SV:**
  - Bổ sung `id="genres"` để liên kết trực tiếp với mục "Thể Loại ▾" trên thanh menu header.
  - Bổ sung responsive 2 cột gọn gàng trên màn hình điện thoại di động (`@media (max-width: 576px)`).

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

### AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?
- **Khởi tạo mã nguồn nền tảng (Boilerplate):** Tiết kiệm đến 80% thời gian gõ cú pháp Semantic HTML5, cấu trúc reset CSS và thiết lập bảng mã màu `:root` Variables.
- **Tích hợp các thư viện hiệu ứng (Animate.css & AOS):** AI nhanh chóng tìm đúng CDN phiên bản ổn định nhất và thiết lập sẵn các thuộc tính `data-aos`, `data-aos-delay` cho từng card một cách chuẩn xác.
- **Tối ưu CSS Responsive:** AI viết sẵn các điểm ngắt (breakpoints: 992px, 768px, 576px) với CSS Grid và Flexbox, giúp website hiển thị mượt mà trên cả desktop lẫn điện thoại.

### Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?
1. **Chia nhỏ yêu cầu (Step-by-Step / Iterative Prompting):** Không nên đưa toàn bộ mọi yêu cầu phức tạp vào một prompt duy nhất. Thay vào đó, hãy làm từ khung HTML cơ bản -> CSS giao diện -> Hiệu ứng thư viện -> Tinh chỉnh chi tiết và Responsive.
2. **Quy định rõ ràng class name và selector:** Khi có yêu cầu chấm điểm cụ thể (như `.story-card`, `.search-box`, `#backToTop`), cần đưa chính xác tên class vào prompt để AI không tự đặt tên ngẫu nhiên.
3. **Luôn kiểm tra mã nguồn (Code Review & Debugging):** AI có thể tạo ra mã thừa hoặc thiếu thuộc tính quan trọng (như `pointer-events: none` trên màn hình loading, hoặc thẻ lặp). Lập trình viên phải hiểu bản chất kỹ thuật để kịp thời phát hiện và chỉ đạo AI sửa lỗi.
