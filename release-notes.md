**Room on the card, and rescue rounds that read only what they touched**

- The engine now takes at most 80% of the card's memory, whatever the card:
  the rest stays free for the screen and for everything else drawing on it.
  Beyond that line a card does not fail, it quietly spills into system
  memory over the bus and everything slows to a crawl - measured by hand
  with large models on a 12 GB card, and seen here at 97% in use. The share
  is relative, so an 8 GB card and a 24 GB one keep the same proportion.
- The first rescue round reads the whole rewritten file, as before, since a
  re-encoding can make something legible anywhere. The rounds after it read
  only around what they have just covered. Measured on the reference
  recording: rounds two and three went from 2 min 35 s to 1 min each, the
  whole job from 16 min 16 s to 12 min 55 s, with the same result - no text
  left legible.

**Screenshots with the notes**

- A note in the history can carry images: paste a screenshot straight into
  the note, drop it there, or pick files with the paperclip. The row shows
  how many it has; "show all" lays them out as thumbnails, and one click
  opens them full size. Whoever has the history open sees them arrive.

---

Download **QA Video Redactor 1.8.3 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
