**Remote access actually shows the page on an installed copy**

- From another computer, 1.6.0 answered "Not Found" instead of the interface.
  The desktop shell carries the interface inside its own executable, so the
  engine - which is what a browser talks to - had no files to serve: they
  existed in the development copy, where every test had passed, and not in the
  installed one. The installer now ships the interface for the engine as well,
  and this release was verified against the installed layout itself, served
  from the network address, before being published.
- An engine that finds no interface beside it now says so plainly instead of a
  bare "Not Found".

---

Download **QA Video Redactor 1.6.1 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
