# PHẦN A

## A1 - 3 cách nhúng CSS

### Inline CSS
<p style="color:red">Text</p>

- Ưu điểm: áp dụng trực tiếp, specificity cao
- Nhược điểm: khó bảo trì, không tái sử dụng
- Dùng khi: test nhanh, override tạm thời

---

### Internal CSS
<style>
p { color: red; }
</style>

- Ưu điểm: gọn trong 1 file HTML
- Nhược điểm: không tái sử dụng nhiều trang
- Dùng khi: demo, bài nhỏ

---

### External CSS
<link rel="stylesheet" href="style.css">

- Ưu điểm: tái sử dụng, tách biệt cấu trúc và style
- Nhược điểm: cần load file riêng
- Dùng khi: project thực tế

---

### Thứ tự ưu tiên (Cascade)

Inline > Internal / External

Giải thích:
- Inline có specificity cao nhất
- Internal và External phụ thuộc:
  + specificity
  + thứ tự xuất hiện (rule viết sau thắng nếu cùng độ ưu tiên)

---

## A2 - Selectors

1. h1 → "ShopTLU"  
2. .price → "25.990.000đ", "45.990.000đ"  
3. #app header → toàn bộ thẻ `<header>`  
4. nav a:first-child → "Home"  
5. .product.featured h2 → "MacBook Pro"  
6. article > p → tất cả `<p>` là con trực tiếp của `<article>` (gồm giá + mô tả)  
7. a[href="/"] → "Home"  
8. .top-bar.dark h1 → "ShopTLU"  

---

## A3 - Box Model

### Trường hợp 1: content-box
width = 400px  
padding = 20px × 2 = 40px  
border = 5px × 2 = 10px  

→ Chiều rộng hiển thị = 400 + 40 + 10 = **450px**  
→ Không gian chiếm (có margin) = 450 + 20 = **470px**

---

### Trường hợp 2: border-box
width = 400px (bao gồm padding + border)

→ Content thực = 400 - 40 - 10 = **350px**  
→ Chiều rộng hiển thị = **400px**  
→ Không gian chiếm = 400 + 20 = **420px**

---

### Margin Collapse
margin-bottom: 25px  
margin-top: 40px  

→ Khoảng cách thực tế = **40px**

Giải thích:
- Margin dọc không cộng
- Trình duyệt lấy giá trị lớn nhất

---

### Nâng cao
margin-bottom: -10px  
margin-top: 40px  

→ Khoảng cách = **30px**

---

## A4 - Specificity

- p → (0,0,1)  
- .price → (0,1,0)  
- #main-price → (1,0,0)  
- p.price → (0,1,1)  

---

### Kết quả màu
→ **RED**

Giải thích:
- ID selector có độ ưu tiên cao nhất

---

### Nếu có inline style
style="color: orange"

→ **ORANGE**

---

### Nếu có !important
p { color: black !important; }

→ **BLACK**

Giải thích:
- !important override mọi rule khác (trừ inline !important)