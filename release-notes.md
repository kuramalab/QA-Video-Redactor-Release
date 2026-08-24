**The computer no longer falls asleep on the job**

- A long video is exactly the work nobody sits and watches, and Windows was
  putting the machine to sleep while the engine was still going. Measured on a
  real run: a job made 1.6% of progress in eight hours of standby, and the run
  started after it was killed outright by the display driver on the way out.
  While a video is being processed the computer is now told the work matters.
  The screen is still free to turn off.

**Masks follow the text instead of covering the trail it left**

- On a page that scrolls, every position a name passed through used to be
  merged into one shape and that shape was covered in every frame of the scene:
  a whole column blurred from top to bottom, the rest of the page unreadable.
  Each sighting now continues the one before it, and the mask travels with the
  text.
- The movement is measured, not guessed: the picture is cut into overlapping
  bands and each is asked how far it has moved, which costs a fraction of a
  millisecond against the 385 ms a reading costs. A phone page does not move as
  one piece — the bars stay while the content scrolls — so where two bands
  disagree the mask covers both answers rather than betting on one.
- Measured on a test recording scrolled at 300, 800, 2000 and 4000 pixels a
  second: the name stayed covered in every one of the 810 frames, while the
  part of the picture covered for nothing fell from 17% to 1.3%. On a real
  recording the worst case fell from 6.5% to 1.8%, with the same 75 detections
  and the same zero residuals as before.
- Every threshold is now a share of the frame instead of a number of pixels, so
  the same code suits a phone clip and a 4K screen. Verified at three
  resolutions of the same video: same result on all three.

**Video memory**

- How many frames are read at once is worked out from what a reading really
  costs on frames of that size — 1.3 GB on a 1080x2340 page, measured, against
  the 700 MB previously assumed. Four readings at a time instead of six: 7% of
  speed given up for half the memory.
- The process is now held under a ceiling. Past it an allocation is refused
  rather than served out of system memory, which does not fail the job but
  makes it crawl. A reading that does not fit waits for the others and goes on
  its own.
- The full recording went from 43.7 to 37.8 minutes, reading fewer frames at a
  time: the card no longer spends the run chasing memory it does not have.

**Progress that moves**

- The engine reads frames in blocks and said nothing until a whole block was
  done — eight seconds of silence at a time, which reads as a program that has
  stopped. It now reports every reading as it lands: one message every 0.22
  seconds instead of every 8, and the bar never walks backwards.
- The elapsed seconds are counted by the interface, one after another, instead
  of arriving in leaps whenever the engine had something to say.
- Spreading the masks across the scenes was the one stretch with nothing to
  read, and therefore silent. It reports its own progress too.

---

Download **QA Video Redactor 1.4.1 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
