# BNotify – Bengali Notification Transliterator & Transmitter

<p align="center">
  <img src="assets/logo.png" alt="BNotify Logo" width="180"/>
</p>

<p align="center">
  <strong>Make your Bangla notifications readable on any smartwatch.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Android-App-green?logo=android" alt="Android App"/>
  <img src="https://img.shields.io/badge/Version-1.21-blue" alt="Version 1.21"/>
  <img src="https://img.shields.io/badge/Language-Bangla%20%7C%20English-orange" alt="Languages"/>
</p>

BNotify is an Android application designed to overcome Bengali notification compatibility limitations on smartwatches and smart bands that cannot properly display Bangla (Bengali Unicode) characters.

It intercepts notifications from selected applications, converts Bengali text into readable Bangla written in Latin script (Romanized Bangla / Avro phonetic), and retransmits the processed notifications through Android's notification system.

The result? Read your Bangla messages on devices that otherwise display broken characters, empty boxes, or unsupported glyphs.

**Creator / Idea:** xelsk  
**AI Assistance:** Made with help from Google Gemini  

---

## Table of Contents

- [The Problem](#the-problem)
- [The Solution](#the-solution)
- [Use Cases](#use-cases)
- [How It Works](#how-it-works)
- [Features](#features)
- [What's New in v1.21](#whats-new-in-v121)
- [Getting Started](#getting-started)
- [First Launch & Permission Setup](#first-launch--permission-setup)
- [User Guide](#user-guide)
- [Transliteration Modes](#transliteration-modes)
- [Custom Dictionary](#custom-dictionary)
- [Privacy & Security](#privacy--security)
- [Troubleshooting](#troubleshooting)
- [Limitations](#limitations)
- [Contributing](#contributing)
- [Acknowledgements](#acknowledgements)

---

## The Problem

Many budget and mid-range smartwatches and smart bands have limited font and character support.

While they can receive notifications in English and other supported languages, Bengali notifications may not render correctly.

Common problems include:

- Bengali characters appearing as empty squares (`□`).
- Missing or broken characters.
- Incomplete or unreadable notification messages.
- Lack of Bengali language support in the manufacturer's firmware.
- No practical way to install additional fonts or modify the watch firmware.

This is particularly frustrating for Bengali-speaking users who rely on their smartwatch for everyday notifications.

## The Solution

BNotify acts as a bridge between your Android smartphone and your smartwatch.

Instead of sending the original Bengali notification to your watch, BNotify creates a new notification containing its Romanized Bangla equivalent.

| Original Notification | BNotify Notification |
|---|---|
| তুমি কেমন আছো? | Tumi kemon acho? |
| আমি বাসায় আছি। | Ami bashay achi. |
| তোমাকে ধন্যবাদ। | Tomake dhonnobad. |
| বাংলাদেশ আমার দেশ। | Bangladesh amar desh. |

Since the converted text uses standard Latin characters, it can be displayed on virtually any smartwatch that supports ordinary English notifications.

**No custom watch firmware or font installation is required.**

---

## Use Cases

BNotify is useful for anyone who receives Bengali notifications on a wearable device with inadequate Bangla character support.

### 1. Reading Bangla WhatsApp Messages

**Original:**

> আজকে কখন আসবে? তোমার জন্য অপেক্ষা করছি।

**On your smartwatch:**

> [WhatsApp] Ajke kokhon ashbe? Tomar jonno opekkha korchi.

### 2. Messenger and Social Media Notifications

Read messages and notifications from Facebook Messenger, Instagram and other supported applications without relying on Bengali font support.

### 3. SMS and Everyday Communication

Read personal messages, delivery updates, service notifications and other Bangla SMS messages directly from your wrist.

### 4. Smartwatch Compatibility Workaround

Useful for devices whose firmware does not support Bengali, including potentially affected models from:

- Xiaomi / Redmi
- Haylou
- Amazfit
- Huawei
- Other generic Android-compatible smart bands and watches

Compatibility depends on the companion application and the watch's notification implementation.

### 5. Mixed Bangla-English Conversations

BNotify is intended to make Bengali messages readable while retaining useful Latin-script content, such as English words, numbers and symbols.

---

## How It Works

BNotify uses Android's Notification Listener Service to receive notifications from applications selected by the user.

The notification text is processed locally through the transliteration engine and then retransmitted as a new Android notification.

```text
       Original App
  (WhatsApp / Messenger / SMS)
              |
              v
   Android Notification System
              |
              v
   BNotify Notification Listener
              |
              v
      Transliteration Engine
              |
       +------+------+
       |             |
       v             v
   Auto Mode     Direct Mode
       |             |
   Dictionary     Avro Rules
       |
   Avro Fallback
       |
       +-------------+
              |
              v
    Processed Notification
      [WhatsApp] Message
              |
              v
     Android Notification
              |
              v
      Companion Application
              |
              v
          Smartwatch
```

The smartwatch receives an ordinary Latin-script notification instead of the original Bengali text.

---

## Features

### 1. Two Transliteration Modes

Choose between high-performance in-memory dictionary-assisted transliteration and direct Avro phonetic conversion.

### 2. Offline Transliteration

The core transliteration process works locally on your Android device. No cloud-based translation service is needed.

### 3. Custom Dictionary Support & GitHub Gist Integration

Use the built-in dictionary or import your own custom dictionary from a GitHub Gist or raw file URL with non-blocking timeouts.

### 4. Selective Application Support

Choose exactly which applications BNotify should monitor and retransmit notifications from.

### 5. Application Identification

Notifications include the originating application name.

Example:

`[WhatsApp] Amar ajke deri hobe.`

### 6. Notification Aggregation (Spam Debouncer)

An optional debouncing feature helps prevent excessive notifications when multiple messages arrive rapidly from the same chat.

### 7. Modern Pixel-Inspired Material 3 Interface

A Pixel-inspired interface with bottom navigation:

- Dashboard
- Apps
- Settings
- About

### 8. Theme Customization

Choose between:

- System default
- Light mode
- Dark mode

### 9. Notification Content Preservation

The transliteration workflow is designed to retain non-Bengali content and make mixed-script notifications readable.

---

## What's New in v1.21

**BNotify v1.21 introduces major performance and reliability optimizations:**

### 1. High-Performance In-Memory Dictionary (`O(1)`)
- All 60,000+ dictionary entries are loaded instantly into an optimized in-memory hash map upon startup.
- Guarantees absolute dictionary priority over phonetic rules with zero database lag.

### 2. NFC Unicode Normalization & Punctuation Stripping
- Automatically normalizes Bengali characters (NFC form) and strips attached punctuation (`।`, `,`, `?`, `!`, `;`) during lookups for flawless word matching.

### 3. Secure GitHub Gist Pulling
- Added strict connection timeouts and non-blocking background coroutines for Gist dictionary pulling.
- Hardened with input sanitization guards against RCE/injection.

### 4. Spam Debouncing
- Added an optional notification aggregator setting to debounce rapid messages from the same chat.

---

## Getting Started

### Requirements

- An Android smartphone (Marshmallow / API 23+).
- A compatible smartwatch or smart band.
- The manufacturer's companion application installed and configured.
- Notification access enabled for BNotify.
- Permission to post notifications.
- Background activity permitted by Android.

### Installation

1. Download and install the latest available BNotify APK.
2. Open BNotify.
3. Complete the initial permission setup.
4. Configure your preferred applications and transliteration settings.

---

## First Launch & Permission Setup

**BNotify requires three important permissions/settings to function correctly.**

During the first launch, make sure you complete all three steps.

### Step 1 – Allow Notification Access

BNotify needs notification access to receive notifications from your selected applications.

1. Open BNotify.
2. When prompted, navigate to Android's Notification Access settings.
3. Find **BNotify** in the application list.
4. Enable Notification Access.
5. Confirm the permission request.

This allows BNotify to listen to notifications generated by other applications.

### Step 2 – Allow BNotify to Send Notifications

BNotify needs permission to publish its own notifications containing the converted text.

1. Open the **Settings** tab in BNotify.
2. Find the notification permission option.
3. Tap it to open the relevant Android settings.
4. Allow BNotify to send/post notifications.

This permission is separate from Notification Access.

Without it, BNotify may be able to receive and process notifications but cannot properly publish the converted notifications.

### Step 3 – Allow Background Activity

BNotify needs to remain active in the background to process incoming notifications reliably.

1. Open the **Settings** tab in BNotify.
2. Find the Background Activity option.
3. Open the relevant Android settings.
4. Allow background activity or unrestricted battery usage, depending on your device.

Depending on your smartphone manufacturer, you may also need to:

- Set battery usage to **Unrestricted** or **Don't Optimize**.
- Allow background activity.
- Enable auto-start or background launch, if available.
- Avoid manually force-stopping the application.

### Important – Restricted Settings on Newer Android Versions

Some newer Android versions may restrict notification access for applications installed from outside Google Play or other unverified sources.

If Android prevents you from enabling Notification Access, you may need to manually allow restricted settings.

Follow these steps:

1. Open your phone's **Settings**.
2. Navigate to **Apps → BNotify → App Info**.
3. Tap the **three-dot menu (⋮)** in the upper-right corner.
4. Look for **Allow restricted settings**.
5. Enable it and confirm if prompted.
6. Return to Notification Access settings.
7. Enable Notification Access for BNotify.

The exact menu names and availability may vary depending on your Android version and smartphone manufacturer.

**Note:** Only allow restricted settings for applications you trust.

---

## User Guide

After completing the initial permission setup, follow these steps to configure BNotify.

### Step 1 – Install BNotify

Install the application on your primary Android smartphone (the phone paired with your smartwatch).

Open BNotify after installation.

### Step 2 – Enable BNotify in Your Watch Companion App

Open your smartwatch's official companion application.

Navigate to its notification management settings and enable notifications for **BNotify**.

For example, depending on your wearable:

- Mi Fitness
- Zepp
- Huawei Health
- Haylou Fun
- Other manufacturer companion applications

**Recommended:** Consider disabling notifications from the original messaging applications in the companion app if you want to avoid receiving both the original and converted notifications.

Keep the original applications enabled on your smartphone itself. Only adjust their notification forwarding settings in the watch companion application.

### Step 3 – Select Applications in BNotify

Open the **Apps** tab in BNotify.

Select the applications whose notifications you want BNotify to process.

For example:

- WhatsApp
- Messenger
- Facebook
- Instagram
- Messages
- Telegram

Only enable the applications you actually need.

### Step 4 – Choose Your Transliteration Mode

Open Settings and select your preferred transliteration mode.

- **Auto:** High-performance dictionary lookup followed by Avro phonetic fallback.
- **Direct Phonetics:** Avro phonetic conversion without dictionary lookup.

You can also configure the notification aggregation option and other available settings.

### Step 5 – Test Your Smartwatch

Send yourself a Bengali message from another device.

You should receive a new notification containing the Romanized Bangla text on your smartwatch.

**You're ready to go!**

---

## Transliteration Modes

BNotify currently provides two operating modes.

### Auto – Dictionary First, Phonetics Second

This mode prioritizes dictionary-based accuracy.

Processing:

1. Check the built-in 60k+ in-memory dictionary or selected custom dictionary.
2. Use the corresponding Latin-script entry when a dictionary match is available.
3. Fall back to the Avro phonetic engine for unlisted words.

This approach allows frequently used words and words with preferred conventional spellings to be handled through dictionary entries, while still providing coverage for words that are not included.

**Recommended for everyday use.**

### Direct Phonetics – Rules Only

This mode bypasses dictionary lookup entirely.

Every Bengali word is processed directly through the rule-based Avro phonetic engine.

This can be useful when you prefer phonetic consistency or want to compare the output against dictionary-assisted transliteration.

---

## Custom Dictionary

BNotify supports custom dictionaries, allowing users to improve transliteration accuracy and customize how particular Bengali words appear on their smartwatch.

You can use either:

1. The default 60k+ dictionary included with BNotify.
2. Your own custom dictionary hosted online.

### Importing a Custom Dictionary

1. Open **Settings**.
2. Navigate to **Custom Dictionary Settings**.
3. Select the custom dictionary option.
4. Paste the URL of your raw GitHub Gist or raw dictionary file.
5. Tap **Pull & Import from GitHub Gist**.
6. Wait for the import to complete.

Once imported, the dictionary can be used offline.

**Note:** Internet access is required for downloading a remote dictionary. The subsequent local transliteration process does not require an internet connection.

### Supported Formats

Both CSV and JSON formats are supported.

#### CSV Format

The CSV file must contain two columns:

- `bengali_word`
- `latin_phonetic`

Example:

```csv
bengali_word,latin_phonetic
বাংলা,bangla
বাংলাদেশ,bangladesh
ধন্যবাদ,dhonnobad
ভালোবাসা,bhalobasha
বন্ধু,bondhu
```

#### JSON Format

A simple key-value structure:

```json
{
  "বাংলা": "bangla",
  "বাংলাদেশ": "bangladesh",
  "ধন্যবাদ": "dhonnobad",
  "ভালোবাসা": "bhalobasha",
  "বন্ধু": "bondhu"
}
```

### Hosting Your Dictionary on GitHub Gist

1. Visit [GitHub Gist](https://gist.github.com/).
2. Create a new Gist.
3. Add your dictionary as a `.csv` or `.json` file.
4. Save the Gist.
5. Open the Raw version of the file.
6. Copy the raw URL.
7. Paste the URL into BNotify's custom dictionary settings.

You can also host a compatible raw CSV or JSON file elsewhere, provided the URL is publicly accessible and returns the raw file contents.

### Dictionary Recommendations

For better results:

- Prefer commonly accepted Bangladeshi Roman Bangla spellings.
- Maintain consistent spelling conventions.
- Use the same spelling for frequently occurring words.
- Include proper nouns and commonly used regional vocabulary.
- Check punctuation and character encoding.
- Use UTF-8 encoded files.
- Avoid duplicate Bengali entries with conflicting transliterations.

The dictionary is particularly useful for words whose conventional Roman Bangla spelling differs from the output generated by phonetic rules.

---

## Privacy & Security

BNotify is designed around local notification processing.

- Notification text is processed on the device.
- The core transliteration engine does not require cloud processing.
- Custom dictionaries can be imported and stored for offline use.
- Hardened with input sanitization guards against injection.
- No third-party translation service is required for everyday operation.

**Important:** Android notification access is a sensitive permission. BNotify needs this permission to perform its primary function. Users should only grant it to applications they trust.

Remote dictionary importing requires an internet connection and access to the selected dictionary URL.

---

## Troubleshooting

| Problem | Possible Solution |
|---|---|
| No notifications on the watch | Enable BNotify in the companion app |
| Original Bangla notification still appears | Disable original app forwarding in the companion app |
| BNotify stops working | Allow background activity and unrestricted battery usage |
| Notification Access cannot be enabled | Check App Info → Three-dot menu → Allow restricted settings |
| BNotify notifications are not appearing | Allow notification posting permission in BNotify Settings |
| Some applications are not processed | Check the Apps page and notification access |
| Notifications arrive inconsistently | Check battery optimization and background restrictions |
| Dictionary import fails | Verify the raw URL and CSV/JSON structure |
| Some words are transliterated incorrectly | Try Auto mode or improve the custom dictionary |
| Duplicate notifications appear | Review original app forwarding and notification aggregation settings |

---

## Limitations

- BNotify does not add Bengali font support to smartwatch firmware.
- The watch displays Romanized Bangla, not Bengali Unicode.
- Transliteration is not the same as translation; the original meaning and language are retained.
- Phonetic transliteration may differ from conventional spelling.
- Dictionary coverage depends on the quality and size of the dictionary.
- Notification behavior depends partly on Android, the manufacturer's companion application and the smartwatch firmware.
- Certain notification formats or rich-media content may not be fully reproduced.

---

## Contributing

Contributions that improve Bengali transliteration quality and smartwatch compatibility are welcome.

Potential areas of contribution include:

- Improving the Avro phonetic engine.
- Expanding the Bengali–Roman Bangla dictionary.
- Adding conventional and regional vocabulary.
- Improving notification handling.
- Testing on different smartwatch models.
- Reporting bugs and suggesting improvements.

If you encounter an issue, please provide:

- Android phone model.
- Android version.
- Smartwatch or smart band model.
- Companion application name.
- BNotify transliteration mode.
- A sample of the original and resulting notification (remove any personal information).

---

## Acknowledgements

Special thanks to the tools and communities that helped make BNotify possible.

- **Avro Phonetic:** For the phonetic transliteration approach.
- **Android:** Notification Listener and notification infrastructure.
- **Open-source community:** For tools, ideas and inspiration.

### AI Assistance

BNotify was developed with assistance from AI tools:

<p align="center">
  <a href="https://gemini.google.com/">
    <img src="https://img.shields.io/badge/Google%20Gemini-AI%20Assistance-8E75B2?logo=googlegemini&logoColor=white" alt="Google Gemini"/>
  </a>
  <a href="https://chatgpt.com/">
    <img src="https://img.shields.io/badge/ChatGPT-AI%20Assistance-10A37F?logo=openai&logoColor=white" alt="ChatGPT"/>
  </a>
  <a href="https://duck.ai/">
    <img src="https://img.shields.io/badge/Duck.ai-AI%20Assistance-DE5833?logo=duckduckgo&logoColor=white" alt="Duck.ai"/>
  </a>
</p>

---

<p align="center">
  <strong>BNotify – Bringing Bangla notifications to your wrist, one message at a time.</strong>
</p>

<p align="center">
  Made with ❤️ and a little help from AI.
</p>
