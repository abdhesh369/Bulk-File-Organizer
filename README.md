<![CDATA[<div align="center">

# 📂 Bulk File Organizer

**A fast, configurable CLI tool that sorts messy directories into clean, categorized folders — instantly.**

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-6366f1?style=for-the-badge)]()

</div>

---

## The Problem

Downloads, Desktops, and project folders get cluttered *fast*. Manually dragging files into folders is tedious and error-prone.

## The Solution

Point this tool at any directory. It reads the file extensions, maps them to categories defined in a simple JSON config, and moves every file into a neatly labeled subfolder — **in seconds**.

```
Before                          After
──────                          ─────
📁 Downloads/                   📁 Downloads/
├── report.pdf                  ├── 📁 documents/
├── photo.jpg                   │   └── report.pdf
├── song.mp3                    ├── 📁 images/
├── archive.zip                 │   └── photo.jpg
├── script.py                   ├── 📁 audio/
└── notes.txt                   │   └── song.mp3
                                ├── 📁 archives/
                                │   └── archive.zip
                                ├── 📁 code/
                                │   └── script.py
                                └── 📁 documents/
                                    └── notes.txt
```

---

## ✨ Features

| Feature | Description |
|---|---|
| **Category Mapping** | 10 built-in categories — images, documents, audio, video, code, and more |
| **JSON Config** | Fully customizable `config.json` — add, remove, or rename categories freely |
| **Dry Run** | Preview all moves with `--dry-run` before touching a single file |
| **Undo** | Every operation is logged; run `--undo` to reverse the last batch instantly |
| **Recursive Mode** | Organize files buried in subdirectories with `-r` |
| **Conflict Resolution** | Duplicate filenames get timestamped suffixes — no overwrites, ever |
| **Hidden File Handling** | Dotfiles are skipped by default; include them with `--include-hidden` |
| **Progress Bar** | Visual progress via `tqdm` for large directories |
| **Logging** | Full operation log written to `organizer.log` |

---

## 🚀 Quick Start

### 1. Clone & Install

```bash
git clone https://github.com/abdhesh369/Bulk-File-Organizer.git
cd Bulk-File-Organizer

# (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate   # Linux/macOS
venv\Scripts\activate      # Windows

pip install -r requirements.txt
```

### 2. Organize a Directory

```bash
python organizer.py ~/Downloads
```

That's it. Files are sorted into category subfolders.

---

## 📖 Usage

```
usage: organizer.py [-h] [--dry-run] [--config CONFIG] [--recursive]
                    [--include-hidden] [--undo] [--create-config] [--verbose]
                    [source_directory]
```

### Common Commands

```bash
# Organize your Downloads folder
python organizer.py ~/Downloads

# Preview changes without moving anything
python organizer.py ~/Downloads --dry-run

# Organize all nested subdirectories too
python organizer.py ~/Downloads --recursive

# Undo the last operation
python organizer.py --undo

# Generate a fresh config.json
python organizer.py --create-config

# Verbose logging for debugging
python organizer.py ~/Downloads --verbose
```

### Flags Reference

| Flag | Short | Description |
|---|---|---|
| `--dry-run` | `-n` | Simulate — print what would happen, move nothing |
| `--config` | `-c` | Path to a custom config file (default: `config.json`) |
| `--recursive` | `-r` | Process files in all subdirectories |
| `--include-hidden` | | Include dotfiles (hidden files) |
| `--undo` | `-u` | Reverse the last organize operation |
| `--create-config` | | Write a starter `config.json` and exit |
| `--verbose` | `-v` | Enable debug-level logging |

---

## ⚙️ Configuration

Categories are defined in `config.json`. Each key is a folder name; the value is a list of extensions.

```json
{
  "file_types": {
    "images":        [".jpg", ".jpeg", ".png", ".gif", ".bmp", ".svg", ".webp", ".ico"],
    "documents":     [".pdf", ".doc", ".docx", ".txt", ".rtf", ".odt", ".md"],
    "spreadsheets":  [".xls", ".xlsx", ".csv", ".ods"],
    "presentations": [".ppt", ".pptx", ".odp", ".key"],
    "archives":      [".zip", ".rar", ".7z", ".tar", ".gz", ".bz2", ".xz"],
    "audio":         [".mp3", ".wav", ".flac", ".aac", ".ogg", ".m4a", ".wma"],
    "video":         [".mp4", ".avi", ".mkv", ".mov", ".wmv", ".flv", ".webm"],
    "code":          [".py", ".js", ".ts", ".html", ".css", ".java", ".cpp", ".c", ".h", ".go", ".rs"],
    "executables":   [".exe", ".msi", ".dmg", ".pkg", ".deb", ".rpm", ".appimage"],
    "data":          [".json", ".xml", ".yaml", ".yml", ".sql", ".db"]
  }
}
```

> Files that don't match any extension are placed in an **`other/`** folder.

To add a new category, just add a new key:

```json
"fonts": [".ttf", ".otf", ".woff", ".woff2"]
```

---

## 🔄 Undo System

Every organize operation writes a journal to `organizer_undo.json`. To reverse:

```bash
python organizer.py --undo
```

This moves every file back to its original location and archives the undo log with a timestamp.

---

## 🏗️ Project Structure

```
Bulk-File-Organizer/
├── organizer.py          # Core CLI application
├── config.json           # File-type → category mapping
├── requirements.txt      # Python dependencies
├── .gitignore            # Git ignore rules
├── organizer.log         # Runtime log (auto-generated)
└── organizer_undo.json   # Undo journal (auto-generated)
```

---

## 🤝 Contributing

1. **Fork** this repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m "Add my feature"`
4. Push: `git push origin feature/my-feature`
5. Open a **Pull Request**

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

<div align="center">

**Built by [abdhesh369](https://github.com/abdhesh369)** · ⭐ Star this repo if you find it useful!

</div>
]]>
