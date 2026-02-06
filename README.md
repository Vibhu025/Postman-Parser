# ⚡ Postman Collection Analyzer

<div align="center">

![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![Security](https://img.shields.io/badge/security-XSS%20Protected-brightgreen)

A professional, high-performance, single-file HTML application designed to audit, normalize, and analyze Postman collections. Built specifically for security researchers, penetration testers, developers, and QA engineers who need to visualize API surface areas quickly and securely.

[Features](#-key-features) • [Usage](#️-usage) • [Security](#-security-specifications) • [Contributing](#-contributing)

</div>

---

## 🎯 Why Use This Tool?

When working with large Postman collections or multiple API environments, it becomes challenging to:
- **Identify duplicate endpoints** across different collections
- **Normalize dynamic IDs** (UUIDs, numeric IDs) to see the actual unique API surface
- **Group endpoints by host** for security scoping and testing
- **Resolve environment variables** to see actual URLs
- **Export clean reports** for documentation or bug bounty submissions

This tool solves all these problems in a **secure, offline-first** environment with **zero dependencies**.

---

## 🚀 Key Features

### 🔐 **Offline-First Security**
- Operates entirely within your browser using the HTML5 File API
- **No data is ever uploaded to a server**, making it safe for sensitive internal API collections
- Works in air-gapped or restricted environments
- No external CDN calls or dependencies

### 🧠 **Deep Variable Resolution**
- Recursively resolves Postman `{{variable}}` syntax up to 15 iterations deep
- Handles complex nested environment variables (e.g., `{{protocol}}://{{baseUrl}}:{{port}}`)
- Supports multiple environment files simultaneously

### 🎨 **Smart URL Normalization**
- **Preserves API versioning**: `v1`, `v2`, `v3` segments remain intact
- **Tokenizes dynamic segments**:
  - UUIDs → `{uuid}` (e.g., `550e8400-e29b-41d4-a716-446655440000` → `{uuid}`)
  - Numeric IDs → `{id}` (e.g., `/users/123` → `/users/{id}`)
  - Query parameters → `{id}` (e.g., `?userId=456` → `?userId={id}`)
- **No URL encoding of placeholders**: Displays `{id}` not `%7Bid%7D`

### 🎯 **Intelligent Deduplication**
- Automatically removes duplicate endpoints based on `METHOD + NORMALIZED_URL`
- Shows statistics: "Removed X duplicates, Y unique endpoints remain"
- Handles the same endpoint appearing in multiple collections

### 📊 **Host-Based Grouping**
- Automatically identifies and groups endpoints by Target Host
- Strips the domain from paths for clean, professional reports
- Handles multiple API domains in a single view

### 🖥️ **Terminal-Style Reporting**
- Clean, monospaced output perfect for security reports
- **Two display modes**:
  - **Grouped**: `[GET,POST,PUT] /api/users/{id}`
  - **One Per Line**: Each method on a separate line for detailed auditing
- Professional formatting suitable for bug bounty reports

### 🔍 **Advanced Filtering & Search**
- Filter by HTTP method (GET, POST, PUT, PATCH, DELETE, OPTIONS, HEAD)
- Real-time search across paths, methods, and names
- Sort by path, method, or name (ascending/descending)
- Debounced search for performance with large datasets

### 📤 **Export Capabilities**
- Export to TXT with formatted, readable output
- Includes metadata: total endpoints, duplicates removed, export date
- Preserves grouping and formatting from the UI

---

## 🛠️ Usage

### Quick Start

1. **Navigate**: Open the [Link](https://vibhu025.github.io/Postman-Parser/) in any modern web browser (Chrome, Firefox, Edge, Safari)
2. **Upload Collections**:
   - Click "Collection Files" and select one or more Postman collection JSON files
   - (Optional) Click "Environment Files" and select Postman environment JSON files
3. **Analyze**: Click "Parse Collections" to generate the dashboard
4. **Explore**: Use filters, search, and sorting to analyze your API surface
5. **Export**: Click "Export to TXT" to save a formatted report

### File Requirements

- **Collection Files**: Postman Collection v2.0 or v2.1 JSON format
- **Environment Files**: Postman Environment JSON format (optional)
- **File Size**: Up to 30MB per file (larger files will show a warning)

---

## 🔒 Security Specifications

### Privacy & Data Handling
- **No Persistence**: No LocalStorage, Cookies, or IndexedDB
- **No Analytics**: No tracking, telemetry, or external requests
- **Session-Only**: Page refresh clears all data
- **Client-Side Only**: All processing happens in your browser

---

## 📊 Dashboard Metrics

| Metric | Description |
|--------|-------------|
| **Unique Endpoints** | Distinct API routes after normalization and deduplication |
| **Total Methods** | Count of different HTTP methods across all endpoints |
| **Total Requests** | Aggregate number of requests in all uploaded collections |
| **Duplicates Removed** | Number of duplicate endpoints that were filtered out |

---

## 🎛️ Advanced Features

### Method Filtering
Click on method buttons to show/hide specific HTTP methods:
- `GET` - Read operations
- `POST` - Create operations
- `PUT` - Full update operations
- `PATCH` - Partial update operations
- `DELETE` - Delete operations
- `OTHER` - OPTIONS, HEAD, etc.

### Layout Toggle
- **Default (Grouped)**: `[GET,POST,PUT] /api/users/{id}`
- **One Per Line**: Each method appears on a separate line

### Search & Sort
- **Search**: Type to filter endpoints by path, method, or name
- **Sort Options**:
  - Path (A → Z / Z → A)
  - Method (A → Z / Z → A)
  - Name (A → Z / Z → A)

---

## 🐛 Known Limitations

- **Browser Memory**: Very large collections (>1000 endpoints) may slow down on older devices
- **URL Parsing**: Malformed URLs or non-standard formats may not parse correctly
- **Export Format**: Only TXT export is currently supported (CSV/JSON coming soon)
- **Postman Versions**: Optimized for Postman Collection v2.0/v2.1

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Report Bugs**: Open an issue with details about the problem
2. **Suggest Features**: Share ideas for new functionality
3. **Submit PRs**: Fork the repo and submit pull requests
4. **Improve Docs**: Help make the documentation clearer

### Development Setup

Since this is a single-file HTML application, development is straightforward:

1. Clone the repository
2. Open `index.html` in your editor
3. Make changes
4. Test in a browser
5. Submit a PR

### Code Style Guidelines

- Use clear, descriptive variable names
- Add comments for complex logic
- Maintain the existing code structure
- Ensure XSS protection for any new features
- Test with the provided test files

---

## 📋 Changelog

### v2.0.0 (Current)
- ✅ Fixed URL encoding issue (displays `{id}` not `%7Bid%7D`)
- ✅ Added intelligent deduplication
- ✅ Improved normalization algorithm
- ✅ Added progress bar for large files
- ✅ Enhanced host-based grouping
- ✅ Fixed accordion scrolling for large lists
- ✅ Added 4th stat card for duplicates

### v1.0.0
- Initial release
- Basic collection parsing
- Environment variable resolution
- Export to TXT

---

## 🙏 Acknowledgments

- Built for security researchers, penetration testers, and API developers
- Inspired by the need for better API surface visualization
- Special thanks to the Postman team for their excellent collection format

---

## 📞 Support

- **Issues**: Open an issue on GitHub
- **Discussions**: Use GitHub Discussions for questions
- **Security**: Report security issues privately via email

---

## 🌟 Star History

If this tool helped you, please consider giving it a star ⭐ to help others discover it!

---

<div align="center">

Made with ❤️ for the security and developer community

[Report Bug](../../issues) • [Request Feature](../../issues) • [Documentation](../../wiki)

</div>
