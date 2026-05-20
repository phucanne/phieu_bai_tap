📋 PHIẾU BÀI TẬP 05
CSS RESPONSIVE & SCSS
PHẦN A — KIỂM TRA ĐỌC HIỂU (20đ)
Câu A1 — Viewport & Mobile-First (5đ)
1. Thẻ viewport chuẩn
<meta name="viewport" content="width=device-width, initial-scale=1.0">

Giải thích:

width=device-width: lấy đúng chiều rộng thiết bị → không bị scale 980px giả lập desktop
initial-scale=1.0: mức zoom mặc định 100%
2. Nếu thiếu viewport
Trang web bị render theo layout desktop (khoảng 980px)
Bị thu nhỏ toàn bộ trên điện thoại
Chữ nhỏ, khó đọc, phải zoom thủ công
3. Mobile-First vs Desktop-First
📱 Mobile-First
.container { font-size: 14px; }

@media (min-width: 768px) {
  .container { font-size: 16px; }
}
🖥 Desktop-First
.container { font-size: 16px; }

@media (max-width: 768px) {
  .container { font-size: 14px; }
}

Vì sao Mobile-First tốt hơn:

Ưu tiên thiết bị phổ biến (mobile)
Dễ mở rộng lên desktop
CSS nhẹ hơn (progressive enhancement)
Câu A2 — Breakpoints (5đ)
Breakpoint	Pixel	Thiết bị	Grid sản phẩm
xs	<576px	điện thoại nhỏ	1 cột
sm	≥576px	điện thoại lớn	1–2 cột
md	≥768px	tablet	2 cột
lg	≥992px	laptop	3–4 cột
xl	≥1200px	desktop lớn	4–6 cột
Câu A3 — Media Queries (5đ)
Màn hình	.container width
375px	100%
600px	540px
800px	720px
1000px	960px
1400px	1140px
Câu A4 — SCSS Basics (5đ)
1. Variables
$primary-color: #ff4d4f;
2. Nesting
.card {
  .title { font-size: 18px; }
}
3. Mixin
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
4. Extend
.btn {
  padding: 10px;
}

.btn-primary {
  @extend .btn;
  background: blue;
}
❓ Vì sao SCSS không chạy trực tiếp?

Browser chỉ hiểu CSS → SCSS cần compile:

sass style.scss style.css
PHẦN B — THỰC HÀNH CODE
B1 — Responsive Product Page (25đ)
Yêu cầu:
Mobile-first
3 breakpoint: 768px, 1024px
8 product cards
Sidebar + grid + header responsive
B2 — Animations (15đ)
5 hiệu ứng:
/* 1. Card hover */
.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.2);
  transition: 0.3s;
}

/* 2. Button hover */
button:hover {
  transform: scale(1.05);
  transition: 0.3s;
}

/* 3. Image zoom */
.card img:hover {
  transform: scale(1.1);
}

/* 4. Spinner */
@keyframes spin {
  from { transform: rotate(0); }
  to { transform: rotate(360deg); }
}

/* 5. Fade-in */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
B3 — SCSS Refactor (20đ)
Variables
$primary: #ff4d4f;
$secondary: #333;
$font: 'Arial';
$tablet: 768px;
$desktop: 1024px;
$sm: 8px;
$md: 16px;
$lg: 32px;
Nesting
.card {
  .title {}
  .image {}

  &:hover {}
  &.active {}
}
Mixins
@mixin flex-center {
  display:flex;
  justify-content:center;
  align-items:center;
}

@mixin shadow {
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

@mixin responsive($size) {
  @media (min-width: $size) {
    @content;
  }
}
Compile SCSS
npx sass scss/style.scss scss/dist/style.css
PHẦN C — PHÂN TÍCH
C1 — Phân tích website (Shopee)
Navigation:
Mobile: hamburger menu
Tablet: menu rút gọn
Desktop: full menu ngang
Grid:
Mobile: 1 cột
Tablet: 2–3 cột
Desktop: 4–6 cột
Ẩn trên mobile:
Sidebar filter
Banner phụ
Text dài
Media queries:
@media (min-width: 768px) {}
@media (min-width: 1024px) {}
C2 — Responsive Strategy (Nhà hàng)
Mobile:
1 cột
Form full width
Map dưới cùng
Tablet:
Grid 2–3 cột
Form giữa trang
Desktop:
2 layout:
Content trái
Map/sidebar phải
CSS skeleton:
.container { display: grid; grid-template-columns: 1fr; }

@media (min-width: 768px) {
  .grid { grid-template-columns: repeat(2,1fr); }
}

@media (min-width: 1024px) {
  .layout { grid-template-columns: 2fr 1fr; }
}