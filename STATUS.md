# CookieClear — Project Status

> Last updated: 2026-07-20（**本项目已被 CrumbKit 取代**。申诉已回复：spam 屏蔽解除，但要求移除未使用的 `tabs` 权限。已修复推送到仓库，但不再继续提交此 item —— 改用 CrumbKit 全新品牌。）

---

## Current State: Blocked — Appeal Submitted ⏳

The item was hard-blocked by CWS ("uncorrectable violation — resubmission disabled, appeal only")
under the Spam / Store Ranking policy (notification ID: Yellow Nickel) for keyword spam.

**Root cause of the block:** repeated keyword-spam trigger. The first rejection was for
competitor names in the store text. A pre-resubmit audit (2026-07-09) then found a *residual*
competitor name baked into the **marquee promo tile** (`promo/generate.js` → `marquee-tile.png`
said "The safe EditThisCookie replacement") — the earlier cleanup missed the tile generator.

**Remediation (2026-07-09) — all store-visible assets verified competitor-name-free:**
- Description: WHY paragraph naming a competitor + "replacement" positioning removed.
- Title / short description / keywords: no competitor names.
- Promo tiles: `promo/generate.js` fixed, all 3 tiles regenerated.
- Screenshots: regenerated from clean source (byte-identical to committed → confirmed clean).
- Website (`wayknow`: cookieclear.html / privacy / terms): verified clean.
- Internal docs (PRODUCT.md, wayknow DECISIONS.md): competitor brand names sanitized.

**Appeal submitted 2026-07-09.** Reason: "action taken on my content was in error." Note stated
the cited violation is fully remediated and requested reinstatement. **Only one appeal per
violation** — awaiting verdict by email.

**Next:**
- If appeal succeeds → item unblocks → submit the saved clean draft (clean description already
  drafted in `docs/store-listing.md`; re-upload the 3 regenerated promo tiles).
- If appeal is denied → the appeal for this violation is exhausted; evaluate republishing under a
  fresh item ID with a clean listing.

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
| 2026-07-09 | **Fix residual competitor name in marquee tile** | Pre-resubmit audit found `promo/generate.js` still generated a marquee tile reading "The safe EditThisCookie replacement". Fixed generator, regenerated all 3 tiles, removed competitor-brand keyword table from PRODUCT.md. |
| 2026-07-09 | **Submit CWS appeal** | Item hard-blocked (resubmission disabled, appeal only) under Spam/Store Ranking policy. All store-visible assets verified competitor-name-free across both repos. Appealed with reason "action was in error" + remediation summary. One appeal per violation — awaiting verdict. |

---

## Related Documents

- [PRODUCT.md](PRODUCT.md) — Full product specification, market context, competitive analysis
- [README.md](README.md) — Quick start and user-facing documentation
- [LICENSE](LICENSE) — MIT

### Appeal Response (2026-07-17)

- **Result:** Appeal reviewed — spam block lifted. New issue: `tabs` permission is not required
- **Fix:** Removed `tabs` from manifest permissions (redundant with `activeTab` for the single `chrome.tabs.query({ active: true })` call)
- **Next:** Resubmit with fixed manifest
