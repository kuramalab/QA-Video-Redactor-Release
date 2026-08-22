**Faster, doing exactly the same work**

- A full recording that used to take 72 minutes now takes 44. Measured on the
  same file with the same settings, start to finish, not estimated.
- The reading spreads across the processor's cores instead of saturating one
  and leaving the graphics card idle. How many cores it uses is worked out from
  the machine it is running on: all of them except two, which stay with the
  operating system, and never more than the free video memory can hold.
- Blurring is computed on a small copy of the region and scaled back up. The
  result is indistinguishable and the masking step is dozens of times cheaper.
- The final verification reads only the frames it actually looks at, in
  parallel, instead of decoding every frame in the video.
- Nothing was changed on trust: every step was compared against the previous
  engine on the same clip. Same detections, down to the single one; same
  residuals.

**Frames per second**

- The Engine step now offers a frame rate. Screen recordings often run at 60 or
  70 frames per second and repeat almost everything: choosing 25 does the same
  job in a third less time, and the finished video plays at the chosen rate.
- Left on "Original", nothing changes.

**Signature**

- The installer and the executable are signed again. A previous build reported
  the signing as failed when it had actually succeeded: the check was reading
  whether this machine trusted the certificate rather than whether the file
  carried it.

---

Download **QA Video Redactor 1.4.0 Setup.exe** below. The installer is a few megabytes: on first launch the app downloads the components that match your computer.
