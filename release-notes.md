**An update can no longer leave the libraries behind**

- Updating to 1.5.0 broke the engine with "No module named rapidocr_onnxruntime":
  the first launch installs the libraries only when nothing is installed yet, so
  an update - or a reinstall over leftover components - skipped that step and a
  version needing a new library never got it. The list is now re-checked at
  every start: a second when everything is in place, a download only for what is
  missing. Proven on a deliberately broken runtime, which healed itself.
- First launch now ends with a real reading by the actual reader, so a broken
  installation shows up there and not on the first video.

**History, with its own button**

- A clock button next to the settings gear opens the history: every video put
  through this computer - who ran it, when it started, how long it took, the
  outcome, detections and residuals, a button to open the result's folder, and a
  note you can write and edit in place. It lives on disk and survives closing
  the application.

**Settings, in one place**

- The gear opens settings with four sections. General: language and a default
  destination folder for results (empty keeps them next to the original).
  Defaults: the values every new run starts from. Updates: automatic checking
  on or off, and a check-now button. System: what machine this is - graphics
  card, cores, memory - and what the engine made of it: where text is read, how
  many frames at a time, where the data lives.

**Faster still, and clearer**

- The final check reads the frames as they are being written instead of
  reopening the finished video: the whole second decode is gone, and checking
  overlaps writing.
- The processing now says when it should be done - as a time of day, learned
  from its own pace, not from a fixed table.
- The three precision choices say what they do on the choice itself: 1 in 5,
  1 in 3, every frame.

---

Download **QA Video Redactor 1.5.1 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
