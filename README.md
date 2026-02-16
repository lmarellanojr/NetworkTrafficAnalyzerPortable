# NetworkTrafficAnalyzerPortable

NetworkTrafficAnalyzerPortable is a lightweight, portable packet capture and analysis tool packaged for easy distribution and quick start on Linux and Windows. It bundles the core NetworkTrafficAnalyzer application along with the minimal dependencies and convenience launch scripts so you can run the analyzer without a lengthy setup.

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
- Source/: canonical source files for the analyzer (entry points and modules)

Requirements
- Python 3.8+ (recommended)
- On Linux: standard user with permissions to capture packets (or run with elevated privileges)
- Optional: root/Administrator privileges may be required to capture on raw interfaces

Installation

Option A — Run the portable bundle (recommended)
On Linux (from repository root):

```bash
chmod +x NetworkTrafficAnalyzerPortable.sh
./NetworkTrafficAnalyzerPortable.sh
```

On Windows: double-click NetworkTrafficAnalyzerPortable.bat or run it from a Command Prompt.

Option B — Run from source
1. Create and activate a Python virtual environment.
2. Install dependencies:

```bash
python -m pip install -r Source/requirements.txt
```
3. Run the analyzer:

```bash
python Source/main.py
```

Usage
- The portable launchers start the GUI and load configuration from the default settings.
- If running from source, the main entrypoints are:

- GUI (source bundle): `Source/main.py`
- Packaged app: `App/NetworkTrafficAnalyzer/main.py`

Configuration
- Default configuration files can be found in `App/DefaultData/settings/settings.ini` and `Data/settings/`.
- To persist settings across runs, edit the settings under `Data/settings/settings.ini` (or the corresponding path in the portable bundle).

Logs and data
- Captured logs and runtime data are saved to the `Data/logs/` and `App/DefaultData/logs/` directories depending on whether you run the portable bundle or the source.

Troubleshooting
- Permission errors while capturing:
  - On Linux, run the launcher with sudo or grant capabilities to the Python binary (e.g., `sudo setcap cap_net_raw,cap_net_admin=eip $(which python3)`).
  - On Windows, run the .bat as Administrator.
- Missing dependencies:
  - Use the included wheel in `App/Dependencies/` or install required packages with `pip install -r Source/requirements.txt`.
- If the GUI fails to start, check the log files under `Data/logs/` for errors and ensure your Python environment meets the version requirements.

Contributing
- Contributions are welcome. Please open issues for bugs or feature requests. For code contributions, fork the repository, create a branch, and submit a pull request with a clear description of the change.

License
- Include your project license here (e.g., MIT, Apache-2.0). If you want me to add a specific license file, tell me which license to use.

Contact
- For questions or help, open an issue in this repository or contact the maintainer listed in the project metadata.

Files to inspect
- See [App/NetworkTrafficAnalyzer/main.py](App/NetworkTrafficAnalyzer/main.py) for the packaged launcher and [Source/main.py](Source/main.py) for the source entrypoint.

--
This README was generated to help users run and contribute to NetworkTrafficAnalyzerPortable. If you'd like a shorter Quick Start, a translated version, or an included LICENSE file, tell me which you'd prefer and I will add it.
