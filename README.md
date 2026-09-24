<div align="center">

# Avarwand Py To Exe Converter 2.2

</div>

A **powerful, modern GUI tool** that turns **Python (.py) scripts into standalone Windows executables (.exe)**, complete with custom icon, embedded version metadata, and smart dependency handling.

> _No command line . No guesswork . Full control_

---

## What's New in v2.2
- **Collect-All Packages**: bundle entire packages (submodules, data files, binaries) with `--collect-all`; auto-detected when you select a script
- **Add Binary**: include native `.dll` / `.so` / `.pyd` files that your script loads at runtime
- **Splash Screen**: show a loading image while the executable unpacks (great for large onefile builds)
- **Copy Metadata**: include distribution metadata for packages that read their own version via `importlib.metadata`
- **Exclude Modules**: leave out unneeded packages to reduce executable size
- **Advanced Options**: Request Admin (UAC), Clean Build, Strip Symbols, UPX Compression, Debug Mode
- **Scrollable main window**: all fields are accessible on any screen size; mouse-wheel scrolling supported
- **Tooltips on every field**: hover over any field or checkbox for a plain-language explanation
- **Auto-detection of collect-all packages**: selecting a script automatically fills the Collect-All field with packages like `pyfiglet`, `babel`, `certifi`, `plotly`, `sklearn`, `nltk`, etc.
- **Live search in Info window**: type to find any topic instantly, with highlighted matches and prev/next navigation
- **Copyable error dialogs**: build errors are shown in a scrollable, selectable text window with a "Copy All" button
- **System32 fix**: builds now start correctly even when the tool's working directory is `C:\Windows\system32`

---

## Main Features
- **Convert any Python (.py) script** into a standalone Windows executable (.exe)
- **Runs without Python on the target machine**: all dependencies are bundled into the build
- **Single File (onefile)** or **Directory (onedir)** packaging
- **Windowed or console** applications (No Console / With Console)
- **Custom icons**: embed your own `.ico` for professional branding
- **Full version metadata** (company, description, version, internal name) embedded into the executable's properties, visible in Windows File Explorer
- **Automatic hidden-import detection**: the selected script is analyzed, and only the imports it really uses are enabled
- **Bundle additional data files** (configuration, database, image, sound, ...) into the build
- **Bundle additional binary files** (.dll, .so, .pyd) for native dependencies
- **Splash screen support**: display an image while the application loads
- **Collect-All**: bundle entire packages including submodules, data files, and binaries
- **Copy Metadata**: include package distribution metadata for `importlib.metadata` compatibility
- **Exclude Modules**: remove unneeded packages to shrink the executable
- **Advanced build options**: UAC admin elevation, clean builds, symbol stripping, UPX compression, debug mode
- **Automatic PyInstaller installation** if it is missing
- **Real-time progress bar** with percentage display and color-coded status messages
- **Multithreaded builds**: the window never freezes
- Safe **STOP** button: cancel a running build at any time, without orphan processes
- **Organized output**: every build gets its own named folder next to the source script
- **Built-in Info window** with a complete field-by-field reference and live search
- **Tooltips** on every field and checkbox for instant guidance
- **Copyable error dialogs**: select and copy the full error text from any build failure
- **Fully GUI-based**: no command-line knowledge required

---

## Smart Automation

The Converter takes care of the fiddly parts of packaging on its own:

- **Finds a working PyInstaller** by testing every plausible way to start it on your system, refreshing the PATH from the Windows registry first; a freshly installed Python is picked up without a reboot
- **Installs PyInstaller automatically** when it is missing, and silently adds the Python `Scripts` directory to the PATH if needed
- **Analyzes the selected script** and enables + pre-ticks only the hidden imports it actually uses; everything else stays grayed out to keep the build lean
- **Auto-detects collect-all packages**: scans the script's imports against a curated list of packages known to need `--collect-all` (pyfiglet, babel, certifi, plotly, sklearn, spacy, nltk, flask, and many more) and pre-fills the Collect-All field
- **Collects extra package data** automatically for libraries that ship additional files (e.g. `tkinterdnd2`)
- **Excludes unused Qt frameworks**, which prevents build aborts and keeps executables noticeably smaller
- **Bundles GUI toolkit data** (Tcl/Tk) when it can be located, so windowed applications work out of the box
- **Logs everything**: the complete build output lands in `build.log` in the output folder, and the decisive error lines are shown directly if a build fails
- **Avoids the system32 trap**: PyInstaller 6+ refuses to run from `C:\Windows\system32`; the tool detects this and automatically switches to a safe working directory

---

## Hidden Imports (Auto-Detected)

Some libraries are loaded dynamically and cannot be discovered by static analysis alone. The Converter watches for the **nine most common cases**:

- `tkinter`, `tkinter.ttk`, `tkinter.messagebox`, `tkinter.filedialog`: the standard GUI toolkit and its sub-modules
- `PIL`, `PIL._tkinter_finder`: the Pillow imaging library and its GUI integration helper
- `psutil`: system and process utilities
- `win32com`, `win32com.client`: Windows COM automation

When you select a script, only the imports it really uses are enabled and ticked; the rest remain disabled to prevent bloat. Manual override is always possible.

---

## Metadata & Branding

Four fields feed straight into the **Details** tab that Windows shows in the executable's Properties:

- **Company Name**: your organization or personal name
- **File Description**: a short summary shown in Task Manager and Explorer tooltips
- **File Version**: in `x.x.x.x` format (e.g. `2.0.0.0`); the first two digits also appear in the output file name
- **Internal Name**: used as the output folder name and as part of the executable name (e.g. `MyApp 2.0 Portable.exe`)

Together with your custom `.ico`, shown in Explorer, the taskbar, and the title bar, the result looks like a finished commercial product, not a packaged script.

---

## Build Options & Output

- **Output Mode**:
  - *Single File (onefile)*: everything packed into one `.exe`, easiest to distribute, unpacks itself at launch
  - *Directory (onedir)*: a folder with the `.exe` and its supporting files, starts faster, easier to debug
- **Console Mode**:
  - *No Console*: for GUI applications, no black window
  - *With Console*: for command-line tools, or when you want to see program output and tracebacks
- **Add Data File**: bundle one extra resource into the package; your program can locate it at run time via the standard `sys._MEIPASS` mechanism
- **Add Binary**: include a native `.dll`, `.so`, or `.pyd` file that your script loads at runtime
- **Splash Screen**: display a `.png` image while the application unpacks and loads (requires Tcl/Tk)
- **Collect-All**: bundle entire packages including all submodules, data files, and binaries (comma-separated list)
- **Copy Metadata**: include distribution metadata for packages that use `importlib.metadata` to read their version at runtime
- **Exclude Modules**: remove specific packages from the build to reduce executable size (comma-separated list)
- **Output structure**: every build is created in `<script folder>\<Internal Name>\`, containing `dist\` (the finished executable), `build\` (working files), the generated `.spec` file, and `build.log`

---

## Advanced Options

- **Request Admin (UAC)**: the executable will prompt for administrator privileges on launch; needed for tools that modify system files, services or the registry
- **Clean Build**: clears PyInstaller's cache before building, ensuring a completely fresh compile; useful after upgrading a dependency or after a failed build
- **Strip Symbols**: removes debugging symbols from the executable and shared libraries, reducing file size; safe for release builds
- **UPX Compression**: enables UPX compression to further shrink the executable; UPX must be installed separately and on the system PATH
- **Debug Mode**: builds with full debug output (`--debug=all`); useful for diagnosing import errors, missing files and startup crashes in the frozen application

---

## System Requirements
- **OS**: Windows 10 / Windows 11
- **Python 3.x** installed on the system (required for packaging your scripts)
- **PyInstaller**: installed automatically at the first build if missing (a one-time internet connection may be needed for this download)

Everything else is handled automatically.

---

## How to Use

1. Download the desired version
2. Unzip it > Install it (_for the installer version_)
3. Select the **Python Script** (.py) you want to convert, its imports and collect-all packages are analyzed automatically
4. Select an **Icon File** (.ico)
5. Fill in the **metadata**: Company Name, File Description, File Version (`x.x.x.x`), Internal Name
6. Choose **Output Mode** and **Console Mode**
7. *Optional*: add extra **data files**, **binary files**, or a **splash screen**; adjust **Collect-All**, **Copy Metadata**, or **Exclude Modules**; enable **Advanced Options**
8. Click **Create the Software**
9. Watch the progress → **Done!** The finished executable is waiting in the `dist` folder inside the new output folder

The **Info** button opens a complete built-in reference explaining every field and option in detail, with a **live search** to find any topic instantly.

---

## Safety Notes

* Your source script is only **read**, never modified
* **All inputs are validated** before a build starts (file existence, `x.x.x.x` version format)
* Builds run **in the background**: the window stays responsive, and the **STOP** button cancels cleanly at any time without leaving orphan processes
* A complete **build.log** is written for every build; if something goes wrong, the actual error message is shown in a **copyable dialog** instead of a vague failure notice
* An **exit confirmation** prevents closing the tool accidentally
* Note: freshly built, unsigned executables are occasionally flagged by antivirus software, a well-known false-positive pattern for self-extracting programs. Only package scripts you trust, and consider signing executables you distribute

---

## Use Cases

* Handing tools to users **who don't have Python installed**
* Turning everyday scripts into **double-clickable programs** for colleagues and customers
* Creating **portable single-file utilities** for USB sticks or network shares
* Giving scripts a **professional finish**: custom icon plus company and version details
* Preparing **clean, versioned releases** of in-house tools
* IT administration and automation tasks

---

## Contributing

This project is released as **freeware**.

While primarily maintained by the author, suggestions, bug reports, and improvement ideas are welcome via email.

Pull requests are currently not accepted.

---

## License

**Avarwand Py To Exe Converter is freeware**, released under a custom End User License Agreement (EULA) by **Avarwand**.

In short, you are free to:

* **Use** the Converter free of charge, for both personal and commercial purposes
* **Keep everything you build**: the executables you create from your own scripts are entirely yours
* **Share** the Converter with anyone, redistributing, hosting, mirroring, and promoting it is welcome, as long as it is passed on **complete and unmodified**, **free of charge**, and with clear credit to **Avarwand**

And you may not:

* Sell the Converter, monetize access to it, or lock it behind paywalls, donations, surveys, registration walls, or paid bundles
* Reverse engineer, decompile, or modify it (except to the limited extent permitted by applicable law)
* Claim it as your own work, or remove its copyright and branding notices

The Converter is provided **"as is"**, without warranty of any kind.

*This summary is for convenience only. The legally binding terms are in the [LICENSE](LICENSE.md) file included with every release and in this repository.*

---

**Developed by Avarwand Software**  
**Latest Version: September 2026**
**Initial Release: May 2025**  

---

## Contact

**Avarwand Support**  
📧 [avarwand@yahoo.com](mailto:avarwand@yahoo.com)  
🌐 [github.com/avarwand](https://github.com/avarwand/)

© 2025–2026 Avarwand. All rights reserved.

---
