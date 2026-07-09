# CookieClear — Project Status

> Last updated: 2026-07-08（SnapMark 已上架，CWS SEO 教训：上架后有 2-7 天索引延迟，搜全称能找到 = 已索引，搜简称找不到 = 排名垫底。上架后立刻去 CWS 后台优化详细描述，秒生效不需要重新审核。）

---

## Current State: Resubmitting After Rejection 🔧

First submission rejected for "keyword spam" — competitor names in title/description/keywords.
All competitor references removed. Resubmitting.

### What's Built

| Module | Status | Notes |
|--------|:------:|-------|
| Manifest V3 | ✅ | 4 permissions, popup + options + service worker |
| Cookie CRUD | ✅ | View, add, edit, delete individual and bulk |
| Import | ✅ | JSON and Netscape format parsing |
| Export | ✅ | JSON, Netscape (curl/wget), cURL command |
| Cookie Classification | ✅ | 6 categories, name pattern + domain matching |
| Privacy Score | ✅ | 0-100 with color gauge, tracker breakdown |
| Domain Whitelist | ✅ | Preserve cookies from trusted domains on bulk delete |
| Undo | ✅ | 50-action stack, Ctrl+Z, delete/add/edit reversal |
| Dark/Light Mode | ✅ | System preference detection + manual toggle |
| Search/Filter | ✅ | Real-time client-side filtering |
| Settings Page | ✅ | Theme selector, whitelist management |
| Tracking Database | ✅ | 101 tracking domains from Disconnect.me (bundled, offline) |
| Icons | ✅ | 16/48/128px |

### Test Coverage

```
76 tests, 0 failures (8.6s)
  50 unit tests: export, import, undo, classify, privacy scoring
  26 e2e tests:  extension loading, popup rendering, options page,
                  manifest validation, resource accessibility, CDP cookies
```

Run: `npm test`

### File Size

```
Total: ~83 KB (well under 200KB target)
  20 source files
  0 dependencies (vanilla JS)
```

---

## What's Next

### Before CWS Submission
- [x] Create a proper 128x128 icon (current is placeholder)
- [x] Create CWS store listing assets (3 screenshots at 1280×800 + 3 promo tiles)
- [x] Write CWS description with SEO keywords → `docs/store-listing.md`
- [x] Add "Suggest a Feature" link in popup → points to GitHub Issues
- [x] Update homepage_url to wayknow.tech/cookieclear.html
- [x] Align directory structure with ClearJSON/SnapMark (promo/ + screenshots/ + docs/)

### After Launch
- [ ] Monitor GitHub Issues for user feedback
- [ ] Track install count and retention
- [ ] If installs > 5,000: analyze feature requests for monetization opportunities
- [x] Cross-promote ClearJSON and SnapMark in the extension

### Feature Ideas (Not Prioritized — Wait for User Feedback)

| Feature | Demand Signal |
|---------|---------------|
| Cookie profiles (save/restore sets) | Paid feature in proprietary editors; wait for user requests |
| Scheduled auto-cleanup | Paid feature in proprietary editors; wait for user requests |
| CSV/Puppeteer export | QA user requests |
| Set-Cookie interceptor | Unvalidated idea; wait for user interest |
| Bulk edit | Wait for user requests |
| JWT decoder | Common free feature in other editors |

### Known Limitations

| Issue | Impact | Plan |
|-------|--------|------|
| Undo is per-session only | Resets when popup closes | Acceptable for MVP; persist later if needed |
| No i18n | English only | Add if non-English users request it |

---

## Decision Log

| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-07-06 | **Free only, no Pro tier** | Market research: no validated paid demand in cookie editor category. CookieClear's role is acquisition for ClearJSON/SnapMark. |
| 2026-07-06 | **Vanilla JS, no framework** | Extension size < 85KB achieved. No build step needed. |
| 2026-07-06 | **MIT License** | Trust foundation — open source code is auditable by anyone. |
| 2026-07-06 | **Bundled tracking list** | Offline classification. Zero network requests — verifiable by anyone. |
| 2026-07-06 | **Domain whitelist + undo** | User research: these features are frequently requested. Low dev cost, high differentiation. |
| 2026-07-07 | **Remove competitor names from metadata** | CWS rejected first submission for keyword spam. All competitor references removed from store listing, README, website, and public docs. |

---

## Related Documents

- [PRODUCT.md](PRODUCT.md) — Full product specification, market context, competitive analysis
- [README.md](README.md) — Quick start and user-facing documentation
- [LICENSE](LICENSE) — MIT
