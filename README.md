# ⚡ Postman Collection Analyzer

A professional, high-performance, single-file HTML application designed to audit, normalize, and analyze Postman collections. Built specifically for security researchers, developers, and QA engineers who need to visualize API surface areas quickly and securely.

## 🚀 Key Features

* **Offline-First Security**: Operates entirely within your browser using the HTML5 File API. No data is ever uploaded to a server, making it safe for sensitive internal API collections.
* **Deep Variable Resolution**: Recursively resolves Postman `{{variable}}` syntax up to **10 iterations deep**. This handles complex nested environment variables, such as a base URL containing protocol and host variables.
* **Smart URL Normalization**: 
    * Preserves critical versioning segments like `v1`, `v2`, and `v3`.
    * Automatically tokenizes dynamic segments: UUIDs are converted to `{uuid}` and numeric IDs are converted to `{id}`.
* **Host-Based Grouping**: Automatically identifies and groups endpoints by their Target Host. It strips the domain from the path to provide a clean, professional "Scope Report" aesthetic.
* **Terminal-Style Reporting**: Generates a clean, mono-spaced report. It supports both grouped methods (e.g., `[GET,POST] /api/users`) and a "One Method Per Line" toggle for granular auditing.
* **Zero Dependencies**: All CSS and JavaScript logic is bundled inline. No external CDNs are called, ensuring full functionality in air-gapped or restricted environments.

## 🛠️ Installation & Usage

1.  **Download**: Save the `postman-analyzer.html` file to your local machine.
2.  **Launch**: Open the file in any modern web browser.
3.  **Upload**: 
    * Select your **Collection JSON** files.
    * (Optional) Select your **Environment JSON** files to resolve variables.
4.  **Process**: Click **Analyze** to generate the real-time dashboard and endpoint list.
5.  **Export**: Click **Export to TXT** to save a formatted text version of your findings for reports or documentation.

## 📊 Dashboard Metrics

* **Unique Paths**: The count of distinct API routes discovered after normalization.
* **Methods**: Total count of different HTTP methods identified across all requests.
* **Total Calls**: The aggregate number of requests found in all uploaded collections.

## 🔒 Security Specifications

* **Content Security Policy (CSP)**: The application uses a strict `default-src 'none'` policy to prevent unauthorized data exfiltration or external script execution.
* **XSS Protection**: All rendered data is passed through a security utility to escape HTML entities. This prevents cross-site scripting from potentially malicious JSON content.
* **No Persistence**: The tool does not use LocalStorage, Cookies, or IndexedDB. A simple page refresh clears all session data.

## 📝 License

Distributed under the MIT License.
