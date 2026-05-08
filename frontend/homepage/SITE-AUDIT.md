# MÍNG LÌ — Site Audit Report

**Date:** 2026-05-07
**Scope:** 5 HTML pages + backend API

---

## 1. File Inventory

| File | Size | Status |
|------|------|--------|
| `index.html` | 34 KB | ✅ Generated |
| `cases.html` | 48 KB | ✅ Generated |
| `what-is-bazi.html` | 36 KB | ✅ Generated |
| `reading.html` | 33 KB | ✅ Generated |
| `sample-report.html` | 44 KB | ✅ Generated |
| `backend/main.py` | — | ✅ Generated |
| `backend/requirements.txt` | — | ✅ Generated |

**Total: 7 files. All generated.**

---

## 2. Internal Link Matrix

| From → To | index.html | cases.html | what-is-bazi.html | reading.html | sample-report.html |
|-----------|-----------|-----------|------------------|-------------|-------------------|
| **index.html** | — | ✅ cases.html | ✅ what-is-bazi.html | ✅ reading.html | ✅ sample-report.html |
| **cases.html** | ✅ index.html | — | ✅ what-is-bazi.html | ✅ reading.html | ✅ sample-report.html |
| **what-is-bazi.html** | ✅ index.html | ✅ cases.html | — | ✅ reading.html | ✅ sample-report.html |
| **reading.html** | ✅ index.html | ✅ cases.html | ✅ what-is-bazi.html | — | ✅ sample-report.html |
| **sample-report.html** | ✅ index.html | ✅ cases.html | ✅ what-is-bazi.html | ✅ reading.html | — |

**Result: All 20 cross-page links verified. No broken links.**

### Same-page anchors on index.html
| Anchor | Target Section | Status |
|--------|---------------|--------|
| `#get-reading` | Final CTA section (line 905) | ✅ Exists |
| `#what-is-bazi` | Features section (line 754) | ✅ Exists |

### Same-page anchors on sample-report.html
| Anchor | Target Chapter | Status |
|--------|---------------|--------|
| `#ch1`–`#ch10` | All 10 chapter divs | ✅ All exist |

---

## 3. Style Consistency

| Property | index | cases | what-is-bazi | reading | sample-report | Consistent? |
|----------|-------|-------|-------------|---------|--------------|-------------|
| Background `#0C0E14` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Gold `#C9A96E` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Playfair Display (headings) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Inter (body) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Nav structure | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Footer structure | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Mobile nav toggle | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| `nav-active` CSS class | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

---

## 4. Responsive Checklist

| Page | Viewport Meta | Mobile Nav Toggle | Tablet Grid | Mobile Grid |
|------|--------------|-------------------|-------------|-------------|
| index.html | ✅ | ✅ 3-line hamburger | ✅ 2-col | ✅ 1-col |
| cases.html | ✅ | ✅ 3-line hamburger | ✅ | ✅ 1-col stacked |
| what-is-bazi.html | ✅ | ✅ 3-line hamburger | ✅ 3/2-col elements | ✅ 1-col |
| reading.html | ✅ | ✅ 3-line hamburger | ✅ 2-col pillars | ✅ 1-col |
| sample-report.html | ✅ | ✅ 3-line hamburger | ✅ sidebar hidden | ✅ 1-col full width |

**All 5 pages: viewport meta present, mobile nav toggle present, responsive breakpoints at 1024px / 768px / 480px.**

---

## 5. SEO Check

| Page | `<title>` | `meta description` | `lang="en"` | Viewport |
|------|-----------|-------------------|-------------|----------|
| index.html | ✅ "MING LI — Your Destiny, Decoded" | ❌ **MISSING** | ✅ | ✅ |
| cases.html | ✅ "Famous Cases — MÍNG LÌ" | ❌ **MISSING** | ✅ | ✅ |
| what-is-bazi.html | ✅ "What is Bazi? — MÍNG LÌ" | ✅ Present | ✅ | ✅ |
| reading.html | ✅ "Your Reading — MÍNG LÌ" | ❌ **MISSING** | ✅ | ✅ |
| sample-report.html | ✅ "Sample Report — MÍNG LÌ" | ✅ Present | ✅ | ✅ |

**Issue: index.html, cases.html, reading.html are missing meta descriptions.**

---

## 6. JavaScript Interactions

| Page | Feature | Logic |
|------|---------|-------|
| **index.html** | Mobile nav toggle | ✅ hamburger → `navLinks.classList.toggle('open')` |
| **cases.html** | Mobile nav toggle | ✅ Same as index |
| | Case card expand/collapse | ✅ `toggleCase()` toggles `.open` on `.case-card` |
| **what-is-bazi.html** | Mobile nav toggle | ✅ Same as index |
| | FAQ accordion | ✅ `toggleFaq()` — only one open at a time |
| **reading.html** | Mobile nav toggle | ✅ Same as index |
| | Form submission → loading → report | ✅ 3-sec simulated flow, `TODO` for real API |
| **sample-report.html** | Mobile nav toggle | ✅ Same as index |
| | Chapter sidebar scroll-spy | ✅ `IntersectionObserver` highlights active chapter |

---

## 7. Known Issues & Placeholders

### High Priority
| # | Issue | Location | Details |
|---|-------|----------|---------|
| 1 | **Missing meta descriptions** | index.html, cases.html, reading.html | Need `<meta name="description" content="...">` |
| 2 | **No real API integration** | reading.html | Form submission uses `setTimeout(3000)` — `TODO` block exists for `/generate-report` endpoint |
| 3 | **Payment not implemented** | reading.html (unlock card) | "Unlock now →" button links to `#`, alerts placeholder message |
| 4 | **Backend not running** | backend/main.py | Requires `DASHSCOPE_API_KEY` in `.env` |

### Medium Priority
| # | Issue | Location | Details |
|---|-------|----------|---------|
| 5 | **`href="#"` placeholder links** | All pages | Privacy, Terms, Contact, and "Read full analysis" links point to `#` |
| 6 | **Static data in sample report** | sample-report.html | Alexandra Chen's report is hardcoded HTML — not generated by API |
| 7 | **No PDF generation** | reading.html unlock card | Claims "PDF download" but no PDF feature exists |
| 8 | **No 30-day guarantee logic** | reading.html unlock card | Claims guarantee but no refund mechanism |
| 9 | **Google Fonts loading** | All pages | External dependency — if offline, falls back to system fonts |

### Low Priority
| # | Issue | Location | Details |
|---|-------|----------|---------|
| 10 | **`/` CTA on index.html** | index.html hero section | "Get my reading — $9.99" links to `/#` — should link to `reading.html` |
| 11 | **No favicon** | All pages | No `<link rel="icon">` — browser shows default globe |
| 12 | **No Open Graph tags** | All pages | Missing `og:title`, `og:description`, `og:image` for social sharing |
| 13 | **No 404 page** | N/A | Missing custom 404 page |
| 14 | **No loading optimization** | All pages | Google Fonts loaded synchronously — could use `display=swap` (already used) |

---

## 8. Next Steps (Priority Order)

### Phase 1 — Foundation (Do First)
1. **Add meta descriptions** to index.html, cases.html, reading.html — 3 lines each
2. **Fix `/#` CTA** on index.html hero → link to `reading.html`
3. **Connect reading.html form to FastAPI backend** — uncomment the `TODO` block, wire `fetch('/generate-report')`
4. **Add favicon** — simple gold MÍNG LÌ icon, 32×32 PNG

### Phase 2 — Payment (Core Business)
5. **Integrate payment gateway** (Stripe recommended for overseas audience):
   - Add Stripe.js to reading.html
   - Create `/create-checkout-session` endpoint in FastAPI
   - After payment success, remove blur from locked chapters
   - Generate PDF report (use `weasyprint` or `pdfkit`)
6. **Add "30-day guarantee" refund policy** — link to a simple policy page

### Phase 3 — Polish
7. **Add Open Graph tags** to all pages for social sharing
8. **Create 404 page** — branded, with link back to index.html
9. **Replace `#` links** — Privacy/Terms pages, "Read full analysis" on cases.html should link to specific case pages (or reading.html with pre-filled data)
10. **Add analytics** (Plausible or Google Analytics) — track form submissions, unlock clicks

### Phase 4 — Performance
11. **Preload Google Fonts** — add `<link rel="preload">` for font files
12. **Lazy-load images** if any are added later
13. **Add `defer` to script tags** — currently inline scripts are fine, but external ones should be deferred
14. **Set up CI/CD** — deploy to Vercel, Railway, or Render

---

*End of audit.*
