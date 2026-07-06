# CookieClear

> A privacy-first cookie editor for Chrome. Open source, zero tracking, no ads.

CookieClear is a Manifest V3 Chrome extension that lets you view, edit, import, export, and manage browser cookies. It's designed to be the trustworthy replacement for EditThisCookie (removed from Chrome Web Store, 3M+ users) and Cookie-Editor (unmaintained since Feb 2024).

## Why CookieClear

- **Reliable import/export** — JSON, Netscape, and cURL formats that actually work (unlike broken alternatives)
- **Zero tracking** — no analytics, no telemetry, no external requests. All data stays on your device.
- **No ads** — unlike competitors that inject ads into your cookie editor
- **MIT licensed** — fully open source, auditable code
- **Fast UI** — no animations, no bloat, just the classic EditThisCookie experience in a modern MV3 package

## Features

- View all cookies for the current site with name, value, domain, path, expiry
- Create, edit, and delete individual cookies
- Search and filter cookies in real-time
- Batch delete all cookies (with domain whitelist protection)
- Export to JSON, Netscape (curl/wget), and cURL formats
- Import from JSON and Netscape formats
- Undo support for accidental deletions
- Privacy score for every site you visit
- Dark/light mode toggle
- Domain whitelist to protect important cookies

## Installation (Development)

1. Clone the repository:
   ```bash
   git clone https://github.com/cookieclear/cookieclear.git
   cd cookieclear
   ```

2. Open Chrome and navigate to `chrome://extensions`

3. Enable "Developer mode" (toggle in top-right corner)

4. Click "Load unpacked" and select the `cookieclear` folder

5. Pin CookieClear to your toolbar for quick access

## Usage

1. Navigate to any website
2. Click the CookieClear icon in your toolbar
3. View, edit, or delete cookies for that site
4. Use the export dropdown to save cookies in your preferred format
5. Import cookies from a file to restore sessions or transfer between environments

## Tech Stack

- Vanilla JavaScript (ES2020+)
- Chrome Extensions Manifest V3
- `chrome.cookies` API
- `chrome.storage.local` for settings and whitelist
- Zero dependencies, zero build tools

## Project Structure

```
cookieclear/
├── manifest.json                 # MV3 manifest
├── src/
│   ├── popup/                    # Extension popup UI
│   │   ├── popup.html
│   │   ├── popup.css
│   │   └── popup.js
│   ├── options/                  # Settings page
│   │   ├── options.html
│   │   ├── options.css
│   │   └── options.js
│   ├── utils/                    # Core modules
│   │   ├── cookies.js            # chrome.cookies wrapper
│   │   ├── export.js             # JSON / Netscape / cURL export
│   │   ├── import.js             # JSON / Netscape import
│   │   ├── classify.js           # Cookie classification & privacy score
│   │   ├── undo.js               # Undo/redo stack
│   │   └── storage.js            # chrome.storage.local wrapper
│   └── background/
│       └── service-worker.js
├── data/
│   └── tracking-domains.json     # Disconnect.me tracker list
├── icons/
└── LICENSE
```

## Privacy

CookieClear never:
- Collects any data
- Makes any network requests
- Uses any analytics or telemetry
- Injects any ads or tracking
- Shares your cookies with anyone

All processing happens locally on your device. You can verify this by inspecting the source code or monitoring the Network tab in Chrome DevTools while using the extension.

## License

MIT — see [LICENSE](LICENSE)

## Related Projects

- [ClearJSON](https://github.com/wayknow/clearjson) — A trustworthy JSON viewer
- [SnapMark](https://github.com/wayknow/snapmark) — Privacy-first screenshot & annotation tool
