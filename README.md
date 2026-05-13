# TiktokDownloadWeb
# TikTok Media Downloader & Injector

<div align="center">

![TikTok Downloader Banner](https://img.shields.io/badge/TikTok-Media%20Downloader-ff004f?style=for-the-badge&logo=tiktok&logoColor=white)
![Version](https://img.shields.io/badge/version-2.0-blue?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

**A powerful tool to download, extract, and manipulate TikTok media content**

[Features](#features) • [Installation](#installation) • [Usage](#usage) • [API Reference](#api-reference) • [Contributing](#contributing)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage Guide](#usage-guide)
- [API Endpoints](#api-endpoints)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

The **TikTok Media Downloader & Injector** is a comprehensive web-based tool that allows you to:

- 📥 Download TikTok videos in high quality (MP4 format)
- 🎵 Extract audio from TikTok videos (MP3 format)
- 📸 Extract hidden high-resolution images from TikTok photo posts
- 📄 Parse and view complete JSON metadata from any TikTok post
- 💉 Inject custom JSON data into downloaded content
- 📦 Batch download multiple URLs simultaneously

Built with modern web technologies and integrated with the TikWM API, this tool provides a seamless experience for content creators, researchers, and TikTok enthusiasts.

---

## ✨ Features

### 🎬 Video Downloader
| Feature | Description |
|---------|-------------|
| **High Quality** | Download videos in original quality (up to 1080p) |
| **Audio Extraction** | Extract audio as MP3 with 320kbps quality |
| **Queue System** | Manage multiple downloads with persistent queue |
| **Progress Tracking** | Real-time download progress indicators |

### 📸 Image Extractor
| Feature | Description |
|---------|-------------|
| **Hidden Images** | Extract all images from TikTok photo posts (including carousel) |
| **Gallery View** | Thumbnail preview of all extracted images |
| **Bulk Download** | Download all images with one click |
| **High Resolution** | Get original quality images (no compression) |

### 📄 JSON Parser
| Feature | Description |
|---------|-------------|
| **Complete Metadata** | Access all video/photo metadata including stats, creator info, etc. |
| **Syntax Highlighting** | Color-coded JSON display for easy reading |
| **Download Option** | Save metadata as JSON file |

### 💉 JSON Injector
| Feature | Description |
|---------|-------------|
| **Custom Data Injection** | Merge your own JSON data with TikTok metadata |
| **Timestamps** | Automatic injection timestamp tracking |
| **Export Capability** | Download the combined JSON structure |

### 📦 Batch Downloader
| Feature | Description |
|---------|-------------|
| **Multi-URL Processing** | Process up to 100 URLs at once |
| **Flexible Options** | Choose what to download per batch (video/audio/JSON) |
| **Parallel Processing** | Sequential processing with progress tracking |
| **Results Summary** | Detailed success/failure report |

---

## 🚀 Installation

### Quick Start (Web Version)

Simply open the `index.html` file in any modern web browser. No server required!

```bash
# Clone the repository
git clone https://github.com/yourusername/tiktok-media-downloader.git

# Navigate to project directory
cd tiktok-media-downloader

# Open in browser (choose one)
start index.html          # Windows
open index.html           # macOS
xdg-open index.html       # Linux
```

### Python Backend Setup (Optional)

For advanced features like server-side processing:

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the server
python app.py
```

### Requirements

- **Modern web browser** (Chrome, Firefox, Safari, Edge)
- **Internet connection** (for API calls)
- **Python 3.8+** (optional, for backend features)

### Dependencies (Python Backend)

```
requests>=2.28.0
tqdm>=4.64.0
rich>=13.0.0
yt-dlp>=2023.0.0
pillow>=9.0.0
```

---

## 📖 Usage Guide

### 1. Downloading Videos

```javascript
// Example URL format
https://www.tiktok.com/@username/video/1234567890123456789

// Steps:
1. Copy the TikTok video URL
2. Paste into the "Video URL" field
3. Click "Download Video" or "Download Audio Only"
4. File will automatically save to your downloads folder
```

### 2. Extracting Images from Photo Posts

```javascript
// Example photo post URL
https://www.tiktok.com/@username/photo/1234567890123456789

// Steps:
1. Copy the TikTok photo post URL
2. Paste into the "Photo Post URL" field
3. Click "Extract Images"
4. View gallery and download individual or all images
```

### 3. Fetching JSON Metadata

```javascript
// Any TikTok URL works
https://www.tiktok.com/@username/video/1234567890123456789

// Steps:
1. Paste any TikTok URL
2. Click "Fetch Metadata"
3. View structured JSON data
4. Optionally download as JSON file
```

### 4. Injecting Custom JSON

```json
// Example custom JSON
{
  "custom_tags": ["viral", "trending", "2024"],
  "notes": "This is my personal annotation",
  "rating": 5,
  "categories": ["entertainment", "music"]
}

// Steps:
1. Enter a TikTok URL (optional, for base metadata)
2. Paste your custom JSON
3. Click "Inject JSON"
4. Download the merged data structure
```

### 5. Batch Processing

```
# Example batch file content
https://www.tiktok.com/@user1/video/1234567890
https://www.tiktok.com/@user2/photo/9876543210
https://www.tiktok.com/@user3/video/5555555555

// Options:
✓ Download Videos
□ Download Audio Only
✓ Extract JSON Metadata
```

---

## 🔧 API Endpoints

### TikWM API Integration

The tool uses the [TikWM API](https://www.tikwm.com/) as its primary data source.

```javascript
// Base URL
const API_URL = 'https://www.tikwm.com/api/';

// Request format
GET ${API_URL}?url=${encodeURIComponent(tiktok_url)}

// Response structure
{
  "code": 0,
  "msg": "success",
  "data": {
    "id": "video_id",
    "title": "video_title",
    "play": "video_url",
    "music": "audio_url",
    "images": ["image1_url", "image2_url"],
    "author": {
      "id": "author_id",
      "unique_id": "username",
      "nickname": "display_name",
      "avatar": "avatar_url"
    },
    "statistics": {
      "play_count": 1000000,
      "digg_count": 50000,
      "comment_count": 1000,
      "share_count": 500
    }
  }
}
```

### Proxy Usage

To avoid CORS issues, the web version uses:
```
https://api.allorigins.win/raw?url=${encoded_url}
```

---

## ⚙️ Configuration

### Browser Settings

| Setting | Recommended | Reason |
|---------|-------------|--------|
| JavaScript | Enabled | Required for all functionality |
| Pop-ups | Allowed | For download windows |
| Storage | Enabled | For queue persistence |
| CORS | Default | Using proxy for cross-origin |

### File Save Locations

Downloads are saved to your browser's default download directory:

- **Windows**: `C:\Users\[Username]\Downloads`
- **macOS**: `/Users/[Username]/Downloads`
- **Linux**: `/home/[Username]/Downloads`

---

## 🔍 Troubleshooting

### Common Issues and Solutions

| Issue | Possible Cause | Solution |
|-------|---------------|----------|
| **"Failed to fetch video info"** | Invalid URL | Verify the URL is correct and the video exists |
| **Images not extracting** | Not a photo post | Ensure the URL is for a photo post (contains `/photo/`) |
| **Download not starting** | Pop-up blocked | Allow pop-ups for this site in browser settings |
| **Slow download speed** | Network congestion | Try again later or use a different network |
| **CORS error** | Direct API access | Ensure using the proxy endpoint |
| **JSON parse error** | Invalid JSON format | Validate your JSON before injection |

### Debug Mode

Enable console logging for debugging:

```javascript
// Open browser console (F12)
localStorage.setItem('debug', 'true');
location.reload();
```

### Support Resources

- 📖 [TikWM API Documentation](https://www.tikwm.com/docs)
- 💬 [GitHub Issues](https://github.com/yourusername/tiktok-media-downloader/issues)
- 📧 Email: support@example.com

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit your changes**
   ```bash
   git commit -m 'Add amazing feature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

### Development Setup

```bash
# Install development dependencies
pip install -r requirements-dev.txt

# Run tests
python -m pytest tests/

# Format code
black .
isort .

# Lint code
flake8 .
pylint src/
```

### Coding Standards

- Follow PEP 8 for Python code
- Use semantic HTML5 elements
- Write vanilla JavaScript (no frameworks required)
- Comment complex logic
- Update documentation for new features

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 TikTok Media Downloader

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## ⚠️ Disclaimer

This tool is for **educational purposes only**. Please respect:

- TikTok's Terms of Service
- Content creators' rights
- Copyright laws in your jurisdiction

Do not use this tool to:
- Download copyrighted content without permission
- Violate TikTok's API terms
- Distribute downloaded content without proper attribution

---

## 📊 Version History

| Version | Date | Changes |
|---------|------|---------|
| 2.0.0 | 2024-01-15 | Complete rewrite with modern UI, batch processing, JSON injector |
| 1.5.0 | 2023-10-01 | Added image extractor and gallery view |
| 1.0.0 | 2023-07-01 | Initial release with basic download functionality |

---

## 🙏 Acknowledgments

- [TikWM API](https://www.tikwm.com/) for providing the data endpoint
- [Font Awesome](https://fontawesome.com/) for icons
- [Google Fonts](https://fonts.google.com/) for typography
- All contributors and users of this project

---

<div align="center">

**Made with ❤️ for the TikTok community**

[Report Bug](https://github.com/yourusername/tiktok-media-downloader/issues) • [Request Feature](https://github.com/yourusername/tiktok-media-downloader/issues) • [Star on GitHub](https://github.com/yourusername/tiktok-media-downloader)

</div>
