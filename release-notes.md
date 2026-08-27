**The visual module and the text readers no longer kill each other**

- A job with a logo to find died on its first visual detection: "operation not
  permitted when stream is capturing". The visual module runs through torch,
  the text readers through onnxruntime, and the two do not share the graphics
  card gracefully - when one is capturing a CUDA stream and the other launches,
  the launch dies. Reproduced deterministically before fixing.
- The card now takes turns: any number of readings still run together, exactly
  as before; the visual module waits for them and holds the card alone; the
  readings queue behind it. A job without the visual module is untouched -
  measured, same time to the second.

---

Download **QA Video Redactor 1.6.3 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
