# Music Downloader

Point it at a spreadsheet. Walk away with MP3s.

## What It Does

Reads a list of songs from an Excel file, searches YouTube for each one, downloads the audio as an MP3, and updates the spreadsheet with the result. Run it again anytime to pick up new entries.

## Requirements

- Python 3.8+
- ffmpeg

### Install ffmpeg

**Windows:**
```bash
winget install ffmpeg
```

**macOS:**
```bash
brew install ffmpeg
```

## Setup

```bash
git clone https://github.com/MrSchaffner/AI-Projects.git
cd Music_Downloader
pip install -r requirements.txt
```

## Usage

**First run** — generates a fresh `songs.xlsx`:
```bash
python downloader.py
```

Fill in your songs. Leave the Status column blank or set it to `waiting`.

**Every run after that:**
```bash
python downloader.py
```

MP3s land in the `downloads/` folder. The spreadsheet updates automatically.

## Spreadsheet

| Artist | Song | Status | Notes |
|---|---|---|---|
| Radiohead | Creep | downloaded | |
| Flume | Drop The Game | waiting | |

| Status | Meaning |
|---|---|
| *(blank)* | Will be downloaded on next run |
| `waiting` | Queued |
| `downloaded` | Done — will be skipped on future runs |
| `not found` | No match on YouTube |
| `error` | Something went wrong — see Notes column |

## Notes

- Close the spreadsheet before running or it won't save
- To retry a failed song — change its status back to `waiting`
- Songs already marked `downloaded` are always skipped
