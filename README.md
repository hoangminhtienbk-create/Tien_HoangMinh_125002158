# ⚡ MangaRealm — Web Đọc Truyện Tranh Kỹ Thuật Số

> **Bài tập lớn giữa kỳ — Môn Thiết Kế Web**
> Sinh viên: **Hoàng Minh Tiến** | MSSV: **125002158**

---

## 📖 Giới thiệu dự án

**MangaRealm** là trang chủ của một nền tảng đọc truyện tranh kỹ thuật số, được xây dựng hoàn toàn bằng **HTML5 thuần ngữ nghĩa (Semantic HTML5)** và **CSS3 hiện đại** theo phương pháp *Vibe Coding* có sự hỗ trợ của công cụ AI. Dự án hướng đến giao diện Dark Mode cao cấp, responsive đa thiết bị và trải nghiệm người dùng mượt mà thông qua các hiệu ứng chuyển động.

---

## 🌐 Demo trực tuyến

🔗 [https://hoangminhtienbk-create.github.io/Tien_HoangMinh_125002158](https://hoangminhtienbk-create.github.io/Tien_HoangMinh_125002158)

---

## 🗂️ Cấu trúc thư mục

```
Tien_HoangMinh_125002158/
├── index.html          # Trang chủ chính (Semantic HTML5)
├── style.css           # Toàn bộ thiết kế giao diện (CSS3 + Variables)
├── assets/             # Thư mục hình ảnh & tài nguyên tĩnh
├── PROMPT_LOG.md       # Nhật ký quá trình Vibe Coding với AI
└── README.md           # Tài liệu mô tả dự án (file này)
```

---

## ✨ Tính năng nổi bật

| Tính năng | Mô tả |
|---|---|
| 🌙 **Dark Mode** | Giao diện tối mặc định, bảo vệ mắt người đọc |
| 🎞️ **Preloader** | Màn hình chờ xoay mượt mà, thuần HTML & CSS (`@keyframes`) |
| 🎨 **Animate.css** | Tiêu đề hero xuất hiện với `fadeInDown`, nút CTA nhấp nháy `pulse` |
| 📜 **AOS Library** | Các card truyện trượt lên đẹp mắt khi cuộn trang (`fade-up`) |
| 🔍 **Search Box** | Thanh tìm kiếm tích hợp trong header, hiệu ứng `:focus` nổi bật |
| 📚 **Grid Card** | 6 card truyện dạng CSS Grid, hover phóng to ảnh bìa |
| 🏷️ **Badges** | Nhãn trạng thái HOT / FULL nổi trên ảnh bìa |
| 🗂️ **Genres Section** | 8 thể loại truyện dạng lưới linh hoạt với hover đổi màu |
| ❓ **FAQ Section** | Câu hỏi thường gặp dùng thẻ `<details>` & `<summary>` thuần HTML5 |
| 📩 **Support Form** | Form gửi yêu cầu hỗ trợ đầy đủ trường nhập liệu chuẩn a11y |
| ⬆️ **Back to Top** | Nút quay về đầu trang cố định góc dưới phải, scroll smooth |
| 📱 **Responsive** | Tương thích đầy đủ Desktop, Tablet & Mobile |

---

## 🛠️ Công nghệ sử dụng

- **HTML5** — Semantic Tags: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<details>`, `<summary>`
- **CSS3** — CSS Variables (`:root`), Flexbox, CSS Grid, `@keyframes`, Media Queries
- **[Animate.css v4.1.1](https://animate.style/)** — Hiệu ứng xuất hiện trang (CDN)
- **[AOS v2.3.4](https://michalsnik.github.io/aos/)** — Animate On Scroll (CDN)
- **[Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans)** — Font chữ hiện đại (Google Fonts)

---

## 🎨 Hệ thống màu sắc (CSS Variables)

```css
:root {
  --primary-color: #ff4757;   /* Màu chủ đạo — Đỏ pha cam */
  --bg-color:      #0f1117;   /* Màu nền tối */
  --text-color:    #f1f2f6;   /* Màu chữ sáng */
  --font-family:   'Plus Jakarta Sans', sans-serif;
}
```

---

## 🏗️ Bố cục trang (Layout)

```
┌─────────────────────────────────────────┐
│  HEADER: Logo | Search Box | Nav | Login│
├─────────────────────────────────────────┤
│  HERO BANNER: Truyện nổi bật tuần này  │
├─────────────────────────────────────────┤
│  GENRES: 8 thể loại truyện (Grid)       │
├─────────────────────────────────────────┤
│  COMIC GRID: 6 card truyện mới nhất    │
├─────────────────────────────────────────┤
│  SUPPORT: FAQ (details/summary) + Form  │
├─────────────────────────────────────────┤
│  FOOTER: Giới thiệu | Links | Pháp lý  │
└─────────────────────────────────────────┘
                              ⬆️ Back to Top
```

---

## 🚀 Hướng dẫn chạy dự án

Dự án **không cần cài đặt** bất kỳ thư viện hay công cụ nào. Chỉ cần:

1. **Clone hoặc tải về** repository:
   ```bash
   git clone https://github.com/hoangminhtienbk-create/Tien_HoangMinh_125002158.git
   ```

2. **Mở file** `index.html` bằng trình duyệt web bất kỳ (Chrome, Firefox, Edge...).

3. ✅ Trang web hoạt động ngay lập tức — không cần server hay build.

---

## 📝 Nhật ký Vibe Coding (Prompt Engineering)

Toàn bộ quá trình tạo ra dự án bằng AI được ghi chép chi tiết trong file [`PROMPT_LOG.md`](./PROMPT_LOG.md), bao gồm:

- **6 lần lặp (Iteration)** từ khung cơ bản đến hoàn thiện
- Các **prompt đã dùng** cho từng tính năng
- **Thách thức gặp phải** và cách debug / sửa lỗi
- **Bài học rút ra** về kỹ thuật prompt engineering

---

## 📋 Thông tin sinh viên

| Thông tin | Chi tiết |
|---|---|
| **Họ và tên** | Hoàng Minh Tiến |
| **MSSV** | 125002158 |
| **Môn học** | Thiết Kế Web |
| **Công cụ AI** | Gemini / Antigravity AI Assistant |
| **GitHub** | [hoangminhtienbk-create](https://github.com/hoangminhtienbk-create) |

---

<p align="center">
  <strong>© 2026 MangaRealm</strong> — Bài tập lớn giữa kỳ Thiết Kế Web
</p>