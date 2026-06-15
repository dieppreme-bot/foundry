# FOUNDRY — Hướng dẫn thiết kế 7 book covers trên Canva

Mục tiêu: làm bản cover cao cấp KHỚP 100% với hệ màu/font đang chạy trên landing page (carousel).

## 0. Thiết lập chung (1 lần)

| Hạng mục | Giá trị |
|----------|---------|
| Kích thước | **1600 × 2560 px** (tỉ lệ 1:1.6, chuẩn Kindle + Gumroad + web) |
| Font tiêu đề | **Playfair Display** (Bold) |
| Font nhãn/brand | **Inter** (hoặc Montserrat) |
| Lề an toàn | chừa ~140px mỗi cạnh |

**Bí quyết:** Thiết kế 1 cover master chuẩn → Canva *Duplicate page* ×6 → mỗi trang chỉ đổi màu nền + accent + tên sách + category + icon mờ. Đảm bảo 7 cover trông như MỘT BỘ (quan trọng để bán bundle).

## 1. Layout master (áp cho cả 7)

Từ trên xuống, căn trái, trong vùng an toàn:

- (1) **FOUNDRY** — brand mark, nhỏ, chữ hoa, giãn cách rộng, trắng opacity ~35%, Inter
- (5) **Motif/icon LỚN mờ** — opacity 8–12%, góc phải trên, đặt Back (làm chiều sâu)
- (2) **Category** — chữ hoa, giãn cách, MÀU ACCENT, Inter
- **Tiêu đề** — Playfair Display Bold, ~110–130px, TRẮNG, 2–3 dòng
- (3) **Gạch accent** — đường kẻ ngắn ~80px màu accent, dưới tiêu đề
- (4) (tùy chọn) Series tag góc dưới: "FOUNDRY LIBRARY · 01"

Nền: màu phẳng, hoặc gradient nhẹ từ màu nền → đen ở đáy.

## 2. Spec từng cuốn (copy hex thẳng vào Canva)

| # | Sách | Category | Nền | Accent | Motif mờ |
|---|------|----------|-----|--------|----------|
| 1 | 10 Disciplines of Deep Focus | FOCUS & PERFORMANCE | `#1A0000` | `#E24B4A` đỏ | Vòng tròn đồng tâm / tâm ngắm |
| 2 | Business Model Mastery | STRATEGY | `#000D1A` | `#378ADD` xanh dương | Lưới ô / khối lắp ghép |
| 3 | 10 Business Wins | GROWTH | `#001409` | `#1D9E75` xanh lá | Mũi tên lên / cột bậc thang |
| 4 | Ecommerce Explained | ECOMMERCE | `#1A0E00` | `#BA7517` hổ phách | Giỏ hàng / thẻ giá |
| 5 | The Agile Manual | OPERATIONS | `#0E0A1A` | `#7F77DD` tím | Vòng lặp mũi tên (sprint) |
| 6 | AI Explained | TECHNOLOGY | `#1A0010` | `#D4537E` hồng | Mạng node / mạch điện |
| 7 | Team Harmony | LEADERSHIP | `#061409` | `#639922` xanh lá mạ | Chấm nối / vòng tròn lồng |

**Quy tắc màu:** Nền luôn tối gần đen. Accent chỉ cho category + line + icon. Tiêu đề LUÔN trắng (không tô accent).

**Tìm icon Canva:** thanh Elements gõ tiếng Anh — "target", "grid", "arrow up", "shopping cart", "refresh cycle", "network nodes", "connected dots". Chọn icon line/outline, kéo to, opacity 8–12%.

## 3. Các bước Canva

1. Create design → Custom size → 1600 × 2560 px
2. Background → màu hex cuốn #1
3. FOUNDRY (Inter ~32px hoa, letter-spacing, trắng 35%) góc trên trái
4. Motif (Elements) → kéo to, opacity ~10%, Position → Back
5. Category (Inter ~28px hoa, accent)
6. Tiêu đề (Playfair Display Bold ~120px trắng)
7. Gạch accent (line element, accent, ~80px) dưới tiêu đề
8. (tùy chọn) Series tag góc dưới
9. Duplicate page → đổi cho cuốn #2…#7
10. Share → Download → PNG → tick Select pages → xuất cả 7

## 4. Sau khi có cover thật

| Nơi | Cách |
|-----|------|
| Hero carousel (web) | Thay mỗi `<div class="carousel-slide">…</div>` bằng `<img src="cover-N.jpg" style="width:100%;height:100%;object-fit:cover;border-radius:6px 10px 10px 6px">` |
| Gumroad | Upload làm thumbnail sản phẩm |
| OG image | Ghép vài cover lên nền tối → ảnh 1200×630 (thay placeholder đang treo) |

## ✅ Checklist đồng bộ trước khi xuất

- [ ] 7 cover: vị trí FOUNDRY/category/tiêu đề giống hệt (chỉ khác màu + chữ)
- [ ] Tiêu đề trắng, category màu accent
- [ ] Nền đủ tối để chữ trắng nổi
- [ ] Icon motif mờ ≤12%, không lấn chữ
- [ ] Không chữ nào chạm mép (lề 140px)
