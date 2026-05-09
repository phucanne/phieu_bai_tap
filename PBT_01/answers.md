# PHẦN A — KIỂM TRA ĐỌC HIỂU

## A1 — HTTP & Browser

### Nguồn: 01_introduction_html_universe.md

1. Thứ tự xảy ra khi truy cập https://shopee.vn:
- DNS lookup: phân giải domain → IP server
- TCP handshake: thiết lập kết nối
- TLS handshake: mã hóa HTTPS
- HTTP request: browser gửi request
- Server response: trả về HTML
- Browser parse HTML → DOM tree
- Load CSS/JS → render tree
- Layout → Paint → Composite

2. Tab Network hiển thị:
- Danh sách request (HTML, CSS, JS, API)
- Status code (200, 404, 301…)
- Thời gian tải từng request (Waterfall)
- Tổng thời gian load page
- Size dữ liệu tải về

---

## A2 — Semantic HTML

### Nguồn: chương 04 semantic HTML

### Lỗi semantic:
1. Dùng `<div>` thay cho `<header>`, `<nav>`
2. Không có `<main>`
3. Sản phẩm không dùng `<article>`
4. Thiếu `<section>` rõ ràng
5. Logo/menu không semantic

### Sửa:
- header → `<header>`
- menu → `<nav>`
- product → `<article>`
- content chính → `<main>`

---

## A3 — Block vs Inline

### Hiển thị:

Hộp 1  
Text A Text B  
Hộp 2  
Text C Text D  
Hộp 3  

### Giải thích:
- `<div>` = block → xuống dòng
- `<span>`, `<strong>` = inline → nằm cùng dòng

---

## A4 — Table

### thead / tbody / tfoot:
- thead: tiêu đề bảng
- tbody: dữ liệu chính
- tfoot: tổng kết

### Không dùng table để layout vì:
1. Không responsive tốt
2. Khó maintain
3. Không đúng semantic
4. SEO & accessibility kém

---

# PHẦN C — SUY LUẬN

## C1 — Cấu trúc trang sản phẩm

```html
<header>
  <nav>Navigation</nav>
</header>

<nav aria-label="breadcrumb">
  <ol>
    <li>Trang chủ</li>
    <li>Điện thoại</li>
    <li>iPhone 16</li>
  </ol>
</nav>

<main>
  <section class="gallery">
    <!-- 5 ảnh sản phẩm -->
  </section>

  <section class="info">
    <h1>Tên sản phẩm</h1>
    <p>Giá</p>
    <p>Rating</p>
  </section>

  <section class="spec">
    <table></table>
  </section>

  <section class="reviews">
    <!-- comment -->
  </section>
</main>

<aside>
  Sản phẩm tương tự
</aside>

<footer>Footer</footer>
Giải thích:
nav: điều hướng
ol: breadcrumb có thứ tự
article/section: phân vùng nội dung
aside: nội dung phụ
C2 — Phản biện

Semantic HTML không chỉ là “tùy chọn” mà là nền tảng quan trọng trong phát triển web hiện đại.

Thứ nhất, về SEO, các công cụ tìm kiếm như Google không đọc giao diện mà phân tích cấu trúc HTML. Khi sử dụng <header>, <main>, <article>, hệ thống hiểu rõ đâu là nội dung chính, đâu là nội dung phụ, từ đó cải thiện khả năng xếp hạng.

Thứ hai, về Accessibility, các công cụ hỗ trợ người khuyết tật (screen reader) dựa vào semantic tags để đọc nội dung đúng ngữ cảnh. Ví dụ <nav> giúp người dùng biết đây là khu vực điều hướng, thay vì phải đọc toàn bộ div vô nghĩa.

Ví dụ thực tế: một trang sản phẩm dùng <article> cho mỗi sản phẩm sẽ giúp Google hiểu mỗi sản phẩm là một thực thể độc lập, tăng khả năng hiển thị rich snippet.

Tuy nhiên, <div> vẫn phù hợp trong các trường hợp layout thuần túy như container, wrapper hoặc animation box, nơi không mang ý nghĩa nội dung.
    