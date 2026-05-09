 PHẦN A — KIỂM TRA ĐỌC HIỂU
 A1 — 10 Input Types trong HTML5
1. type="email"
→ UI: ô nhập text có kiểm tra định dạng email
→ Validation: phải có @ và domain hợp lệ
→ Use case: đăng ký tài khoản / login

2. type="password"
→ UI: ký tự bị ẩn (••••)
→ Validation: có thể kết hợp minlength/pattern
→ Use case: mật khẩu người dùng

3. type="number"
→ UI: ô nhập số + nút tăng/giảm
→ Validation: chỉ cho phép số, hỗ trợ min/max
→ Use case: số lượng sản phẩm

4. type="date"
→ UI: calendar picker
→ Validation: định dạng ngày hợp lệ
→ Use case: ngày sinh / ngày giao hàng

5. type="tel"
→ UI: ô nhập số điện thoại
→ Validation: không bắt buộc format nhưng hỗ trợ pattern
→ Use case: số liên hệ khách hàng

6. type="radio"
→ UI: chọn 1 trong nhiều lựa chọn
→ Validation: bắt buộc chọn 1 nếu required
→ Use case: giới tính / phương thức thanh toán

7. type="checkbox"
→ UI: tick chọn nhiều mục
→ Validation: có thể required 1 checkbox
→ Use case: đồng ý điều khoản

8. type="file"
→ UI: chọn file từ máy
→ Validation: giới hạn type/size (JS nâng cao)
→ Use case: upload ảnh sản phẩm

9. type="range"
→ UI: thanh kéo slider
→ Validation: trong khoảng min/max
→ Use case: chọn mức giá / số ngày giao

10. type="search"
→ UI: ô tìm kiếm có icon search
→ Validation: không bắt buộc
→ Use case: tìm sản phẩm
 A2 — Dự đoán Validation
Case 1:
required + empty → KHÔNG submit
Lý do: required bắt buộc phải có giá trị

Case 2:
email = "abc" → KHÔNG submit
Lý do: sai format email (thiếu @ và domain)

Case 3:
number 15 (min=1 max=10) → KHÔNG submit
Lý do: vượt giới hạn max

Case 4:
pattern="[0-9]{10}" + "abc123" → KHÔNG submit
Lý do: không đúng 10 chữ số

Case 5:
minlength=8 + value="123" → KHÔNG submit
Lý do: input vẫn validate minlength dù không required
 A3 — Accessibility
1. <label for="email"> quan trọng vì:
Kết nối label với input qua id
Click label → focus input
Screen reader đọc đúng ngữ cảnh
Tăng accessibility (WCAG compliance)
2. <fieldset> + <legend> dùng khi:
Nhóm các input liên quan

Ví dụ:

<fieldset>
  <legend>Thông tin cá nhân</legend>
</fieldset>

Use case:

Form đăng ký
Form thanh toán
Form khảo sát
3. aria-label
Dùng khi KHÔNG có label hiển thị
Ví dụ: icon button (search, menu)

❌ Không nên dùng khi đã có <label> vì:

Gây trùng nội dung screen reader
Giảm accessibility quality
 A4 — Media
1. loading="lazy"
Trì hoãn load ảnh đến khi user scroll tới
Giảm tải trang + tăng tốc độ load

❌ Không dùng khi:

ảnh hero (quan trọng đầu trang)
ảnh cần hiển thị ngay
2. <video> nhiều source vì:
đảm bảo tương thích trình duyệt

Format phổ biến:

MP4
WebM
OGG
3. ALT attribute
iPhone 16:
"iPhone 16 Pro Max màu Titan góc chụp chính diện"
Decorative:
alt=""
Biểu đồ:
"Biểu đồ doanh thu Q1/2026 tăng 20%"
 A5 — <figure> vs <img>
Cách 1 — <img>

Dùng khi:

ảnh đơn giản
không cần caption

Ví dụ:

icon
avatar
thumbnail nhỏ
Cách 2 — <figure>

Dùng khi:

cần mô tả + caption
nội dung mang ý nghĩa

Ví dụ:

sản phẩm ecommerce
ảnh blog
infographic
 PHẦN C — PHÂN TÍCH
 C1 — Debug Form (8 lỗi)
Lỗi 1:
Input "Tên" không có label for/id
Sửa:
<label for="name">Tên</label>
<input id="name" type="text" required>

---

Lỗi 2:
Email thiếu name attribute
Sửa: thêm name="email"

---

Lỗi 3:
Password không có name attribute
Sửa: name="password"

---

Lỗi 4:
Confirm password không có validation logic
HTML không thể check match password
→ phải dùng JavaScript

---

Lỗi 5:
Phone input type="text"
Sửa: type="tel"

---

Lỗi 6:
Select thiếu label
Sửa: thêm <label for="city">

---

Lỗi 7:
Checkbox không có input liên kết rõ ràng
Sửa: wrap input trong label hoặc for/id

---

Lỗi 8:
Submit dùng input type="submit" không semantic tốt
Sửa: dùng <button type="submit">
 C2 — Validation cho ngân hàng
1. Regex

CMND/CCCD (12 số):

^[0-9]{12}$

Số tài khoản (10–15 số):

^[0-9]{10,15}$

PIN (6 số):

^[0-9]{6}$
2. HTML5 có đủ an toàn không?

 Không đủ an toàn

Lý do:

Có thể bypass bằng DevTools
Không mã hóa dữ liệu
Không kiểm soát server-side
Không chống request giả
3. Validation HTML5 KHÔNG làm được
Kiểm tra dữ liệu trùng database
Kiểm tra logic nghiệp vụ (ví dụ tài khoản tồn tại)
So sánh dữ liệu confirm (password match)
Kiểm tra blacklist / fraud detection
4. Rủi ro nếu chỉ dùng frontend validation
User bypass bằng DevTools → gửi dữ liệu sai
Hacker gửi request trực tiếp API (Postman/cURL)