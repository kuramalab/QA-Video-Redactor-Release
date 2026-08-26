**A recording that took 72 minutes now takes 15**

- Measured end to end on the same file with the same settings, across four
  versions: 72.4 minutes, then 43.7, then 37.0, now 14.9. Same detections, same
  residuals, nothing given up.
- The engine no longer reads what it has already read. It remembers what is on
  screen, carries it to where the picture has moved it, and reads again only
  the strips that have changed — the one that has just scrolled into view, or
  the part that changed on its own. Measured on a real recording, 85% of
  everything read had already been read in the frame before and had only moved.
- Decoding and reading now happen at the same time. They used to take turns:
  while the card read a block the processor sat idle, and the other way round —
  11% of the processor and 55% of the card, neither of them the bottleneck.
- The final check looks twelve times a second instead of every second frame.
  On a phone recording at 71 frames a second that meant 35 checks a second,
  three times what a 25 fps video has always had, for a protection nobody asked
  to be three times denser. Anything legible for a twelfth of a second is still
  seen, and at Maximum precision every frame is still read.

**A name half typed has to be half the name**

- Covering a name while it is being entered used to start at three characters.
  With the term "Genny Sirianni" that claimed every "gen" on the page — and on
  a Dutch page "gen" is everywhere, wherever a word breaks across two lines.
  Measured on a real recording: all 75 detections in a twenty second stretch
  were that fragment, and not one of them was the name.
- A beginning now has to be a real share of what it begins, and the words of a
  term are recognised in their own right, so a first name on its own stays
  covered while an unrelated syllable no longer is.

**The update dialog opens in the middle of the window**

- It was opening in the top left corner. The code asked for a style the
  stylesheet no longer had under that name, and a missing style neither fails
  nor warns: the element is simply drawn without it.
- Six more had gone the same way, and they are all back: the language menu, the
  tabs of the Engine step, the right-click menu, the close button of the
  privacy strip, and the mascot with its shadow. The colours of the job states
  had never once applied.
- The build now checks that every style the interface asks for exists, so this
  particular silence cannot come back.

---

Download **QA Video Redactor 1.4.2 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
