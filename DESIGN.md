# DESIGN.md — Trà Yên (quán trà đạo)

Landing page cho quán trà đạo Trà Yên. Repo: https://github.com/Muse-Soft/m-software-tra-yen
Task Thiết kế: TEC-198 · Epic: TEC-197 · Yêu cầu web: MSR-25.
Tài liệu này là quyết định thiết kế DUY NHẤT cho sprint: Dev (TEC-199) dựng đúng theo đây, QA (TEC-200) đối chiếu theo đây. Cấm mô tả chung chung kiểu "đẹp, hiện đại" không kèm thông số — mọi điểm dưới đây đều có số đo cụ thể.

## 1. Phong cách tham chiếu (MỘT phong cách, tên rõ)

**Wabi-sabi Nhật Bản tối giản, mộc mạc** — vẻ đẹp của sự không hoàn hảo, vật liệu thô, khoảng trống.
Áp dụng cụ thể: bề mặt giấy ấm, gỗ mộc không sơn bóng, gốm men thô, một vật một khoảng trống (không xếp chồng đồ trang trí), không bóng đổ mạnh, không màu neon, không họa tiết rườm rà, không hiệu ứng chuyển động nhanh.

## 2. Bảng màu (mã hex kèm vai trò — không dùng màu ngoài bảng này)

| Mã hex | Vai trò | Dùng ở đâu / quy tắc |
|---|---|---|
| `#F3EDE1` | Nền chính | Toàn trang; nền các khối nội dung |
| `#E7DCC8` | Nền phụ | Thẻ thực đơn, khối xen kẽ, nền form; tách khối mà không cần đường kẻ đậm |
| `#2B2620` | Chữ chính + nền tối | Toàn bộ chữ nội dung; nền footer và khối lịch trà thất (chữ trên nền tối dùng `#F3EDE1`) |
| `#6F7D4F` | Nhấn (xanh matcha ô-liu) | Nút chính (nền nút, chữ `#F3EDE1`), link, tiêu đề phụ, đường kẻ nhấn, số bước nghi thức |
| `#8A7B63` | Chữ phụ + đường kẻ mảnh | Nhãn nhỏ, chú thích, đường kẻ hairline 1px; KHÔNG dùng làm chữ nội dung chính (độ tương phản thấp) |
| `#FFFFFF` | Ô nhập liệu | Nền các ô input/select/textarea của form, trên nền `#E7DCC8` |

Quy tắc tương phản: chữ nội dung luôn `#2B2620` trên `#F3EDE1` hoặc `#FFFFFF`; `#6F7D4F` chỉ dùng cho chữ lớn (tiêu đề, ≥ 20px) hoặc chữ trên nền nút; không đặt chữ nhỏ màu `#8A7B63` trên nền `#F3EDE1`.

## 3. Font chữ (cụ thể, có subset tiếng Việt)

- **Tiêu đề: Playfair Display** (serif, chân thanh mảnh, hợp không khí trà đạo cổ điển). Tải qua Google Fonts với subset `vietnamese`. Chữ hoa đầu câu, không viết hoa toàn bộ tiêu đề.
- **Nội dung: Be Vietnam Pro** (sans, đọc rõ tiếng Việt có dấu). Tải qua Google Fonts với subset `vietnamese`.
- Cỡ chữ desktop: H1 hero 56–64px; H2 khối 32–40px; H3 22–24px; nội dung 16–18px, line-height 1.7–1.8; chú thích/nhãn 13–14px, letter-spacing 0.12em cho nhãn viết hoa.
- Cỡ chữ mobile (< 768px): H1 36–40px; H2 26–30px; nội dung 16px, line-height 1.7. Không thu nhỏ dưới 15px cho nội dung.

## 4. Quy tắc hình ảnh (tỉ lệ khung, tông ảnh)

- **Tông ảnh: gam ấm, tĩnh, nhiều khoảng trống.** Ảnh chụp bàn trà, ấm gốm, lá trà, ánh nắng qua cửa sổ — không ảnh đông người, không ảnh sặc sỡ, không ảnh quảng cáo bóng bẩy. Ảnh mẫu lấy từ Unsplash, khai báo rõ là ảnh mẫu trong code và trong comment kết quả của Dev.
- **Ảnh là nội dung chính (visual-first, §16.1):** mỗi khối có ít nhất một ảnh lớn; chữ ngắn, không đoạn văn dài.
- **Tỉ lệ khung bắt buộc:**
  - Hero: 16:9, full-bleed toàn màn hình (100vh desktop, 80vh mobile), ảnh phủ kín, lớp phủ tối nhẹ để chữ đọc được.
  - Triết lý: ảnh 4:5 đặt cạnh khối chữ (desktop 2 cột 45/55; mobile ảnh trên, chữ dưới).
  - Thực đơn trà: ảnh vuông 1:1 cho mỗi món.
  - Nghi thức pha trà: ảnh 3:2 cho mỗi bước.
  - Không gian: ảnh 4:3, lưới 2 cột desktop.
- **Khoảng trắng:** padding dọc mỗi khối 96px desktop / 56px mobile; khoảng cách giữa các khối nội dung tối thiểu 48px; nội dung chính giới hạn chiều rộng 1120px, căn giữa.

## 5. Bố cục trang (thứ tự khối, không đổi thứ tự)

1. **Header** (dính trên cùng, nền `#F3EDE1`, cao 64px): logo chữ "Trà Yên" (Playfair Display, 24px, `#2B2620`) bên trái; nav phải: Triết lý · Thực đơn · Không gian · Lịch trà thất · Đặt chỗ; nút "Đặt chỗ" nền `#6F7D4F`. Mobile: nav thu gọn thành nút menu.
2. **Hero toàn màn hình** — ảnh bàn trà gỗ mộc bên cửa sổ nắng sớm (16:9 full-bleed). Tiêu đề: "Trà Yên — một chén trà, một khoảng lặng." + 1 câu dẫn ngắn (tối đa 2 dòng) + 2 nút: "Xem thực đơn" (nền `#6F7D4F`) và "Đặt chỗ" (viền `#F3EDE1`, chữ `#F3EDE1`).
3. **Triết lý trà đạo** — H2 "Uống trà là trở về với sự tĩnh lặng" + 2 đoạn ngắn (mỗi đoạn tối đa 3 câu) + ảnh 4:5. Nội dung triết lý: chậm, ít, thật — không khẩu hiệu sáo rỗng.
4. **Thực đơn trà theo mùa** — H2 "Trà theo mùa". Lưới 3 cột desktop / 1 cột mobile, mỗi món: ảnh 1:1, tên trà, mô tả 1 dòng, giá. 4 món mẫu theo mùa (xuân, hạ, thu, đông — ví dụ: trà xanh xuân, ô long hạ, phổ nhĩ thu, trà sen đông). **Tất cả giá đều là "Giá mẫu"** (ghi rõ chữ "Giá mẫu" cạnh giá, ví dụ 45.000đ–120.000đ/ấm) — giá thật chờ bổ sung, không bịa.
5. **Không gian + nghi thức pha trà từng bước** — H2 "Nghi thức pha trà". 4 bước đánh số 01–04, mỗi bước: ảnh 3:2 + tên bước + 1–2 câu mô tả (tráng ấm → đánh thức trà → hãm → thưởng). Dưới đó: khối không gian với 2 ảnh 4:3 (trà thất, góc cửa sổ) + 1 đoạn ngắn về không gian yên tĩnh, tối đa 30 chỗ.
6. **Lịch trà thất + đặt chỗ** — nền tối `#2B2620`, chữ `#F3EDE1`. Bảng lịch 7 ngày mẫu (giờ mở cửa mẫu 8:00–21:00, trà thất riêng theo khung giờ) + ghi chú "Lịch mẫu". Nút "Đặt chỗ" dẫn xuống form.
7. **Form liên hệ / đặt bàn** — nền `#E7DCC8`, các ô nền `#FFFFFF`. 5 trường: họ tên, số điện thoại, ngày muốn đến, khung giờ, số khách (ghi chú thêm tùy chọn). **Form chỉ giao diện (frontend-only):** bấm gửi chỉ hiện thông báo "Bản demo — form chưa gửi dữ liệu thật", không hứa hẹn xác nhận, không gọi API thật. Dùng `preventDefault`.
8. **Footer** — nền `#2B2620`, chữ `#F3EDE1`: tên quán, địa chỉ **[CẦN BỔ SUNG]**, điện thoại **[CẦN BỔ SUNG]**, giờ mở cửa mẫu, link nav lặp lại. Địa chỉ/điện thoại thật CHƯA CÓ — tuyệt đối không bịa số, không dùng số mẫu làm số thật.

## 6. Responsive và chuyển động

- Breakpoint duy nhất: 768px. Dưới 768px: mọi lưới về 1 cột; hero 80vh; header chỉ còn logo + nút menu; bảng lịch cuộn ngang nếu cần.
- Chuyển động: chỉ fade-in nhẹ 300–500ms khi cuộn tới khối; không hiệu ứng nảy, không parallax mạnh, không autoplay video. Đúng tinh thần tĩnh của wabi-sabi.

## 7. Ghi chú cho Dev (TEC-199) và QA (TEC-200)

- Dev: dựng đủ 8 khối theo đúng thứ tự mục 5; màu/font/khung ảnh đúng mục 2–4; ảnh mẫu Unsplash phải khai báo là ảnh mẫu; form có thông báo demo; không dùng màu/font ngoài tài liệu này.
- QA: đối chiếu đủ 4 điểm §16.2 (bảng màu có vai trò, font cụ thể, 1 phong cách tham chiếu, quy tắc ảnh) + đủ 8 khối + giá ghi "Giá mẫu" + địa chỉ/điện thoại là `[CẦN BỔ SUNG]` + form demo. Lệch rõ (sai màu/font chủ đạo, vỡ bố cục, ảnh lệch tông) là lỗi Dev sửa được (§12.9). Không chụp được màn hình thì ghi rõ "chưa kiểm thị giác — mới kiểm mức code".
