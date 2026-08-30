**The margin is worked out by the engine**

- The safety margin around every cover no longer has to be chosen: left on
  "automatic" (the default) it comes from the thing being covered - half
  the text height, so a headline gets a wide margin and a caption a narrow
  one, never below what the old fixed default gave body text, plus an
  allowance for how far the picture moved into that frame. All shares of the
  frame, so a phone clip and a 4K screen agree. The rescue rounds use the
  same rule as the writing, which they did not before. The slider stays,
  as the exception: switch "automatic margin" off and pick a number.
- Every job records what was applied: the number, or "automatic" with the
  smallest and largest margin actually used.

**Measured on every recording sent so far, and corrected where it failed**

- Every field recording, each with the settings it was run with, went through
  the engine and was judged by an independent reading of the finished video.
  What that found is fixed in this version: a scrolling page had whole
  sections covered because the measuring windows disagreed about the timing
  of the scroll - between two sightings every window is now re-anchored on
  where the text was actually seen again, so the cover follows the text and
  covers only the windows' disagreement; a light-theme keyboard (white keys on
  a pale bed) was not recognised - the keycap search now takes its grey
  levels from the picture itself, dark theme or light; a sign-in button
  "with itsme(R)" was covered as an e-mail because the sign reads as "@" -
  a bare "name@" no longer counts, a domain letter has to follow.

- Two more from the same bank: an account number wrapped onto two lines on a
  payment summary - "Brite AB BE10 0019 6865" - was not recognised as the
  account learned whole from another frame, and stood in plain sight beside
  the payer's account that was covered; a learned code is now known by its
  head inside a longer reading as well. And a garbled headline repaired into
  an account number that happened to pass the check digits - one in
  ninety-seven does - is refused unless its country exists and its length is
  that country's: the IBAN registry is in the engine.

**The grain follows the text**

- A forty-pixel headline stayed readable through the mosaic: the blocks were
  eight pixels whatever the text, five of them over a letter, and the
  recogniser read the name back from the finished video. A block is now a
  third of the box, so a letter of any size is one or two blocks and no
  shape; plain blur shrinks the copy until the box is five pixels tall.
  Measured on lines of 20, 40 and 80 pixels: nothing read back, no shapes.
- The keyboard is recognised only by its keycaps now; the reading-based
  guess that stood beside it took a product list for a keyboard and covered
  half the page for a second.

**A proof bank before every release**

- The field recordings that revealed a fault - the reference recording, the
  keyboard one, the one with the address bar - are now permanent cases in
  `packaging/proof.py`, each with the exact settings that were used and what
  the finished video must satisfy (no readable name, keyboard covered, no
  ghost cover, address bar covered, coverage within bounds). The bank runs
  before a version is published.

---

Download **QA Video Redactor 1.8.6 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
