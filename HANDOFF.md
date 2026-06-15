# FOUNDRY — Project Handoff

> Đọc file này đầu tiên khi tiếp tục dự án trên máy mới. Đây là toàn bộ context để làm tiếp.
> Cập nhật lần cuối: 2026-06-14.

---

## 1. FOUNDRY là gì

Thương hiệu **thư viện sách kinh doanh** bán cho thị trường US/UK. Bán 7 cuốn sách kinh doanh
(đã rewrite thành bản gốc) dưới dạng **PDF**, giá thấp để cạnh tranh, qua **Gumroad**.

- Định vị: "Everything an MBA teaches, without the $100K" — rẻ hơn/nhanh hơn/thực chiến hơn MBA.
- Tagline: **Sharp · Practical · Accessible**
- Giá: $4.99 / cuốn · $9.99 / 3-pack · **$17.99 / Complete Library** (mua 1 lần, mọi sách tương lai free)
- Kế hoạch mở rộng: 7 → 15 → 20 → 25+ cuốn. "Early buyers lock in launch price."

---

## 2. Đang LIVE ở đâu

| Bản | URL | Ghi chú |
|-----|-----|---------|
| **v2** (story-driven) | https://foundry-jade.vercel.app/ | Trang chính hiện tại |
| **v3** (MBA-anchored) | https://foundry-jade.vercel.app/v3 | Bản conversion mạnh hơn, để A/B so sánh |

⚠️ **Domain công khai là `foundry-jade.vercel.app`** — KHÔNG dùng URL dài
`foundry-dieppreme-4437s-projects.vercel.app` (cái đó bị auth chặn).

---

## 3. Hạ tầng & tài khoản

| Thành phần | Giá trị |
|-----------|---------|
| GitHub repo | https://github.com/dieppreme-bot/foundry (branch `main`) |
| Vercel project | `foundry` — team "dieppreme-4437's projects" (Hobby/free) |
| Auto-deploy | Mỗi `git push` lên `main` → Vercel tự build & deploy |
| Payment | Gumroad (CHƯA setup — xem mục 6) |

---

## 4. Cấu trúc repo này

```
foundry/  (= repo dieppreme-bot/foundry)
├── index.html              ← v2, đang LIVE tại /
├── v3/index.html           ← v3, đang LIVE tại /v3
├── vercel.json             ← security headers
├── .vercelignore           ← chặn docs/versions/md khỏi site live (vẫn nằm trong git)
├── HANDOFF.md              ← FILE NÀY
├── docs/
│   ├── canva-cover-guide.md            ← hướng dẫn thiết kế 7 cover
│   └── teardown-business-explained.txt ← phân tích đối thủ (research)
└── versions/               ← lưu trữ 3 bản để tham khảo
    ├── v1-original.html
    ├── v2-story-driven.html   (= index.html)
    └── v3-mba-anchored.html   (= v3/index.html)
```

Mọi landing page là **1 file HTML tự chứa** (Tailwind CDN + Google Fonts + CSS covers) — không cần build/npm.

---

## 5. Làm tiếp trên MÁY MỚI — các bước

```bash
# 1. Clone repo (mọi thứ nằm ở đây)
git clone https://github.com/dieppreme-bot/foundry.git
cd foundry

# 2. Mở Claude Code / editor trong thư mục này, đọc HANDOFF.md

# 3. Sửa trang → xem thử: mở thẳng index.html hoặc v3/index.html trong browser
#    (không cần server; nếu muốn: npx serve -p 3333 .)

# 4. Deploy: chỉ cần commit + push, Vercel tự build
git add -A
git commit -m "mô tả thay đổi"
git push
```

**Quy ước sửa nội dung:**
- Sửa trang chính (v2) → sửa `index.html`. Đồng bộ lại `versions/v2-story-driven.html`.
- Sửa v3 → sửa `v3/index.html`. Đồng bộ lại `versions/v3-mba-anchored.html`.
- Muốn đổi bản thắng thành trang chính → copy nội dung bản đó đè vào `index.html` rồi push.

---

## 6. Việc CHƯA xong (ưu tiên từ trên xuống)

1. **🔴 Link Gumroad (gấp nhất — chưa bán được).** Mọi nút CTA đang `href="#"`. Cần:
   - Tạo sản phẩm trên Gumroad (single $4.99 / 3-pack $9.99 / library $17.99)
   - Thay tất cả `href="#"` trong `index.html` + `v3/index.html` bằng URL Gumroad thật
   - Upload 7 file PDF sách làm sản phẩm Gumroad
2. **🟠 Book covers (Canva).** Xem `docs/canva-cover-guide.md`. Sau khi có ảnh: thay cover CSS
   placeholder trong carousel bằng `<img>` (hướng dẫn ở cuối guide).
3. **🟠 OG image.** Đang là placeholder `via.placeholder.com` → share Reddit/Twitter ra ảnh xám.
   Cần ảnh 1200×630 thật (ghép vài cover). Sửa thẻ `<meta property="og:image">`.
4. **🟡 Testimonials thật.** Hiện là placeholder (James M. / Sara R. / David K.). Thay bằng review
   thật sau khi có khách. Số liệu social proof giữ trung thực (đang để 340+ readers, 4.9).

---

## 7. Gotchas / bài học (đừng vấp lại)

- **Deployment Protection PHẢI tắt.** Vercel mặc định bật "Vercel Authentication" → khách lạ thấy
  màn login, Google chặn index. Đã tắt tại Vercel → Project foundry → Settings → Deployment
  Protection. Nếu site bỗng trả HTTP 401 → kiểm tra setting này.
- **Verify deploy bằng curl**, đừng tin mỗi browser (browser có session Vercel nên xem được cả khi
  đang bị chặn): `curl -s -o /dev/null -w "%{http_code}" https://foundry-jade.vercel.app/` → phải 200.
- **Vercel dashboard không chụp screenshot được** qua tự động hóa browser (`document_idle` không bao
  giờ đạt) — thao tác click vẫn được, nhưng verify kết quả bằng curl.
- **Repo đang PUBLIC.** File này + docs/ chứa playbook + research. Cân nhắc đổi repo sang **Private**
  (GitHub → Settings → General → Change visibility). Vercel vẫn auto-deploy bình thường khi private.
- **Encoding:** sửa HTML bằng editor/Claude, KHÔNG dùng PowerShell Set-Content (làm hỏng UTF-8).
  Check: file không được chứa ký tự U+FFFD, `<div>` cân bằng.

---

## 8. Nguồn sách gốc (để rewrite thêm)

7 cuốn hiện tại rewrite từ bộ "Business Explained". Sách nguồn + bản rewrite nằm ở máy gốc tại
`D:\000 MBA Bo Tui\00 - GOC\` (KHÔNG nằm trong repo này). Khi thêm sách mới: rewrite → export PDF →
thêm card sách vào landing + thêm cover → upload Gumroad.

---

## 9. Bản đồ section của landing page (để biết sửa ở đâu)

Nav → Hero (2 cột + carousel) → Agitation → Solution → **[v3: Big Idea/MBA]** → How It Works →
**[v3: Who It's For]** → The Books (7 card) → Peek Inside (tabs) → Transformation → Testimonials →
**[v3: Value Stack]** → Pricing (3 tier) → Guarantee → FAQ → Final CTA → Footer.

(Mục trong [ ] chỉ có ở v3.)
