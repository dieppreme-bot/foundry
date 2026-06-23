# FOUNDRY — Project Handoff

> Đọc file này đầu tiên khi tiếp tục dự án trên máy mới.
> Cập nhật lần cuối: **2026-06-21**.

---

## 1. FOUNDRY là gì

Thương hiệu **thư viện học liệu kinh doanh** bán cho thị trường US/UK dưới dạng **PDF bundle**.

- Định vị: "Everything an MBA teaches, without the $100K"
- Tagline: **Sharp · Practical · Accessible**
- Sản phẩm: **25 Business Products** gồm 7 cuốn sách + templates + frameworks
- Giá: **$49 launch** (→ $79 khi bundle mở rộng). Early buyers nhận tất cả sản phẩm tương lai miễn phí.
- Kế hoạch: 25 → 30 → 40+ products. "Early buyers lock in launch price."
- Bán qua: **Gumroad** (đã có link thật — xem mục 6)

---

## 2. Đang LIVE ở đâu

| Bản | URL | Ghi chú |
|-----|-----|---------|
| **v2** (story-driven) | https://foundry-jade.vercel.app/ | Bản gốc |
| **v3** (MBA-anchored) | https://foundry-jade.vercel.app/v3 | Thêm Big Idea / Value Stack |
| **v4** | https://foundry-jade.vercel.app/v4 | Iteration trung gian |
| **v5** | https://foundry-jade.vercel.app/v5 | Hero 2 cột, dark sections |
| **v6** | https://foundry-jade.vercel.app/v6 | Visual-first hero, 25 sách cũ |
| **v7** ⭐ | https://foundry-jade.vercel.app/v7 | **PHIÊN BẢN MỚI NHẤT** — 27 sách mới, Library grid |

**Domain riêng đã add vào Vercel:** `foundbundler.store` / `www.foundbundler.store`
(DNS chưa trỏ hoàn toàn — kiểm tra Vercel → Project → Domains)

⚠️ Domain public dùng để test: `foundry-jade.vercel.app` — KHÔNG dùng URL dài `foundry-dieppreme-4437s-projects.vercel.app` (bị auth chặn).

---

## 3. Hạ tầng & tài khoản

| Thành phần | Giá trị |
|-----------|---------|
| GitHub repo | https://github.com/dieppreme-bot/foundry (branch `main`) |
| Vercel project | `foundry` — team "dieppreme-4437's projects" (Hobby/free) |
| Auto-deploy | Mỗi `git push` lên `main` → Vercel tự build & deploy |
| Gumroad | https://topgum.gumroad.com/l/Foundbundler?wanted=true |
| Google Analytics | Property: **FOUNDBundler Web** · ID: **G-MW676VFVVF** |
| Meta Pixel | ID: **3361285220711101** |
| Email liên hệ | dieppreme@gmail.com |

---

## 4. Cấu trúc repo

```
foundry/
├── index.html          ← v2, LIVE tại /
├── v3/index.html       ← v3, LIVE tại /v3
├── v4/index.html       ← v4, LIVE tại /v4
├── v5/index.html       ← v5, LIVE tại /v5
├── v6/index.html       ← v6, LIVE tại /v6 (25 sách cũ)
├── v7/index.html       ← v7 ⭐ LIVE tại /v7 (MỚI NHẤT — 27 sách)
├── covers/             ← tất cả ảnh bìa sách
│   ├── press-01-profit-levers.png ... press-27-shockproof-finance.png  (27 bìa mới)
│   ├── web-mockup-1.png ... web-mockup-4.png  (ảnh chèn web)
│   ├── v2x.webp, sach-xep-hinh.webp  (mockup cũ v5/v6)
│   └── *.webp  (7 bìa cũ dùng ở v2–v6)
├── vercel.json         ← security headers
├── HANDOFF.md          ← FILE NÀY
└── docs/
    ├── canva-cover-guide.md
    └── teardown-business-explained.txt
```

### Danh sách 27 sách v7 theo track

| # | Tên sách | Track |
|---|----------|-------|
| 01 | Profit Levers | Strategy |
| 02 | Focus Lock | Operations |
| 03 | Momentum Stack | Operations |
| 04 | Signal Mirror | Operations |
| 05 | Sprint Engine | Operations |
| 06 | Algorithms to Advantage | Strategy |
| 07 | The Intelligent Enterprise Engine | Strategy |
| 08 | Brand Gravity | Marketing |
| 09 | Growth Engine Architecture | Strategy |
| 10 | Profit Logic | Strategy |
| 11 | The Revenue Shape System | Finance |
| 12 | Failure-Proof Operator | Finance |
| 13 | The Advantage Map | Strategy |
| 14 | The Advisory Method | Innovation |
| 15 | The Consultant's Operating System | Innovation |
| 16 | The Content Engine Room | Marketing |
| 17 | Audience Magnet Lab | Marketing |
| 18 | Pathways to Purchase | Marketing |
| 19 | From Click to Commitment | Marketing |
| 20 | The Relationship Revenue System | Marketing |
| 21 | The Everyday Security System | Innovation |
| 22 | From Resistance to Rollout | Leadership |
| 23 | The Online Store Operating System | Innovation |
| 24 | The Workplace Energy System | Leadership |
| 25 | Stay Power | Leadership |
| 26 | The Talent Continuity System | Leadership |
| 27 | Shockproof Finance | Finance |

Mọi landing page là **1 file HTML tự chứa** (Tailwind CDN + Google Fonts) — không cần build/npm.

---

## 5. Làm tiếp trên MÁY MỚI

```bash
# 1. Clone repo
git clone https://github.com/dieppreme-bot/foundry.git
cd foundry

# 2. Xem thử trang (không cần server)
# Mở thẳng v6/index.html trong browser
# Hoặc: npx serve -p 3333 .  → http://localhost:3333/v6

# 3. Sửa → deploy
git add -A
git commit -m "mô tả thay đổi"
git push
# Vercel tự build, live sau ~30 giây
```

**Quy ước:**
- Làm việc chính ở `v6/index.html` — đây là phiên bản active nhất
- KHÔNG sửa các file cũ (v2–v5) trừ khi cần A/B test
- Muốn đổi v6 thành trang chính → copy v6/index.html đè vào index.html rồi push

---

## 6. Design system của v7

| Yếu tố | Giá trị |
|--------|---------|
| Font heading | Playfair Display (serif) |
| Font body | Inter |
| Font label | Barlow Condensed |
| Nền trang | `#fafaf8` (trắng ngà) |
| Dark section | `#0F172A` (navy đậm) |
| Màu amber/CTA | `#D97706` |
| CSS framework | Tailwind CDN |

**Cấu trúc sections v7:**
Nav → Hero (fan 7 bìa mới + CTA) → Proof Bar (27 products, 88%) → Problem →
Outcomes (2-col grid) → 6 Tracks (dark, "Browse All 27" CTA) →
**The Library** (27-book grid với filter tabs theo track) →
Why FOUNDRY (2-col: text + web-mockup-2) → Transformation (dark) →
Who It's For → Pricing (web-mockup-1 + 3-col compare $405→$49 + price-hero) →
Future Updates → FAQ → Final CTA (dark) → Footer

---

## 7. Tracking đã cài (tất cả 5 phiên bản)

**Google Analytics 4:**
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-MW676VFVVF"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-MW676VFVVF');
</script>
```

**Meta Pixel:**
```html
<script>
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
  n.callMethod.apply(n,arguments):n.queue.push(arguments)};
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
  n.queue=[];t=b.createElement(e);t.async=!0;
  t.src=v;s=b.getElementsByTagName(e)[0];
  s.parentNode.insertBefore(t,s)}(window,document,'script',
  'https://connect.facebook.net/en_US/fbevents.js');
  fbq('init', '3361285220711101');
  fbq('track', 'PageView');
</script>
```

GA4 cross-domain config: `foundbundler.store` + `foundry-jade.vercel.app` (kiểu "Chứa").

---

## 8. Việc CHƯA xong (ưu tiên từ trên xuống)

1. **🔴 Domain DNS.** `foundbundler.store` đã add vào Vercel nhưng cần trỏ DNS tại nhà đăng ký:
   - CNAME `www` → `cname.vercel-dns.com`
   - A record `@` → IP của Vercel (xem trong Vercel → Domains)

2. **🔴 Upload PDF lên Gumroad.** Link Gumroad đã có (`topgum.gumroad.com/l/Foundbundler`) nhưng cần upload 25 file PDF thật vào sản phẩm.

3. **🟠 OG image thật.** Đang dùng placeholder `via.placeholder.com` → share MXH ra ảnh xám. Cần ảnh 1200×630 (ghép vài cover). Sửa thẻ `<meta property="og:image">` trong tất cả các file.

4. **🟠 Testimonials thật.** Hiện là placeholder. Thay bằng review thật sau khi có khách.

5. **🟡 Verify GA4 realtime.** Vào GA4 → Báo cáo → Thời gian thực, mở trang web, xác nhận thấy 1 active user.

6. **🟡 Facebook Pixel verify.** Cài Meta Pixel Helper extension → mở trang → icon xanh = OK.

7. **🟡 Connect Gumroad + PayPal.** Gumroad dashboard → Settings → Payments → Connect PayPal.

---

## 9. Gotchas / bài học

- **Deployment Protection PHẢI tắt.** Vercel mặc định bật "Vercel Authentication" → khách thấy màn login. Đã tắt tại Vercel → Project → Settings → Deployment Protection. Nếu site trả 401 → kiểm tra lại.
- **Verify deploy bằng curl:** `curl -s -o /dev/null -w "%{http_code}" https://foundry-jade.vercel.app/v6` → phải 200.
- **Encoding:** sửa HTML bằng editor/Claude, KHÔNG dùng PowerShell Set-Content (làm hỏng UTF-8).
- **Repo PUBLIC** — docs/ chứa playbook/research. Cân nhắc đổi sang Private (GitHub → Settings → Change visibility). Vercel vẫn auto-deploy bình thường khi private.
- **Fan image (v6 hero):** 7 file `/covers/*.webp` + CSS transform rotate(-36deg → +36deg), transform-origin: bottom center. Desktop: 480×340px, mobile: 280×210px.

---

## 10. Prompt để tiếp tục với AI khác

Paste đoạn này vào Claude / ChatGPT khi bắt đầu phiên mới:

```
Tôi đang làm landing page cho FOUNDRY — thư viện học liệu kinh doanh PDF bundle bán thị trường US/UK.

Context:
- Repo: https://github.com/dieppreme-bot/foundry (branch main)
- Live: https://foundry-jade.vercel.app/v6 (phiên bản mới nhất)
- Domain riêng: foundbundler.store (DNS đang setup)
- Sản phẩm: 25 business products, $49 launch price (→ $79)
- Bán qua Gumroad: https://topgum.gumroad.com/l/Foundbundler?wanted=true
- GA4: G-MW676VFVVF | Meta Pixel: 3361285220711101
- Deploy: git push lên main → Vercel tự build

File chính cần làm việc: v6/index.html
Design system: Tailwind CDN + Playfair Display + Inter + Barlow Condensed
Màu: nền #fafaf8, dark section #0F172A, amber #D97706

Đọc HANDOFF.md trong repo để biết đầy đủ context.
```
