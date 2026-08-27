**A different reader, and the recording takes nine minutes instead of fifteen**

- The text is now read by PP-OCR instead of EasyOCR. Measured against a page
  whose contents we wrote ourselves, character for character, it gets right the
  three things the old reader got wrong and that cost the most: a tax code read
  as RSSMRA8SMO1H501Q instead of RSSMRA85M01H501Q, an address read
  `mario rossi@example.com` with a space where the dot was, an IBAN with a
  lowercase letter in the middle of it.
- On the same recording: 9.4 minutes against 14.9, with the same detections and
  the same zero residuals. The final check alone went from 453 seconds to 123.
- The new reader joins words together where the old one kept them apart, so the
  address rule no longer expects a space to be there.

**It works out what the machine can do, rather than assuming**

- Where the reading runs is asked of the runtime, not assumed: an NVIDIA card
  on Windows or Linux, an AMD card on Linux, anything with DirectX 12 on
  Windows — which is what gives a laptop with Intel or AMD graphics real
  acceleration — and the processor everywhere else. Measured on the same card:
  217 ms a frame on CUDA, 375 on DirectML, around 900 on the processor.
- How many frames are read at once is worked out from the machine too. On a
  card: how much memory is free, and how much a reader needs for frames of that
  size — 0.94 GB each on a phone recording, 2.67 GB on a 4K one — so a 12 GB
  card reads six at a time and a 4 GB card two, from the same code. Past six the
  card gives nothing back: 14.5 frames a second at six, 14.0 at eight.
- On the processor it reads one frame at a time, and that is now measured
  rather than inherited: one reader does 1.02 frames a second, two do 0.87,
  four do 0.66. The runtime already spreads one reading across every core, and
  more readers only take those cores from each other.

**The processing says when it should be done**

- A share of the bar cannot say it — measured on three real videos, the final
  check took 22%, 36% and 43% of the time — so the engine measures its own pace
  as it goes and works out what is left from that. Every phase walks the same
  frames, so as each one starts, its own pace replaces the estimate.
- It is shown as a time of day rather than a countdown: half a minute of error
  is invisible on "done by 14:32" and glaring on a number ticking down.

**Codes the reader got wrong are recognised anyway**

- A screen reader confuses the same shapes every time: 0 with O, 1 with I, 5
  with S, 8 with B. The rules now allow that confusion where it can happen —
  a digit position accepts the letters it might have been read as, and the
  other way round — and what comes out is put back the way it must have been
  written and checked against the code's own arithmetic: the check character of
  a tax code, the modulo 97 of an IBAN, the Luhn sum of a card number. A
  repaired code that adds up is that code, not a guess.
- Where a code sits inside a longer line, only the code is covered now, not the
  whole line with its label and everything beside it. Only codes: they are
  matched whole, while a name half read is not.

**The visual search is where the logo is asked for**

- Naming a brand to obscure did nothing unless the visual module was switched
  on, and that switch was in the next step, out of sight. It now sits directly
  under the field, and naming a brand without it says so instead of leaving it
  to be discovered from the result.

---

Download **QA Video Redactor 1.5.0 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
