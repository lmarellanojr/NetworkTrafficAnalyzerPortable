# NetworkTrafficAnalyzerPortable

NetworkTrafficAnalyzerPortable is a lightweight, portable packet capture and analysis tool packaged for easy distribution and quick start on Linux, macOS, and Windows. It bundles the core NetworkTrafficAnalyzer application along with the minimal dependencies and convenience launch scripts so you can run the analyzer without a lengthy setup.

**Key features**
- Capture and analyze network traffic using the included NetworkTrafficAnalyzer core.
- Portable packaging: run using the provided shell, batch, or desktop launcher.
- Includes required dependencies (e.g., Scapy) for offline/air-gapped environments.
- Config-driven: settings files are provided for persistent configuration.

Repository layout
- App/: Packaged portable application (runnable bundle).
  - NetworkTrafficAnalyzer/: packaged app and launcher scripts
  - DefaultData/: default logs and settings shipped with the bundle
  - Dependencies/: included third-party wheels (e.g., scapy)
- Other/: help documentation and canonical source mirror
- Data/: user data directory (logs and settings, created at first run)

Requirements
- Packet capture requires root/administrator privileges.
- No installation needed. Copy the NetworkTrafficAnalyzerPortable/ folder to any USB drive, external disk, or local directory and run.
- Python 3.8+ is only needed if no compiled binary is present.

How to run

**Linux:**

Option A — Double-click (recommended):
1. Open the NetworkTrafficAnalyzerPortable/ folder in your file manager.
2. Double-click "NetworkTraffic Analyzer" (the .desktop file).
3. A graphical password dialog will appear (like Windows UAC).
4. Enter your password and the app launches.

> Note: If your file manager asks what to do with the .desktop file, choose "Trust and Launch" or "Mark as Executable", then double-click again.

Option B — Terminal:

```bash
chmod +x NetworkTrafficAnalyzerPortable.sh
./NetworkTrafficAnalyzerPortable.sh
```

A graphical password prompt will appear automatically. Falls back to terminal sudo if no desktop is detected.

CLI mode (no GUI):

```bash
./NetworkTrafficAnalyzerPortable.sh --cli
```

**Windows:**
1. Navigate to the NetworkTrafficAnalyzerPortable\ folder.
2. Right-click `NetworkTrafficAnalyzerPortable.bat` → "Run as administrator".

CLI mode (no GUI): open Command Prompt as Administrator, then run:

```
NetworkTrafficAnalyzerPortable.bat --cli
```

**macOS:**
1. Open Terminal and navigate to the NetworkTrafficAnalyzerPortable/ folder.
2. Launch the app:

```bash
./NetworkTrafficAnalyzerPortable.sh
```

3. If prompted, enter your password for sudo access.

CLI mode (no GUI):

```bash
./NetworkTrafficAnalyzerPortable.sh --cli
```

> Note: On macOS, you may need to allow Terminal in System Settings → Privacy & Security → App Management.

**Run from source (any platform):**
1. Install dependencies:

```bash
pip install scapy
```

2. Run the analyzer:

```bash
cd App/NetworkTrafficAnalyzer
python3 main.py           # GUI mode
python3 main.py --cli     # CLI mode
```

How to build the binary

1. Install dependencies:

```bash
pip install pyinstaller scapy
```

2. Build the executable:

```bash
cd App/NetworkTrafficAnalyzer/
python3 build.py
```

3. The binary is placed in App/NetworkTrafficAnalyzer/ automatically. Build artifacts are cleaned up after a successful build.

> Note: The build produces a native binary for the current OS — ELF on Linux, .exe on Windows, Mach-O on macOS.

Configuration
- Default configuration files can be found in `App/DefaultData/settings/settings.ini` and `Data/settings/`.
- To persist settings across runs, edit the settings under `Data/settings/settings.ini`.

Logs and data
- Captured logs are saved to the `Data/logs/` directory.
- To reset to defaults, delete the `Data/` folder. It will be recreated from `App/DefaultData/` on next launch.

Portability
- Copy the entire NetworkTrafficAnalyzerPortable/ folder to any USB drive or external disk. No installation needed. No system files or registry entries are modified. Works fully offline.

Troubleshooting
- Permission errors while capturing:
  - On Linux, the launcher automatically elevates via `pkexec` (graphical) or `sudo` (terminal).
  - On Windows, right-click the .bat and select "Run as administrator".
- Missing dependencies:
  - Use the included wheel in `App/Dependencies/` or install required packages with `pip install scapy`.
  - The app will prompt to auto-install from bundled files on first run if Scapy is missing.
- If the GUI fails to start, check the log files under `Data/logs/` for errors and ensure your Python environment meets the version requirements.

Contributing
- Contributions are welcome. Please open issues for bugs or feature requests. For code contributions, fork the repository, create a branch, and submit a pull request with a clear description of the change.

License
- Include your project license here (e.g., MIT, Apache-2.0). If you want me to add a specific license file, tell me which license to use.

Contact
- For questions or help, open an issue in this repository or contact the maintainer listed in the project metadata.

Files to inspect
- See [App/NetworkTrafficAnalyzer/main.py](App/NetworkTrafficAnalyzer/main.py) for the packaged launcher and [Other/Source/main.py](Other/Source/main.py) for the source entrypoint.
