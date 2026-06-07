# YT-DLP Premium Downloader

A macOS tool primarily built for **YouTube Music Premium** users who want to download their music in the highest available quality. By authenticating with your Premium account cookies, the tool unlocks format 141 — a 256kbps AAC stream in `.m4a` format, complete with embedded metadata and cover art. Downloads are verified to work with Pioneer CDJ equipment including all models back to the **CDJ-2000 NXS (Nexus 1)**, making them fully compatible with USB playback on professional DJ setups. The audio is lossless in terms of the source stream quality and carries proper ID3 tags, making it a solid choice for anyone who cares about audio fidelity, archiving, or professional playback.

If HQ is unavailable (no cookies or stream not accessible), the tool automatically falls back to an **AIFF pipeline**, converting the best available WebM audio to AIFF with embedded cover art and metadata via ffmpeg.

> ⚠️ Read `README.txt` **before and after installation** for full guidance on setup, usage, and troubleshooting.

---

## Features

- **HQ 256kbps AAC downloads** in `.m4a` format via YouTube Music Premium cookies (format 141)
- **Embedded metadata and cover art** on all downloaded files
- **CDJ-compatible bitrate and format** - tested back to CDJ-2000 NXS models
- **AIFF fallback pipeline** with cover art and metadata if HQ is unavailable
- **Playlist batch downloading** from a simple `.txt` URL list
- **Single track mode** via direct URL input
- **URL sanitization** - automatically normalizes country-coded domains and strips playlist tags
- **Anti-bot protection** — randomized delay between playlist track downloads
- **Cancel on relaunch** - double-clicking the app while a download is running cancels it
- **Auto folder management** - creates and cleans up `[HQ-256k]` and `[Fallback-AIFF]` subfolders
- **Automatic PO token framework installation** - required for authenticated HQ streams, handled by the installer
- **Session log file** generated after every run for easy troubleshooting

---

## Requirements

- macOS (Apple Silicon natively supported - see note below for other architectures)
- [Homebrew](https://brew.sh) with `yt-dlp` and `ffmpeg` installed
- Python 3.12+
- A YouTube Music Premium account

Install yt-dlp and ffmpeg via Homebrew if you haven't already:
```bash
brew install yt-dlp ffmpeg
```

> **Apple Silicon note:** The rustypipe-botguard binary included in this package is built for `aarch64-apple-darwin` (Apple Silicon). If you are on an Intel Mac or another architecture, you can still use this tool by manually downloading the correct binary from [here](https://codeberg.org/ThetaDev/rustypipe-botguard/releases) and placing it in your install folder. Everything else works the same.

> **Chrome extension note:** The cookies extension required for HQ downloads will be offered automatically during installation. No need to set it up beforehand.

---

## Installation

1. Download and unzip this repository

2. Before double-clicking `install.command`, macOS will likely block it as it comes from the internet. To allow it:
   - Right-click `install.command` in Finder
   - Click **Open**
   - A dialog will appear saying it is from an unidentified developer — click **Open** anyway
   - If no Open option appears, go to **System Settings → Privacy & Security**, scroll down and you will see a message about `install.command` being blocked - click **Open Anyway**

3. Terminal will open and guide you through the setup. When prompted for an install path, enter a path with **no spaces in the folder name**, for example:
```
/Users/yourname/YouTubeDownloader
```

4. After installation completes, place your `cookies.txt` file into the install folder

5. Move `YouTube Downloader.app` to your **Applications folder** for easy access

> The installer automatically installs Python dependencies, sets up the PO token framework, extracts the rustypipe-botguard binary, and compiles the launcher into a native macOS `.app`. The Chrome extension for cookie export will be opened for you at the end of installation.

---

## Usage

**Single track:**
1. Double-click `YouTube Downloader.app`
2. Select *Single Track*
3. Choose or create a destination folder
4. Paste your YouTube Music URL

**Playlist:**
1. Open your YouTube Music playlist in Chrome and scroll to the very bottom to make sure all tracks are loaded
2. Press F12 → Console tab
3. Paste the contents of `F12Developer_Tool_Command.txt` and press Enter
4. Copy all returned URLs into a plain `.txt` file (TextEdit → Format → Make Plain Text), with a blank line after the last URL
5. Double-click `YouTube Downloader.app`
6. Select *Playlist* and point it to your `.txt` file

Downloaded files are saved under your install folder in:
- `yt-dlp/[folder name]/[HQ-256k]/` — 256kbps AAC `.m4a` with metadata (requires valid cookies)
- `yt-dlp/[folder name]/[Fallback-AIFF]/` — AIFF with cover art and metadata

---

## Troubleshooting

See `README.txt` inside your install folder for detailed troubleshooting steps including cookie setup, PO token configuration, and manual rustypipe-botguard installation.

If you are stuck and nothing seems to work, feel free to open an issue on this repository or reach out directly — happy to help.

---

## Notes

- `cookies.txt` needs to be re-exported roughly every 24 hours
- Folder names with spaces are not supported — use underscores or no separator, e.g. `YouTubeDownloader` or `YouTube_Downloader`
- Apple Silicon is natively supported out of the box; other architectures require a manual binary swap
- To cancel an active download, simply double-click the app again

---

## Support

BTC donations welcome: `15hMZCUhPZs9tMAoVUR3YY4ZLxAKebo3wU` (BTC network)

*Thanks for downloading. -Nutcracker :)*

---

Save this as `README.md` in your repository root. Want any tweaks?
