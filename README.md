# QA Video Redactor

**Screen recordings leak.** A demo, a bug report, a training clip: on screen
there is a customer's email address, an IBAN, a tax code, a name in a form. The
recording gets shared with a colleague, a client, a supplier — and the personal
data travels with it. Blurring it by hand means scrubbing frame by frame, and a
single frame missed is a leak.

QA Video Redactor does it for you: it reads the video, finds personal data and
covers it for as long as it stays on screen.

## Nothing leaves your computer

There is no upload, no account, no telemetry. The video is opened, read and
rewritten on your own disk, and the result is saved next to the original. The
only time the app uses the network is the one-off download of its components on
first launch, and the check for new versions.

That is a deliberate choice: a video full of personal data is exactly the kind
of file that should not be handed to someone else's servers, least of all to
have the personal data extracted from it. It is also **why the requirements
below are what they are** — the recognition that a cloud service would run on
its own machines runs on yours.

## Download

**[Get the latest release](https://github.com/kuramalab/QA-Video-Redactor-Release/releases/latest)**

The installer is only a few megabytes. On first launch the app detects your
hardware and downloads what it needs: about 2.5 GB with an NVIDIA card
(GPU-accelerated) or about 350 MB without.

## How it works

1. **Pick a video** — the result is saved next to the original as
   `filename_blur1.mp4`, with a counter so nothing is ever overwritten.
2. **Choose what to hide** — categories of personal data plus your own terms.
3. **Tune the engine** — analysis precision, blur style, safety margin.
4. **Processing** — a neural network reads the frames; frames identical to the
   previous one are skipped, which keeps the tool usable on machines without a
   dedicated GPU.
5. **Result** — preview, a log of every detection with its timecode, and the
   verification verdict.

Three mechanisms work together so nothing slips through:

- **Recognition** — OCR on sampled frames plus rules for personal data.
- **Learning** — from the data it finds, the engine derives the underlying
  secrets (for example the local part of an email address) and re-checks every
  piece of text against them, prefixes included. That is what covers a value
  while it is still being typed, character by character.
- **Scene memory** — the video is split into scenes; once a sensitive area is
  found, it stays masked for the whole scene, and short gaps such as cross-fades
  are closed automatically.

When processing ends, an **automatic verification pass** re-reads the finished
video with OCR and reports anything still legible. That is what makes the file
deliverable without a manual review.

## Requirements

Everything runs locally, so the work has to fit on your machine. A recent
computer is enough; an NVIDIA card is not required, it only makes it faster.

| | Minimum | Recommended |
|---|---|---|
| Operating system | Windows 10 64-bit (build 1809+) | Windows 11 |
| Processor | x86-64 with AVX2, 4 cores | 8 cores or more |
| Memory | 8 GB | 16 GB |
| Disk space | 6 GB with an NVIDIA card - 2 GB without | 10 GB |
| Graphics | optional: NVIDIA with 4 GB VRAM, driver 527 or newer | NVIDIA with 6 GB+ |
| Network | only for the first-run setup and update checks | - |

The disk space is for the recognition libraries, downloaded once: about 5.4 GB
for the CUDA build, about 1.2 GB for the CPU one. They live in your user data
folder, and the uninstaller offers to remove them.

**Measured usage** while processing a 1920x1080 video:

- memory: about 1.2 GB for the engine, plus the interface
- video memory: about 1.8 GB when GPU acceleration is active

**Indicative timings** for 17 seconds of 1080p screen recording, with the final
verification enabled:

| Machine | Time |
|---|---|
| With an NVIDIA card (RTX 4070 Ti) | about 1 minute |
| CPU only (12th-gen Intel i7) | about 6 minutes |

Frames identical to the previous one are not analysed again: on screen
recordings that saves up to 80% of the work, and it is what makes the tool
practical without a dedicated GPU. On footage with continuous motion there is
nothing to save, and timings rise accordingly.

## Version

Current: **1.3.2** - see [Releases](https://github.com/kuramalab/QA-Video-Redactor-Release/releases) for the
full changelog. The app checks for new versions on its own and offers to update.

---

Built by **Genny Sirianni** - kuramalab@gmail.com - KuramaLab
