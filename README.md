# TikTok Media Downloader & Injector

<div align="center">

![Version](https://img.shields.io/badge/version-2.0-blue?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)
![Platform](https://img.shields.io/badge/platform-Web%20%7C%20Mobile-lightgrey?style=for-the-badge)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

**A complete web-based toolkit for downloading TikTok videos, extracting high-quality images, parsing JSON metadata, and injecting custom data**

[Features](#features) • [Quick Start](#quick-start) • [Usage Guide](#usage-guide) • [API Reference](#api-reference) • [FAQ](#faq)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Quick Start](#quick-start)
- [Usage Guide](#usage-guide)
- [API Endpoints](#api-endpoints)
- [File Structure](#file-structure)
- [Browser Compatibility](#browser-compatibility)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [License](#license)

---

## 🎯 Overview

The **TikTok Media Downloader & Injector** is a standalone HTML/JavaScript application that provides a professional interface for interacting with TikTok content. No installation required - simply open the HTML file in any modern browser!

### Why Use This Tool?

| Feature | Benefit |
|---------|---------|
| **No Installation** | Just open the HTML file in your browser |
| **No API Key Required** | Uses free public APIs |
| **Cross-Platform** | Works on Windows, Mac, Linux, iOS, Android |
| **Privacy Focused** | All processing happens in your browser |
| **Completely Free** | No hidden costs or premium tiers |

---

## ✨ Features

### 📥 **Video Downloader**
- Download TikTok videos in MP4 format
- Extract audio as high-quality MP3
- Smart URL detection
- Download queue management

### 📸 **Image Extractor**
- Extract all images from TikTok photo posts
- Support for carousel/multiple images
- High-resolution original quality
- Bulk download capability
- Gallery view with thumbnails

### 📄 **JSON Parser**
- Fetch complete metadata from any TikTok post
- View creator information, statistics, and more
- Syntax-highlighted JSON display
- Copy to clipboard functionality

### 💉 **JSON Injector**
- Inject custom JSON data into TikTok metadata
- Merge original metadata with custom fields
- Timestamp tracking for injections
- Export combined JSON structure

### 📦 **Batch Downloader**
- Process multiple URLs simultaneously
- Configurable options (video, audio, JSON)
- Progress tracking for each item
- Summary report of successful/failed downloads

---

## 🚀 Quick Start

### Installation (Zero Setup!)

```bash
# Step 1: Download the HTML file
# Save the complete HTML code as "tiktok-downloader.html"

# Step 2: Open in browser
# Double-click the file or open with any modern browser

# Step 3: Start using!
# Paste a TikTok URL and click download
```

### System Requirements

| Requirement | Minimum | Recommended |
|-------------|---------|-------------|
| **Browser** | Chrome 80+, Firefox 75+, Safari 13+ | Latest version |
| **RAM** | 512 MB | 2 GB |
| **Internet** | Broadband connection | Fiber optic |
| **JavaScript** | Enabled | Enabled |

---

## 📖 Usage Guide

### 1. Downloading Videos

```javascript
// Step-by-step:
1. Navigate to the "Downloader" tab
2. Paste your TikTok video URL in the input field
3. Click "Download Video" or "Download Audio Only"
4. Wait for the download to complete
5. File saves automatically to your Downloads folder
```

**Supported URL Formats:**
```
https://www.tiktok.com/@username/video/1234567890123456789
https://vm.tiktok.com/XXXXXX/
https://www.tiktok.com/t/XXXXXX/
```

### 2. Extracting Images from Photo Posts

```javascript
// Step-by-step:
1. Go to the "Image Extractor" tab
2. Paste a TikTok photo post URL
3. Click "Extract Images"
4. View the gallery of extracted images
5. Click individual images or "Download All"
```

**Photo Post URLs:**
```
https://www.tiktok.com/@username/photo/1234567890123456789
```

### 3. Parsing JSON Metadata

```javascript
// Step-by-step:
1. Switch to the "JSON Parser" tab
2. Enter any TikTok URL (video or photo)
3. Click "Fetch Metadata"
4. View the formatted JSON response
5. Copy or analyze the data structure
```

**Metadata Includes:**
- Video/Photo information
- Creator details
- Statistics (views, likes, comments, shares)
- Music information
- Thumbnail URLs

### 4. Injecting Custom JSON

```json
// Example custom JSON to inject:
{
  "custom_tags": ["viral", "trending", "2024"],
  "personal_notes": "This content is amazing!",
  "rating": 5,
  "categories": ["entertainment", "music", "dance"],
  "my_metadata": {
    "saved_date": "2024-01-15",
    "collection": "favorites"
  }
}

// Steps:
1. Go to "JSON Injector" tab
2. (Optional) Enter a TikTok URL for base metadata
3. Paste your custom JSON
4. Click "Inject JSON"
5. Download the merged result
```

### 5. Batch Processing

```
# Example batch file content (one URL per line):
https://www.tiktok.com/@user1/video/1234567890
https://www.tiktok.com/@user2/photo/9876543210
https://www.tiktok.com/@user3/video/5555555555
https://www.tiktok.com/@user4/video/1111111111

// Options:
✓ Download Videos     - Save MP4 files
□ Download Audio Only - Save MP3 files only
✓ Extract JSON        - Save metadata as JSON

// Steps:
1. Switch to "Batch Downloader" tab
2. Paste multiple URLs (one per line)
3. Select your options
4. Click "Start Batch Download"
5. Monitor progress and results
```

---

## 🔧 API Endpoints

### Primary API: TikWM

The application uses the [TikWM API](https://www.tikwm.com/) for all data fetching.

```javascript
// Base URL
const API_URL = 'https://www.tikwm.com/api/';

// Request format
GET ${API_URL}?url=${encodeURIComponent(tiktok_url)}

// Success Response Structure
{
  "code": 0,
  "msg": "success",
  "data": {
    // Video/Photo information
    "id": "string",
    "title": "string",
    "description": "string",
    "duration": number,
    "create_time": number,
    
    // Media URLs
    "play": "string (video URL)",
    "wmplay": "string (watermarked video)",
    "music": "string (audio URL)",
    "images": ["string"] (for photo posts),
    
    // Creator information
    "author": {
      "id": "string",
      "unique_id": "string",
      "nickname": "string",
      "avatar": "string",
      "signature": "string"
    },
    
    // Statistics
    "statistics": {
      "play_count": number,
      "digg_count": number,
      "comment_count": number,
      "share_count": number,
      "download_count": number
    },
    
    // Additional data
    "region": "string",
    "private_item": boolean,
    "duet_enabled": boolean,
    "stitch_enabled": boolean,
    "stickers_on_item": boolean
  }
}
```

### Error Response

```javascript
{
  "code": -1,
  "msg": "error message",
  "data": null
}
```

---

## 📁 File Structure

```
tiktok-downloader.html
├── <head>
│   ├── Meta tags
│   ├── CSS styles (embedded)
│   └── Font families
├── <body>
│   ├── Container div
│   │   ├── Header section
│   │   ├── Tab navigation (5 tabs)
│   │   ├── Downloader panel
│   │   ├── Image Extractor panel
│   │   ├── JSON Parser panel
│   │   ├── JSON Injector panel
│   │   └── Batch Downloader panel
│   └── Script section
│       ├── State management
│       ├── API handlers
│       ├── Download functions
│       ├── UI updates
│       └── Event listeners
└── Dependencies (none - self-contained)
```

---

## 🌐 Browser Compatibility

| Browser | Minimum Version | Status |
|---------|----------------|--------|
| Google Chrome | 80+ | ✅ Fully Supported |
| Mozilla Firefox | 75+ | ✅ Fully Supported |
| Safari | 13+ | ✅ Fully Supported |
| Microsoft Edge | 80+ | ✅ Fully Supported |
| Opera | 67+ | ✅ Fully Supported |
| Brave | 1.0+ | ✅ Fully Supported |
| Mobile Chrome | 80+ | ✅ Supported |
| Mobile Safari | 13+ | ✅ Supported |

**Required Browser Features:**
- JavaScript ES6+
- Fetch API
- Blob API
- LocalStorage
- ES6 Promises

---

## 🔍 Troubleshooting

### Common Issues and Solutions

| Issue | Possible Cause | Solution |
|-------|---------------|----------|
| **"Failed to fetch video info"** | Invalid URL or video removed | Verify URL works in browser |
| **CORS errors** | Browser security | Using proxy API (auto-handled) |
| **Download doesn't start** | Pop-up blocker | Allow pop-ups for this site |
| **Images not extracting** | Not a photo post | Ensure URL contains `/photo/` |
| **JSON parse error** | Invalid JSON format | Validate JSON using online tool |
| **Slow download speed** | Network congestion | Try again later or use different network |

### Debug Mode

Enable console logging for detailed debugging:

```javascript
// Open browser console (F12) and run:
localStorage.setItem('debug', 'true');
location.reload();

// To disable:
localStorage.removeItem('debug');
location.reload();
```

### Clearing Application Data

```javascript
// Clear all saved data:
localStorage.clear();

// Or use the "Clear Queue" button in the UI
```

---

## ❓ FAQ

### Q1: Is this tool free to use?
**A:** Yes, completely free! No hidden costs, no premium tiers.

### Q2: Do I need to install anything?
**A:** No installation required. Just save the HTML file and open it in any browser.

### Q3: Does this violate TikTok's terms of service?
**A:** This tool is for educational purposes. Always respect content creators' rights and TikTok's terms.

### Q4: Can I download videos without watermark?
**A:** Yes, the tool downloads videos without watermark when available.

### Q5: What's the maximum video length supported?
**A:** TikTok videos up to 10 minutes are supported.

### Q6: Can I download multiple videos at once?
**A:** Yes, use the Batch Downloader tab to process multiple URLs.

### Q7: Where are downloaded files saved?
**A:** Files save to your browser's default download location.

### Q8: Does this work on mobile devices?
**A:** Yes, the interface is responsive and works on iOS and Android browsers.

### Q9: Is my data private?
**A:** Yes, all processing happens in your browser. No data is sent to external servers except TikTok API calls.

### Q10: What happens if TikTok changes their API?
**A:** The tool uses TikWM API which is regularly updated. Updates will be provided if needed.

---


## 🙏 Acknowledgments

- [TikWM API](https://www.tikwm.com/) - Free TikTok API service
- All contributors and users of this project

---

## 📞 Support

For issues, feature requests, or contributions:
- 📧 Open an issue on GitHub
- 💬 Join the discussion
- ⭐ Star the repository if you find it useful

---

<div align="center">

**Made with ❤️ for the TikTok community**

**[⬆ Back to Top](#tiktok-media-downloader--injector)**

</div>
