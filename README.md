# BNotify - Bengali Notification Transliterater & Transmitter

**Creator / Idea**: xelsk  
**AI Assistance**: Made with help from Gemini  

BNotify is an advanced offline Android service and application that intercepts incoming system notifications from selected apps, processes them according to your chosen transliteration mode, prefixes the app source (e.g., `[WhatsApp]`), and re-posts them in Bangla-Latin (Avro phonetic) script.

---

## Architecture & Transliteration Modes

BNotify offers two core operating modes:
1. **Auto (Dictionary then Phonetics)**: Primary high-accuracy dictionary lookup (`dictionary.csv` shipped in assets), falling back dynamically to the rule-based **Avro Phonetic Engine** for unlisted words.
2. **Direct Phonetics (Rules Only)**: Bypasses dictionary lookup entirely and applies the Avro rule-based phonetic engine directly.

---

## Custom Dictionary & GitHub Gist Integration

BNotify comes pre-shipped with a starter dictionary in `app/src/main/assets/dictionary.csv`. You can switch between the default shipped dictionary and your own custom dictionary in **Settings** -> **Custom Dictionary Settings**.

### Pulling from GitHub Gist
You can publish your custom dictionary as a raw GitHub Gist (`.csv` or `.json`), paste the raw URL directly into the app, and tap **"Pull & Import from GitHub Gist"** to download and apply it offline.

### Dictionary CSV Structure & Headings
```csv
bengali_word,latin_phonetic
বাংলা,bangla
বাংলাদেশ,bangladesh
ধন্যবাদ,dhonnobad
```

### Dictionary JSON Structure
```json
{
  "বাংলা": "bangla",
  "বাংলাদেশ": "bangladesh",
  "ধন্যবাদ": "dhonnobad"
}
```

---

## Key Features

1. **Modern Pixel-Inspired UI with Bottom Navigation**: Clean Material 3 dashboard, app selector, settings, and about tabs docked with a bottom navigation bar.
2. **Theme Mode Selection**: Supports **System**, **Light**, and **Dark** modes.
3. **No Notification Skips**: Transmits and processes all notifications from enabled apps regardless of script.
4. **App Source Identifier**: Automatically prefixes notifications with `[App Name]` (e.g., `[WhatsApp] ...`).
5. **Notification Aggregation (Spam Debouncer)**: Optional setting to debounce and aggregate rapid messages from the same chat (e.g. preventing 10 messages from 3 chats from spamming).
6. **Offline Security Hardened**: Input sanitization guards against script/RCE injection during custom dictionary imports while remaining 100% offline (zero internet permission required for notification processing).
