# Changelog

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
