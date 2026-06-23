# FOUNDRY — AI Continuation Guide

> Copy toàn bộ file này vào Claude / ChatGPT / Codex khi bắt đầu phiên mới.
> AI sẽ hiểu đủ context để làm tiếp ngay, không cần giải thích.

---

## PHẦN 1 — PASTE VÀO AI (system context)

```
Bạn đang hỗ trợ tôi phát triển landing page cho dự án FOUNDRY.

=== DỰ ÁN LÀ GÌ ===
FOUNDRY là thư viện học liệu kinh doanh (PDF bundle) bán cho thị trường US/UK.
- Sản phẩm: 25 Business Products (sách PDF + frameworks + templates)
- Giá: $49 launch (tăng lên $79 khi bundle mở rộng)
- Định vị: "Everything an MBA teaches, without the $100K"
- Bán qua Gumroad: https://topgum.gumroad.com/l/Foundbundler?wanted=true

=== REPO & DEPLOY ===
- GitHub: https://github.com/dieppreme-bot/foundry (branch: main)
- Live URL: https://foundry-jade.vercel.app/v6 (phiên bản mới nhất)
- Domain: foundbundler.store (đang setup DNS)
- Deploy: git push lên main → Vercel tự build, live sau ~30 giây
- KHÔNG cần build/npm — mọi file là HTML tự chứa

=== CÁC PHIÊN BẢN ===
- / (index.html) = v2 gốc
- /v3, /v4, /v5 = các iteration cũ, KHÔNG sửa
- /v6 = PHIÊN BẢN ĐANG LÀM ← tập trung vào đây

=== FILE CHÍNH ===
v6/index.html — chỉnh sửa file này

=== DESIGN SYSTEM (v6) ===
- CSS: Tailwind CDN (https://cdn.tailwindcss.com)
- Font: Playfair Display (heading serif) + Inter (body) + Barlow Condensed (label/eyebrow)
- Màu nền trang: #fafaf8
- Dark section: #0F172A
- Amber/CTA: #D97706
- Button chính (.cta-btn): nền #111, chữ trắng
- Button sáng (.cta-btn-light): nền trắng, chữ đen

=== STRUCTURE v6 (thứ tự sections) ===
Nav → Hero (fan 7 bìa sách + CTA) → Proof Bar → Problem →
Outcomes (2-col grid) → 6 Tracks (dark) → Why FOUNDRY →
Transformation (dark, card ngang) → Who It's For →
Pricing (3-col compare + price-hero box) → Future Updates →
FAQ → Final CTA (dark) → Footer

=== TRACKING (đã cài tất cả versions) ===
- Google Analytics 4: G-MW676VFVVF
- Meta Pixel: 3361285220711101

=== ẢNH / COVERS ===
Nằm trong thư mục /covers/ của repo:
- 7 bìa sách WebP: ai-decoded.webp, agile-manual.webp, business-model-mastery.webp,
  common-business-mistakes.webp, mastering-corporate-finance.webp,
  10-business-wins.webp, 10-disciplines.webp
- v2x.webp: 3D mockup stack sách (dùng trong pricing section)

=== QUY TẮC QUAN TRỌNG ===
1. Chỉ sửa v6/index.html trừ khi được yêu cầu rõ ràng
2. Không sửa vercel.json, index.html (v2), v3/, v4/, v5/
3. Sửa HTML bằng editor — KHÔNG dùng PowerShell Set-Content (hỏng UTF-8)
4. Sau mỗi thay đổi: git add v6/index.html && git commit -m "..." && git push
5. Verify: curl -s -o /dev/null -w "%{http_code}" https://foundry-jade.vercel.app/v6 → phải 200
6. Mọi nút CTA mua hàng đều link đến: https://topgum.gumroad.com/l/Foundbundler?wanted=true

=== VIỆC CÒN LẠI (ưu tiên) ===
🔴 1. Trỏ DNS foundbundler.store về Vercel (CNAME www → cname.vercel-dns.com)
🔴 2. Upload 25 PDF thật lên Gumroad product
🟠 3. Thay OG image placeholder (via.placeholder.com) bằng ảnh thật 1200×630
🟠 4. Thay testimonials placeholder bằng review thật
🟡 5. Verify GA4 realtime hoạt động (vào GA → Báo cáo → Thời gian thực)
🟡 6. Kết nối PayPal vào Gumroad (Gumroad Settings → Payments)

Đọc HANDOFF.md trong repo để biết chi tiết đầy đủ hơn.
```

---

## PHẦN 2 — HƯỚNG DẪN LÀM VIỆC VỚI AI

### Cách bắt đầu phiên mới

1. Mở Claude / ChatGPT / Codex
2. Paste toàn bộ block code ở PHẦN 1 vào
3. Thêm yêu cầu cụ thể của bạn vào cuối

Ví dụ:
```
[paste PHẦN 1]

Yêu cầu hôm nay: Sửa lại phần testimonials — tôi có 3 review thật từ khách hàng như sau: [...]
```

---

### Các lệnh hay dùng nhất

**Xem trang trước khi deploy:**
```bash
npx serve -p 3333 .
# Mở http://localhost:3333/v6
```

**Deploy:**
```bash
cd "đường dẫn đến thư mục foundry-repo"
git add v6/index.html
git commit -m "mô tả thay đổi"
git push
```

**Kiểm tra live:**
```bash
curl -s -o /dev/null -w "%{http_code}" https://foundry-jade.vercel.app/v6
# Phải ra 200
```

**Clone về máy mới:**
```bash
git clone https://github.com/dieppreme-bot/foundry.git
cd foundry
```

---

### Prompt mẫu cho từng tác vụ phổ biến

**Sửa copy/nội dung:**
```
[PHẦN 1]
Tôi muốn sửa nội dung phần [tên section] trong v6/index.html.
Nội dung mới: [...]
Giữ nguyên HTML structure, chỉ thay text.
```

**Thêm section mới:**
```
[PHẦN 1]
Thêm section mới vào v6/index.html sau section [tên section hiện tại].
Section cần có: [mô tả]. Dùng đúng design system đã có (font, màu, CSS classes).
```

**Fix lỗi hiển thị:**
```
[PHẦN 1]
Phần [tên section] trên mobile đang bị [mô tả lỗi].
Screenshot: [đính kèm ảnh]
Sửa CSS/HTML để khắc phục.
```

**Thêm tính năng:**
```
[PHẦN 1]
Thêm [tính năng] vào v6/index.html.
Yêu cầu: [chi tiết]. Không dùng thư viện ngoài, chỉ vanilla JS + Tailwind.
```

---

### Với Claude Code (CLI)

Nếu dùng Claude Code trong terminal, chạy lệnh này để load context:

```bash
cd "đường dẫn/foundry-repo"
claude
# Claude tự đọc HANDOFF.md và AI-PROMPT.md trong thư mục
```

Sau đó gõ yêu cầu bình thường — Claude Code sẽ tự đọc file, sửa, và commit.

---

### Với Codex (GitHub Copilot / OpenAI)

1. Mở repo trong VS Code
2. Mở file `v6/index.html`
3. Dùng Copilot Chat, paste PHẦN 1 + yêu cầu
4. Copilot sẽ suggest trực tiếp trong file

---

## PHẦN 3 — CHECKLIST TRƯỚC KHI LAUNCH

- [ ] DNS `foundbundler.store` trỏ đúng về Vercel
- [ ] `curl https://www.foundbundler.store` trả 200
- [ ] Gumroad product có đủ 25 PDF đã upload
- [ ] Nhấn nút "Get Bundle" → mở đúng trang Gumroad thanh toán được
- [ ] GA4 Realtime thấy user khi mở trang
- [ ] Meta Pixel Helper extension xác nhận pixel hoạt động
- [ ] OG image thật (share lên Facebook/Twitter ra ảnh đẹp)
- [ ] Testimonials là review thật
- [ ] Không còn chữ "placeholder" nào trong trang
