# Intelligent Application Management System

An **enterprise-level application** for managing and organizing duplicate applications with intelligent categorization.

---

## 🚀 Features

- **Directory Scanner** – Recursively scan directories for application files
- **Duplicate Detection** – SHA-256 hash-based duplicate detection
- **Rule-Based Categorization** – Flexible categorization system with customizable rules
- **Duplicate Management** – Safe deletion of duplicate files with logging
- **File Organization** – Automatic organization into category-based folders
- **Web Interface** – Modern React-based dashboard
- **CLI Tool** – Command-line interface for automation
- **Comprehensive Logging** – Detailed operation logs and reports
- **Export Capabilities** – JSON and CSV report generation

---

## 📂 Supported File Types

### Windows
- `.exe`
- `.msi`
- `.appx`

### macOS
- `.app`
- `.dmg`
- `.pkg`

### Linux
- `.deb`
- `.rpm`
- `.snap`
- `.sh`

### Android
- `.apk`

---

## ⚙️ Installation

### Web Application

1. Clone the repository

```bash
git clone <repository-url>
cd intelligent-application-manager
```

2. Install dependencies

```bash
npm install
```

3. Start the development server

```bash
npm run dev
```

4. Open in browser

```
http://localhost:3000
```

---

### CLI Tool

1. Ensure Python 3.7+ is installed

```bash
python --version
```

2. Install required packages

```bash
pip install pyyaml
```

3. Make the CLI tool executable

```bash
chmod +x scripts/cli-tool.py
```

---

## 💻 Usage

### Web Interface

The dashboard provides the following sections:

1. **Dashboard** – View system statistics and scan status
2. **Scan** – Enter a directory path and start scanning
3. **Duplicates** – Review and manage duplicate files
4. **Categories** – View categorized applications
5. **Rules** – Configure categorization rules
6. **Logs** – Monitor system activity

---

### Command Line

#### Basic Scan

```bash
python scripts/cli-tool.py --directory /Applications
```

#### Scan with organization

```bash
python scripts/cli-tool.py --directory /Applications --organize
```

#### Dry run (no changes)

```bash
python scripts/cli-tool.py --directory /Applications --dry-run --organize
```

#### Delete specific duplicates

```bash
python scripts/cli-tool.py --directory /Applications --delete-duplicates "1,3,5"
```

---

## ⚙️ Configuration

### Web Application

Configuration is managed through the **Rules tab** in the web interface.

---

### CLI Tool

Create a file named `config.yaml`

```yaml
source_directory: "/Applications"
output_directory: "./output"
rules_file: "./rules.json"
dry_run: false
log_level: "INFO"
```

---

## 🧠 Categorization Rules

Rules are defined in **JSON format**.

Example:

```json
{
  "rules": [
    {
      "id": "1",
      "category": "Developer Tools",
      "keywords": ["code", "studio", "dev", "git"],
      "pathPatterns": ["/Developer", "/Applications/Developer"],
      "enabled": true
    }
  ]
}
```

---

## 🔍 Rule Matching

Rules match files using:

- **Keywords** → File name matching (case-insensitive)
- **Path Patterns** → Full path matching
- **Enabled Flag** → Toggle rule on/off

---

## 🔗 API Endpoints

| Endpoint | Method | Description |
|--------|--------|-------------|
| `/api/scan` | POST | Start directory scan |
| `/api/duplicates` | GET | Get duplicate groups |
| `/api/delete` | POST | Delete selected files |
| `/api/organize` | POST | Organize files by category |
| `/api/rules` | GET / POST | Manage categorization rules |
| `/api/logs` | GET | Retrieve system logs |
| `/api/reports` | GET | Download reports (JSON/CSV) |

---

## 📁 File Organization

Output structure:

```
output/
├── Developer_Tools/
├── Productivity/
├── Entertainment/
├── System_Utilities/
└── Uncategorized/
```

---

## 📝 Logging

Operations are logged with timestamps and severity levels.

### Log Levels

- **INFO** → Normal operations
- **WARN** → Non-critical issues
- **ERROR** → Critical errors

### Log Locations

```
Web logs → data/logs.json
CLI logs → app_manager.log
```

---

## 📊 Reports

### JSON Report

Contains complete scan results including:

- File information
- Duplicate groups
- Categorization results
- Scan statistics

---

### CSV Report

Spreadsheet-friendly format containing:

- File Name
- File Path
- Hash
- Category
- File Size

---

## 🔒 Security Considerations

- File operations are logged for audit trails
- SHA-256 hashing ensures content-based duplicate detection
- Dry-run mode prevents accidental data loss
- Backup options available before file deletion

---

## 🛠 Troubleshooting

### Permission Denied

Ensure read/write permissions for target directories.

### Large Files

Adjust `max_file_size` in configuration.

### Memory Usage

Enable parallel processing for large directories.

---

## ⚡ Performance Tips

- Use **SSD storage** for faster file operations
- Enable **parallel scanning** for large directories
- Use **MD5 hashing** for faster scans (less secure but quicker)

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request
