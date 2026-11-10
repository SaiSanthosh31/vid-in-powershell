# Video to ASCII Art Converter with Audio Support

![GitHub stars](https://img.shields.io/github/stars/SaiSanthosh31/vid-in-powershell?style=flat)
![License](https://img.shields.io/github/license/SaiSanthosh31/vid-in-powershell)

A **stand‑alone** Python script that converts video files (or webcam input) into ASCII art, optionally synchronising audio playback.  The entire implementation is bundled in a single file (`vid_in_ps.py`) so it can be dropped into any directory and run without a complex build system.

---

## Features
- Convert any video (MP4, AVI, etc.) or live webcam feed to ASCII art.
- Multiple built‑in character sets (`standard`, `simple`, `detailed`, …).
- Optional colour output using true‑colour ANSI codes.
- Audio playback synchronised with the video (uses a tiny portable `ffplay.exe` on Windows).
- Export frames as plain‑text files for further processing.
- Fully configurable via command‑line arguments.

---

## Requirements
- Python 3.8+ (tested on 3.10).
- `opencv-python` and `numpy` (the script will attempt to install them automatically on first run).
- On Windows, internet access the first time you enable audio – a ~15 MB zip containing `ffplay.exe` is downloaded and cached in `%LOCALAPPDATA%\ASCIIVideoPlayer`.

---

## Installation
```powershell
# Clone the repository (replace with your actual repo URL)
git clone https://github.com/SaiSanthosh31/vid-in-powershell.git
cd vid-in-powershell

# (Optional) Create a virtual environment
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# Run the script – required dependencies will be installed automatically
python vid_in_ps.py -f <your‑video‑file.mp4>
```

---

## Usage
```text
python vid_in_ps.py -f <video> [options]

Options:
  -f, --file       Path to video file or camera index (e.g. "0")   [required]
  -w, --width      Output width in characters (default: 120)
  -c, --charset    Choose charset (standard, simple, detailed, …)   [default: standard]
  --audio          Enable audio playback (downloads ffplay on first run)
  --color          Enable coloured ASCII output
  --speed <float>  Playback speed multiplier (default: 1.0)
  --skip <int>     Skip every N‑1 frames (default: 0 → process all)
  --export <dir>   Export each frame as a .txt file instead of playing
  --export-color   Include ANSI colour codes when exporting frames
```

### Examples
```powershell
# Simple playback
python vid_in_ps.py -f video.mp4

# Wider output, simple charset, doubled speed, with audio
python vid_in_ps.py -f video.mp4 -w 100 -c simple --speed 2.0 --audio

# Export coloured frames to a folder
python vid_in_ps.py -f video.mp4 --export frames/ --export-color
```
---

## Contributing
Feel free to open issues or submit pull requests. Please ensure any new dependencies are listed in the script’s automatic‑install block.

