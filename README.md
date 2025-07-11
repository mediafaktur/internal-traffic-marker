# Internal Traffic Marker

A lightweight browser extension that marks internal traffic by automatically appending a query parameter (e.g. `?internal=true`) to specific domain URLs. Designed to help organizations reliably filter internal visits in analytics tools like Google Analytics 4 (GA4).

## Problem Solved

In many organizations, internal staff frequently access the company website for testing or research. These visits can distort analytics data if not properly filtered. Traditional IP-based filters are ineffective when team members work from home or use dynamic IP addresses.

This extension solves that problem by ensuring that all requests to specified domains include a custom query parameter (e.g. `?internal=true`). This allows simple and reliable filtering of internal traffic in GA4.

Unlike JavaScript-based solutions, this extension uses **declarative rules** provided by modern browser APIs. This has two major advantages:

- **No reloads or redirects**: The parameter is appended before the request is sent, ensuring a seamless user experience without visible flickering or network hits.
- **100% reliable from first page view**: The tracking parameter is available immediately—even on the initial visit—making it ideal for pageview-based filtering.

## Key Features

- Zero-flicker query parameter injection
- Works from the **first page load**
- Uses browser-native `declarativeNetRequest` API
- Configurable list of domains and parameter key
- No cookies, storage or client-side scripts
- Manual installation – no store required
- Works in Chrome, Edge, Firefox

## Components

```text
extension/
├── manifest.json         # Extension metadata and permissions
├── rules.json            # List of domains and parameters to apply
└── icons/
    └── icon128.png       # Toolbar icon

```

## Installation

### 1. Customize Configuration

Before installing, open both `manifest.json` and `rules.json`:

- In `manifest.json`, edit the `host_permissions` array to include your actual domain(s) *
- In `rules.json`, modify the `urlFilter` value to match a domain. To apply the redirect to multiple domains, simply duplicate the rule object for each domain and adjust the urlFilter value accordingly.
- Optionally, change the query parameter (default: `?internal=true`)

Placeholder: The files use `example.com` as a dummy domain.  
Make sure to replace this with your real website(s) before installing.

> If you intend to use the extension in Firefox and plan to sign and distribute it using your own Firefox Developer Hub account, you must replace the default id inside the `browser_specific_settings` object with a unique value, such as internal-traffic-marker@yourcompany.com.

### 2. Install in Chrome or Edge

1. Open `chrome://extensions/` (or `edge://extensions/`)
2. Enable **Developer mode**
3. Click **Load unpacked**
4. Select the folder containing the customized `manifest.json` and `rules.json` files

No signing is required. The extension will work locally without a store upload.

### 3. Install in Firefox (Permanent Installation Recommended)

To install the extension permanently and securely in Firefox:

1. Go to [https://addons.mozilla.org/de/developers/](https://addons.mozilla.org/de/developers/)
2. Sign in or create a Firefox Developer account
3. Select **Submit a New Add-on**
4. Choose **Self-distribution**
5. Upload a ZIP of your extension folder (with customized domains)
6. Once reviewed and signed by Mozilla, download the signed `.xpi` file
7. Install the `.xpi` in Firefox (double-click or drag into the browser)

ℹ️ **You can also temporarily test the extension before signing:**
- Open `about:debugging#/runtime/this-firefox`
- Click **Load Temporary Add-on**
- Select your `manifest.json` file
- ⚠️ This version will be removed when Firefox is restarted

## License

MIT – see [LICENSE](./LICENSE)

## Author

**/ MEDIAFAKTUR – Marketing Performance Precision**  
[https://mediafaktur.marketing](https://mediafaktur.marketing)  

**Florian Pankarter**  
[fp@mediafaktur.marketing](mailto:fp@mediafaktur.marketing)