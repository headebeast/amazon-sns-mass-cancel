# 🛒 Amazon Subscribe & Save Mass Cancel

> Bulk cancel all your Amazon Subscribe & Save subscriptions in one click.

![Chrome Extension](https://img.shields.io/badge/Chrome-Extension-green?logo=googlechrome)
![Manifest V3](https://img.shields.io/badge/Manifest-V3-blue)
![License](https://img.shields.io/badge/License-Proprietary-red)

## The Problem

Amazon Subscribe & Save is great for discounts, but managing dozens of subscriptions is tedious. Canceling them one-by-one takes forever, especially if you only wanted the discount and not the recurring delivery.

**This extension fixes that** — cancel all your subscriptions with a single click.

## ✨ Features

- 🚀 **One-Click Mass Cancel** — Cancel all subscriptions at once
- 📊 **Real-Time Progress** — Watch the progress bar as each item is canceled
- ⚡ **Direct API Calls** — No popup spam, no new tabs
- 🛡️ **Rate Limit Protection** — Built-in delays to avoid Amazon blocks
- 📝 **Error Reporting** — See exactly which items failed (if any)

## 📦 Installation

### From Source (Developer Mode)

1. **Download** this repository (click `Code` → `Download ZIP`, or clone it)
2. **Unzip** if needed
3. Open Chrome and go to `chrome://extensions/`
4. Enable **Developer mode** (toggle in top-right corner)
5. Click **Load unpacked**
6. Select the `amazon-sns-mass-cancel` folder

The extension icon will appear in your Chrome toolbar.

## 🚀 Usage

1. **Navigate** to your [Subscribe & Save page](https://www.amazon.com/auto-deliveries/subscriptionList?listFilter=active)
2. **Scroll down** and click "Show more subscriptions" until all items are visible
3. **Click** the extension icon in your toolbar
4. **Click "Scan Page"** to detect all subscriptions
5. **Click "Cancel All"** to cancel them

That's it! Watch the progress bar as each subscription is canceled.

## 📸 Screenshot

<p align="center">
  <img src="screenshots/progress.png" alt="Extension in action - canceling 66 subscriptions" width="320">
</p>

*The extension showing real-time progress while canceling 66 subscriptions*

## ⚠️ Important Notes

- **Emails**: Amazon sends a confirmation email for each canceled subscription. Expect inbox activity.
- **Irreversible**: Cancellations cannot be undone. You'll need to re-subscribe manually if needed.
- **US Only**: Currently only works on `amazon.com` (US site).

## 🛠️ Technical Details

### How It Works

1. **Extraction**: The extension scrapes subscription IDs from the page DOM using multiple fallback methods
2. **Cancellation**: Makes direct `fetch()` calls to Amazon's internal cancellation API endpoint
3. **Rate Limiting**: 500ms delay between requests to avoid triggering Amazon's bot detection

### API Endpoint Used

```
GET https://www.amazon.com/auto-deliveries/ajax/cancelSubscriptionAction
  ?actionType=cancelSubscription
  &canceledNextDeliveryDate={timestamp}
  &subscriptionId={id}
```

### Project Structure

```
amazon-sns-mass-cancel/
├── manifest.json          # Chrome extension manifest (V3)
├── popup/
│   ├── popup.html         # Extension popup UI
│   ├── popup.css          # Dark theme styling
│   └── popup.js           # Main cancellation logic
├── content/
│   └── extractor.js       # Content script for page detection
└── icons/
    ├── icon16.png
    ├── icon48.png
    └── icon128.png
```

## 🤝 Contributing

Contributions are welcome! Feel free to:

- 🐛 Report bugs
- 💡 Suggest features
- 🔧 Submit pull requests

## 📄 License

**All Rights Reserved** — Personal use only. See [LICENSE](LICENSE) for details.

---

**Disclaimer**: This is an unofficial tool and is not affiliated with Amazon. Use at your own risk.
