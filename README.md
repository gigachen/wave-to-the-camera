# 📸 wave to the camera

> **Category:** Forensic | **Difficulty:** Baby | **Author:** gigachen

## Description

> say cheeeeese 🧀

**Flag format:** `PETIR{part1_part2}`

---

## Challenge File

- `challenge.mp3`

---

## Solution Walkthrough

### Part 1 — Spectrogram Analysis

The MP3 file hides data visually in its **audio spectrogram**. Open the file in a spectrogram viewer to reveal the first part of the flag.

**Tools you can use:**
- [Sonic Visualiser](https://www.sonicvisualiser.org/) — add a Spectrogram layer
- [Audacity](https://www.audacityteam.org/) — View > Show Spectrogram
- [SpectroPlayer](https://www.spectro-player.com/) (online)

**Steps:**
1. Open `challenge.mp3` in Sonic Visualiser or Audacity
2. Switch to spectrogram view
3. Look for text or patterns hidden in the frequency visualization
4. Note down **Part 1** of the flag

---

### Part 2 — Binwalk + Exiftool

The MP3 file also has a **hidden image file** embedded inside it. Extract it and read its metadata.

**Step 1: Extract embedded files with Binwalk**
```bash
binwalk -e challenge.mp3
```
This will create an output folder (e.g., `_challenge.mp3.extracted/`) containing extracted files including a `pt2.jpg`.

**Step 2: Read EXIF metadata with Exiftool**
```bash
exiftool pt2.jpg
```
Look through the metadata fields — **Part 2** of the flag is hidden inside.

---

## Flag Assembly

Combine both parts using the format:
```
PETIR{part1_part2}
```

---

## Tools Required

| Tool | Purpose | Install |
|------|---------|---------|
| Sonic Visualiser / Audacity | Spectrogram analysis | `sudo apt install audacity` |
| binwalk | Extract embedded files | `sudo apt install binwalk` |
| exiftool | Read image metadata | `sudo apt install libimage-exiftool-perl` |

---

## Concepts Covered

- Audio steganography (spectrogram hiding)
- File carving with binwalk
- EXIF metadata forensics

---

*Part of the PETIR regen-2026 CTF qualification round — Forensic category.*
