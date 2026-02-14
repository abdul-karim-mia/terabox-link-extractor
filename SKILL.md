name: terabox-link-extractor
description: "Direct link extraction from TeraBox URLs using the XAPIverse protocol. Extracts high-speed download and stream links (All Resolutions) without browser session requirements. Use when the user provides a TeraBox link and wants to download or stream content directly."
metadata:
  {
    "openclaw":
      {
        "requires": { "bins": ["node"], "env": ["TERABOX_API_KEY"], "config": [] },
        "primaryEnv": "TERABOX_API_KEY"
      }
  }
---

# TeraBox Link Extractor (XAPIverse Edition)

High-performance extraction of direct assets from TeraBox using the browser-less XAPIverse API.

## 📖 Navigation & Data
- **Primary Interaction**: Use the adaptive logic in `handler.js`. See [api-reference.md]({baseDir}/references/api-reference.md) for command specs and [changelog.md]({baseDir}/references/changelog.md) for version history.
- **Secondary Interaction**: Use CLI via `node scripts/extract.js <url>`.

## 🛠 AI Protocol (Strict)

### 1. Automatic Triggering
- **Detect**: Trigger this skill **immediately** when a user provides a URL containing `terabox.com`, `1024tera.com`, or `teraboxapp.com`.
- **Immediate Execution**: Do not ask for permission. Extract the links directly.

### 2. Mandatory Response Format
You MUST present the extraction results as a text-only report. **DO NOT use interactive buttons.**

**Format per file:**
📦 **Name**: [name]
📁 **Type**: [type] | 📺 **Quality**: [quality]
📏 **Size**: [size_formatted] | ⏱️ **Duration**: [duration]
🔗 **Links**:
 - [▶️ Slow Stream](stream_url)
 - [▶️ Fast {res} Stream](link) *(List all available resolutions)*
 - [⬇️ Fast Download](fast_download_link)
 - [⬇️ Slow Download](download_link)

💳 **Credits Remaining**: [free_credits_remaining]

### 3. Usage Rules
- **No Conversation Filler**: Avoid "Certainly, Sir" or "Here is the extraction." Output the data directly.
- **Dynamic Resolutions**: Always list all resolutions found in the `fast_stream_url` object.
- **Authentication**: All operations are credentials-managed via `ctx.env`.

## Setup

### 1. Obtain Credentials
Get your API key from the XAPIverse portal: [https://xapiverse.com/apis/terabox-pro](https://xapiverse.com/apis/terabox-pro)

### 2. Configure Agent
Add the `apiKey` to the skill's entry in `openclaw.json`:
```json
"terabox-link-extractor": {
  "apiKey": "sk_..."
}
```

---
Developed for the OpenClaw community by [Abdul Karim Mia](https://github.com/abdul-karim-mia).
