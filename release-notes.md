**The interface can be reached from another computer**

- A Remote section in Settings opens the engine to the local network. Anyone on
  the network reaches the same interface in a browser and signs in - admin/admin
  to begin with, and the admin account can add and remove other accounts and
  change passwords. With remote off, which is the default, connections from the
  network are refused outright, exactly as before.
- Processing works from remote too: the video travels over the network, is
  processed on the computer that hosts the engine, and the result stays there -
  the interface says so rather than leaving it to be discovered.
- Every run in the history carries the name of who asked for it: the signed-in
  account from remote, the person at the keyboard locally. Notes and the audit
  trail work the same from both sides.
- What remote cannot do, by construction: switch remote off, or manage accounts
  without being admin. Passwords are never stored - only a derivation that
  cannot be turned back, ground through two hundred thousand rounds.

**The computer staying awake is now a choice**

- Since 1.4.1 the engine has kept the computer from sleeping while a video is
  being processed. That is now a switch in Settings - on by default - for
  whoever prefers the machine to follow its own power rules. The change applies
  from the next run; a run already going keeps the promise it started with.

---

Download **QA Video Redactor 1.6.0 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
