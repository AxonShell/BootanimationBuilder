# BootanimationBuilder
Simpler and up-to-date bootanimation maker, made to be safer without viruses or trojans.

# Bootanimation Builder

**Bootanimation Builder** is a Python-based GUI tool that helps you create custom Android bootanimations from videos, images, or PNG sequences. It converts videos into bootanimation-compatible frame sequences, generates the necessary `desc.txt`, and packages everything into a `bootanimation.zip` ready to flash on rooted Android devices.

---

## Features

- Import MP4/video or PNG images
- Extract frames at desired framerate and resolution
- Create `desc.txt` with customizable settings (looping and parts)
- Package everything into `bootanimation.zip`
- Optional audio support (WAV files)
- Easy-to-use interface inspired by Rufus

---

## Requirements

- Rooted Android device
- A file explorer with root access (e.g., Root Explorer, Mixplorer)

---

# How to Use

1. **Launch the app**:
   - Run the .exe 

2. **Choose your input**:
   - Select a video (MP4) or a PNG image (for a static frame).
   - Optional: Select a WAV file for boot sound.

3. **Set parameters**:
   - Framerate (e.g., 30 fps)
   - Resolution (e.g., `1080x1920`)
   - Loop mode for animation: `p` or `c`
     - `p` = play once (e.g., boot intro)
     - `c` = continuously loop (e.g., boot loading)

4. **Generate bootanimation**:
   - The tool will extract frames, build the correct folder structure (`part0`, `part1`, ...), write the `desc.txt`, and create a `bootanimation.zip`.

---

## desc.txt Format (Explained)

1080 1920 30
p 1 0 part0
c 0 0 part1



- **1080 1920** = width and height
- **30** = framerate
- **p / c**:
  - `p`: play the part once
  - `c`: loop continuously
- **1** = number of times to play the part (ignored with `c`)
- **0 0** = pause and background color (usually left as 0)
- **part0 / part1** = folder name where PNG frames are stored

---

## How to Flash the Bootanimation on Android (Root Required)

⚠ You must have root to replace the system bootanimation.

### Steps using Root Explorer or similar:

1. Transfer the bootanimation.zip to your device.
2. Open Root Explorer (or Mixplorer in root mode).
3. Navigate to:  
/system/media/

or on some devices:
/data/local/

markdown
Copier
Modifier
4. Rename the original bootanimation to something like:
bootanimation_backup.zip
etc. and save to a location in /storage/emulated/0

5. **Copy your new `bootanimation.zip`** to that folder.

6. **Set permissions**:
- Long-press the file → "Permissions" or "Properties"
- Set to:
  ```
  rw-r--r--
  (User: Read+Write, Group: Read, Others: Read)
  ```
  or numerically: `644`

7. Reboot your phone to see the new animation.

---

## Troubleshooting

- If nothing plays, check:
- Frame resolution must match your screen (e.g., `1080x1920`)
- Permissions must be `644`
- The file **must be named exactly** `bootanimation.zip`
- Ensure you copied it to the correct folder (`/system/media/` or `/data/local/`)

---

## Disclaimer

This tool modifies system visuals. Improper use may cause bootloops or system issues. Always keep a backup and proceed at your own risk.

---

## License

MIT License. Made with love by AxonShell.
