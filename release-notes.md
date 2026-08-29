**The second logo job in a session no longer dies**

- The first job with a brand to find worked; the next one failed with
  "expected all tensors to be on the same device". Naming the targets encodes
  the brand's text, and after a detection has moved the model to the graphics
  card that encoder is left half on the card and half on the processor. When
  the naming meets that split it now redoes itself on the processor, and the
  next detection moves what it needs back to the card on its own. Reported
  twice from the field in one morning; reproduced on the second job exactly,
  then proven on four consecutive jobs with three different brands.

---

Download **QA Video Redactor 1.6.9 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
