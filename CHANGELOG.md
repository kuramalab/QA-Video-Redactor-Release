# Changelog

## 1.2.2 — 21 August 2026

**One click, one job**

- The “Process” button stayed active until the engine replied: a second click in
  that window started a second job on the same video, leaving two rows in the
  history and two output files. The button now switches off the moment it is
  clicked.
- The engine defends itself too: a second request for the same video returns the
  job already running instead of duplicating it.

**Rounded corners**

- Redacted areas are no longer sharp-cornered rectangles. The radius never
  exceeds the safety margin, so the rounded corner eats into the margin only and
  uncovers nothing; the edge is soft rather than jagged.

**Clean uninstall**

- The libraries downloaded on first launch live in the user's data folder, where
  the uninstaller never looked: several gigabytes stayed behind. It now asks
  whether to remove them once uninstalling is done, and suggests keeping them if
  you plan to reinstall. Processed videos are never touched.

## 1.2.1 — 21 August 2026

**Fix: setup stopped with “Access denied”**

- First-run setup wrote its components inside the program folder. When the app
  is installed in `C:\Program Files`, Windows denies writing to anyone who is
  not an administrator, and preparation stopped with
  “Access denied (os error 5)”.
- Program and components now live in two separate places: the code stays where
  the installer puts it, while the interpreter, libraries and models — several
  gigabytes, and belonging to whoever uses the app — go into the user's data
  folder. Where the program folder is writable, as in a portable copy,
  everything stays together as before.

**Right-click**

- The browser menu (reload, view source, inspect) is gone: it makes no sense in
  an application and opened doors that serve no purpose.
- Text fields get a reduced menu instead — Cut, Copy, Paste, Select all —
  translated into all five languages, with inapplicable entries greyed out.

## 1.2.0 — 21 August 2026

**Automatic updates**

- The app checks the public releases at startup and once an hour. When a new
  version is out, a dialog shows what changed: update with one click, or postpone
  and keep a discreet reminder in the header.
- The download reports progress; when it finishes the installer starts and the
  application closes itself.

**Multiple languages**

- Five languages: English, Italian, French, Spanish and German. On first launch
  the system language is picked automatically; the flag selector in the header
  changes it and the choice is remembered.
- Messages coming from the engine are shown translated too, including the
  processing stages and the data categories.

## 1.1.0 — 21 August 2026

**Speed**

- Frames identical to the previous one are no longer analysed again. On a screen
  recording, 78% of the readings were repeated work. The sample video went from
  242 to 64 seconds with an NVIDIA card, and from roughly 25 minutes to 6 without
  one. On footage with continuous motion there is nothing to save, but nothing to
  lose either: the block fingerprint costs microseconds.
- The result is unchanged: the final verification still reports zero readable
  data in both cases.

**Distribution**

- The installer is now 3.6 MB. The heavy libraries are downloaded by the app on
  first launch, picking the build that matches the machine: CUDA when an NVIDIA
  card is present, CPU otherwise.
- A dedicated first-run setup page reports real progress, including during
  package installation — which would otherwise stay silent for minutes.
- No project source code ships inside the package: the code travels as bytecode
  and the interface is embedded in the executable.

**Interface**

- Five-step flow: Source, Data to hide, Engine, Processing, Result. Processing
  and result used to share a single step.
- A pixel-art mascot, used as the application icon, in the brand mark and on the
  loading screens.
- The AI work is named where it actually happens: phases, activity badge and
  final summary.

**Behaviour**

- The masked video is saved next to the original as `filename_blur1.mp4`, with a
  counter so nothing is ever overwritten.
- A single version number for the app and the installer, with a check that stops
  the build when anything is out of sync.

## 1.0.0 — 20 August 2026

First complete release.

- Redaction engine: neural OCR, rules for personal data, term learning and scene
  memory.
- Automatic final verification that re-reads the produced video.
- HTTP service with streaming progress, a queue and cancellation.
- Web interface and desktop application.
- H.264 output that plays anywhere, original audio preserved.
