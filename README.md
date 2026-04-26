# Py To Exe Converter

**Professional Python to Standalone Windows Executable Builder**

A free, modern, and fully automated GUI tool that converts any Python (`.py`) script into a professional standalone `.exe` file using PyInstaller — with **zero manual setup**, **smart hidden import detection**, **custom icons**, **full metadata**, and a beautiful polished interface.

---

## Key Features

- One-click conversion of `.py` → standalone `.exe`
- Smart script analysis: **auto-detects hidden imports** (tkinter, PIL, psutil, win32com, etc.)
- Only enables required imports — keeps your executable small and clean
- **Automatically installs PyInstaller** if missing
- Embeds custom `.ico` icons
- Full Windows version info (Company, Description, Version, Internal Name)
- Supports **Single File** (`--onefile`) and **Directory** (`--onedir`) modes
- Windowed (no console) or console applications
- Add extra files/folders (`--add-data`)
- Real-time progress bar with percentage
- Cancel build anytime
- Modern, compact, centered GUI with yellow title ribbon
- Color-coded status messages (blue/green/orange/red)
- Threaded build — GUI stays fully responsive
- Exit confirmation & placeholder text support

### Auto-Detected Hidden Imports
| Library                  | Purpose                          |
|--------------------------|----------------------------------|
| `tkinter`                | GUI framework                    |
| `tkinter.ttk`            | Themed widgets                   |
| `tkinter.messagebox`     | Message dialogs               	  |
| `tkinter.filedialog`     | File dialogs                     |
| `PIL` / `Pillow`         | Image processing                 |
| `PIL._tkinter_finder`    | Pillow + Tkinter integration     |
| `psutil`                 | System monitoring                |
| `win32com`               | Windows COM automation           |
| `win32com.client`        | COM client support               |

---

## Requirements

- Windows 10/11
- Python 3.6+ installed from [python.org](https://www.python.org/downloads/)  
  (Important: Do **not** use Microsoft Store version)
- No manual installation needed — PyInstaller is auto-installed

---

## Output Naming Format

`<Internal Name> <Major.Minor> Portable.exe`  
Example: `Calculator 1.5 Portable.exe`

---

### Output Example
```
Your Project Folder/
└── MyAwesomeApp/
    ├── build/           (temporary files)
    └── dist/
        └── MyAwesomeApp 2.1 Portable.exe   ← Final executable
```

---

## License

**Freeware** – Completely free for personal and commercial use  
© May 2025 by Avarwand  
You may freely use, modify, share, and distribute this software.

---

## Author

**Avarwand Software**  
Created: 01 June 2025  
Version 2.1 Enhanced: 13 April 2026

Email: avarwand@yahoo.com  
GitHub Issues & Pull Requests welcome!

---

**Thank you for using Py To Exe Converter 2.0**  

```