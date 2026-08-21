# Changelog

## 1.3.3 — 21 August 2026

**Placeholders left showing**

- The update panel read “Version {version} is available” with the placeholder in
  place of the number: the migration moved the code to English but not the
  placeholders inside the text, so they stopped being filled.
- Every case of the same kind is fixed, not only the one that was noticed: the
  unrecognised file name, the installed version in the update panel and the
  frame counter in the processing phases.
- Durations follow the chosen language: they were assembled by hand in the code,
  so four translations out of five were never used.

**Icon**

- The mascot's eyes are green in the application icon too.

## 1.3.2 — 21 August 2026

**Signed executable**

- The application and the installer are signed with a KuramaLab certificate. It
  is self-signed, so it only counts on machines where it has been trusted: there
  Windows names the publisher instead of saying “unknown”. Everywhere else
  nothing changes, and no antivirus is convinced by it - the first-launch scan
  stays until there is a recognised certificate.
- Signing is optional: without a certificate the build carries on and still
  produces a working product.

## 1.3.1 — 21 August 2026

**The startup screen tells the truth**

- On the loading page the second and third items were hardcoded as not done and
  never updated: “AI ready” could not light up even in principle. The screen now
  asks the engine every second: the service lights up when it really answers,
  the neural network when it has finished warming up, and only then does the
  step-by-step flow appear.
- The first video therefore starts at once, instead of sitting at zero while the
  graphics card tunes its kernels.

**Fixes**

- The interface was still sending Italian precision and style values to the
  engine, which refused the job. Besides fixing them, they are realigned on
  startup with what the engine declares, so that kind of mismatch cannot happen
  again.
- When a job fails to start, the app stays on the Processing step where the
  button was pressed: the Result step was promising an outcome that did not
  exist.
- The mascot's eyes are green before the engine is ready too.

**Under the hood**

- The migration of the code to English is complete: shell, engine, interface,
  stylesheets, packaging scripts and release workflow. The text on screen stays
  in the five languages, because that is content rather than code.

## 1.3.0 — 21 August 2026

**The engine starts without elevated rights**

- The application failed to start its engine when launched normally: the check
  “is the engine answering?” went through a full HTTP client, which hangs when
  the program has no administrator rights. It is now a plain socket on a thread
  with a hard deadline — on some machines the antivirus inspects even local
  connections, and a closed port takes seconds to answer.
- Waiting no longer watches the clock but the process: while the engine lives it
  is worth waiting, and if it dies the app says so and points at `engine.log`,
  which the shell now writes next to the components.
- The bar used to sit at zero for half a minute at the start of the first video:
  not the models loading, but the first inference tuning the GPU kernels. That
  time is now spent while the service starts, as you pick a video.

**Several videos at once**

- Pick or drop more than one video. Each appears in a list and can be removed on
  its own. While working you see the queue: the one being processed with its
  bar, the others waiting. Cancel stops the whole queue.

**Drag and drop**

- Dropping a video onto the window now works. If the app runs as administrator
  Windows forbids it, and the window explains that instead of looking inert.

**Result**

- “Save a copy elsewhere” opens the system dialog; “Open folder” shows the
  result selected in the file manager. Deleting a job no longer removes the
  result of a video you picked from disk — that file is yours.

**Privacy, stated plainly**

- A strip on the source step says the video never leaves your computer: no
  upload, no account, no telemetry, so no personal data handed to third parties.

**Interface**

- The engine step is split into two tabs; redacted areas have rounded corners;
  one click on Process starts exactly one job; the footer stays put like the
  header; the history appears only on the result step.

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
