# Changelog

## 1.6.6 — 27 August 2026

**The history reads as columns again**

- The file name opens the line, as it originally did, and the four fields that
  follow - outcome, date, duration, author - now have fixed widths, each
  measured against the widest thing its language can write ("fehlgeschlagen"
  for the outcome, the French full-year date). Five perfect columns on every
  card, verified to the pixel at two window sizes.
- The progress bar on a running card is back in plain view inside the card,
  where it was liked, instead of a thin line on the edge.

## 1.6.5 — 27 August 2026

**The history lines up**

- Duration is the first field now, in a fixed right-aligned column, with the
  author beside it: "38s" and "21 min 6 s" take the same room, so every file
  name starts at the same point. The outcome badge closes the line on the
  right, where the eye can run down the column and see at a glance what went
  well.
- A closed note is one line with an ellipsis, and every closed card is exactly
  the same height - measured, not eyeballed: all at the same pixel. "Show all"
  appears only when the text really is cut, which is measured on the text
  itself, so the same sentence offers it in a narrow window and not in a wide
  one.

## 1.6.4 — 27 August 2026

**Typing is covered, not just the finished value**

- An address being typed showed its first letters in the clear, and the blur
  arrived only once it was complete. Short fragments must not be sensitive on
  their own - that lesson cost a video of masked Dutch syllables - but the
  place makes the difference: if the finished value appears somewhere, the
  growing prefixes seen in that same spot just before it are its typing. They
  are covered backwards now, from the fourth-fifth character on. Proven on a
  purpose-built typing video: field covered, surrounding text untouched.

**Addresses, the world over**

- The Addresses category knew seven Italian street words. It now recognises
  the street vocabularies of fifteen languages - traversa and contrada, rue,
  straat, strasse, calle, rua, ulica, namesti, utca, ulitsa, caddesi, sokak,
  gata, katu, jalan, nagar, marg - and all four shapes an address takes:
  word before the name, word after it (Kossuth utca 4), glued to it
  (Kerkstraat 5), and number first (7 Baker Street; 12, MG Road). Verified on
  47 cases in both directions, including the traps: "Boarding Gate 4" and
  "3 Street Fighter" stay untouched.

**The history is made of cards, not a table**

- Ten columns fit no window: the horizontal scrollbar is gone because there is
  nothing left to scroll. Each run is a card - name, outcome, date, duration,
  author, detections, folder, note - and long notes fold to three lines with
  "show all". A filter narrows the list by file or author. Verified at two
  window sizes, to the pixel.

## 1.6.3 — 27 August 2026

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

## 1.6.2 — 27 August 2026

**A brand name is no longer mistaken for someone's address**

- A registered-trademark sign next to a brand name - itsme(R), in the report
  that led here - is sometimes read as an @ by the recogniser, and the engine
  then learned the brand as a "secret" and masked it through the whole video.
  Nothing is learned from an address that is not whole any more: name, provider
  and extension, all three. A half-typed address is still covered where it
  stands - it just teaches nothing.

**The visual module works on installed copies**

- Asking for a logo failed with a complaint about the model file: the weights
  were never shipped and never downloaded, so no installed machine had them,
  and the path they were looked for under carried a Windows long-path prefix
  that the loader refused. The weights now download themselves the first time
  the visual module is asked for - 54 MB, once - and the paths are clean.
  Proven from an empty folder before publishing.

## 1.6.1 — 27 August 2026

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

## 1.6.0 — 27 August 2026

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

## 1.5.1 — 27 August 2026

**An update can no longer leave the libraries behind**

- Updating to 1.5.0 broke the engine with "No module named rapidocr_onnxruntime":
  the first launch installs the libraries only when nothing is installed yet, so
  an update - or a reinstall over leftover components - skipped that step and a
  version needing a new library never got it. The list is now re-checked at
  every start: a second when everything is in place, a download only for what is
  missing. Proven on a deliberately broken runtime, which healed itself.
- First launch now ends with a real reading by the actual reader, so a broken
  installation shows up there and not on the first video.

**History, with its own button**

- A clock button next to the settings gear opens the history: every video put
  through this computer - who ran it, when it started, how long it took, the
  outcome, detections and residuals, a button to open the result's folder, and a
  note you can write and edit in place. It lives on disk and survives closing
  the application.

**Settings, in one place**

- The gear opens settings with four sections. General: language and a default
  destination folder for results (empty keeps them next to the original).
  Defaults: the values every new run starts from. Updates: automatic checking
  on or off, and a check-now button. System: what machine this is - graphics
  card, cores, memory - and what the engine made of it: where text is read, how
  many frames at a time, where the data lives.

**Faster still, and clearer**

- The final check reads the frames as they are being written instead of
  reopening the finished video: the whole second decode is gone, and checking
  overlaps writing.
- The processing now says when it should be done - as a time of day, learned
  from its own pace, not from a fixed table.
- The three precision choices say what they do on the choice itself: 1 in 5,
  1 in 3, every frame.

## 1.5.0 — 27 August 2026

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

## 1.4.3 — 26 August 2026

**The waking screen stands in the middle of the window**

- While the engine starts up there is nothing else on the page, and the panel
  was sitting at the top with the rest of the window empty below it. It is now
  centred in whatever room the window gives, at any size — and if the window is
  made shorter than the panel itself, the top stays reachable rather than being
  cut off above the edge.

**The update dialog fits, and reads properly**

- It never grows past the window now. The notes scroll; the title and the
  buttons stay where they are, so the dialog is usable on a short window.
- Release notes are written wrapped at a fixed width, and every line was
  becoming its own bullet point: one sentence arrived as four. Lines that
  continue the one above are joined back onto it.
- A heading arrived with a stray asterisk in front of it, because the bullet
  marker was stripped before the bold one and ate half the pair. Headings are
  now recognised whole and shown as headings.

## 1.4.2 — 26 August 2026

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

## 1.4.1 — 24 August 2026

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

## 1.4.0 — 22 August 2026

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

## 1.3.3 — 21 August 2026

**Placeholders left showing**

- The update panel read “Version {version} is available” with the placeholder in
  place of the number: the migration moved the code to English but not the
  placeholders inside the text, so they stopped being filled.
- Every case of the same kind is fixed, not only the one that was noticed: the
  unrecognised file name, the installed version in the update panel and the
  frame counter in the processing phases.
- Durations follow the chosen language: they were assembled by hand in the code,
  so four translations out of five were never used.

**Icon**

- The mascot's eyes are green in the application icon too.

## 1.3.2 — 21 August 2026

**Signed executable**

- The application and the installer are signed with a KuramaLab certificate. It
  is self-signed, so it only counts on machines where it has been trusted: there
  Windows names the publisher instead of saying “unknown”. Everywhere else
  nothing changes, and no antivirus is convinced by it - the first-launch scan
  stays until there is a recognised certificate.
- Signing is optional: without a certificate the build carries on and still
  produces a working product.

## 1.3.1 — 21 August 2026

**The startup screen tells the truth**

- On the loading page the second and third items were hardcoded as not done and
  never updated: “AI ready” could not light up even in principle. The screen now
  asks the engine every second: the service lights up when it really answers,
  the neural network when it has finished warming up, and only then does the
  step-by-step flow appear.
- The first video therefore starts at once, instead of sitting at zero while the
  graphics card tunes its kernels.

**Fixes**

- The interface was still sending Italian precision and style values to the
  engine, which refused the job. Besides fixing them, they are realigned on
  startup with what the engine declares, so that kind of mismatch cannot happen
  again.
- When a job fails to start, the app stays on the Processing step where the
  button was pressed: the Result step was promising an outcome that did not
  exist.
- The mascot's eyes are green before the engine is ready too.

**Under the hood**

- The migration of the code to English is complete: shell, engine, interface,
  stylesheets, packaging scripts and release workflow. The text on screen stays
  in the five languages, because that is content rather than code.

## 1.3.0 — 21 August 2026

**The engine starts without elevated rights**

- The application failed to start its engine when launched normally: the check
  “is the engine answering?” went through a full HTTP client, which hangs when
  the program has no administrator rights. It is now a plain socket on a thread
  with a hard deadline — on some machines the antivirus inspects even local
  connections, and a closed port takes seconds to answer.
- Waiting no longer watches the clock but the process: while the engine lives it
  is worth waiting, and if it dies the app says so and points at `engine.log`,
  which the shell now writes next to the components.
- The bar used to sit at zero for half a minute at the start of the first video:
  not the models loading, but the first inference tuning the GPU kernels. That
  time is now spent while the service starts, as you pick a video.

**Several videos at once**

- Pick or drop more than one video. Each appears in a list and can be removed on
  its own. While working you see the queue: the one being processed with its
  bar, the others waiting. Cancel stops the whole queue.

**Drag and drop**

- Dropping a video onto the window now works. If the app runs as administrator
  Windows forbids it, and the window explains that instead of looking inert.

**Result**

- “Save a copy elsewhere” opens the system dialog; “Open folder” shows the
  result selected in the file manager. Deleting a job no longer removes the
  result of a video you picked from disk — that file is yours.

**Privacy, stated plainly**

- A strip on the source step says the video never leaves your computer: no
  upload, no account, no telemetry, so no personal data handed to third parties.

**Interface**

- The engine step is split into two tabs; redacted areas have rounded corners;
  one click on Process starts exactly one job; the footer stays put like the
  header; the history appears only on the result step.

## 1.2.2 — 21 August 2026

**One click, one job**

- The “Process” button stayed active until the engine replied: a second click in
  that window started a second job on the same video, leaving two rows in the
  history and two output files. The button now switches off the moment it is
  clicked.
- The engine defends itself too: a second request for the same video returns the
  job already running instead of duplicating it.

**Rounded corners**

- Redacted areas are no longer sharp-cornered rectangles. The radius never
  exceeds the safety margin, so the rounded corner eats into the margin only and
  uncovers nothing; the edge is soft rather than jagged.

**Clean uninstall**

- The libraries downloaded on first launch live in the user's data folder, where
  the uninstaller never looked: several gigabytes stayed behind. It now asks
  whether to remove them once uninstalling is done, and suggests keeping them if
  you plan to reinstall. Processed videos are never touched.

## 1.2.1 — 21 August 2026

**Fix: setup stopped with “Access denied”**

- First-run setup wrote its components inside the program folder. When the app
  is installed in `C:\Program Files`, Windows denies writing to anyone who is
  not an administrator, and preparation stopped with
  “Access denied (os error 5)”.
- Program and components now live in two separate places: the code stays where
  the installer puts it, while the interpreter, libraries and models — several
  gigabytes, and belonging to whoever uses the app — go into the user's data
  folder. Where the program folder is writable, as in a portable copy,
  everything stays together as before.

**Right-click**

- The browser menu (reload, view source, inspect) is gone: it makes no sense in
  an application and opened doors that serve no purpose.
- Text fields get a reduced menu instead — Cut, Copy, Paste, Select all —
  translated into all five languages, with inapplicable entries greyed out.

## 1.2.0 — 21 August 2026

**Automatic updates**

- The app checks the public releases at startup and once an hour. When a new
  version is out, a dialog shows what changed: update with one click, or postpone
  and keep a discreet reminder in the header.
- The download reports progress; when it finishes the installer starts and the
  application closes itself.

**Multiple languages**

- Five languages: English, Italian, French, Spanish and German. On first launch
  the system language is picked automatically; the flag selector in the header
  changes it and the choice is remembered.
- Messages coming from the engine are shown translated too, including the
  processing stages and the data categories.

## 1.1.0 — 21 August 2026

**Speed**

- Frames identical to the previous one are no longer analysed again. On a screen
  recording, 78% of the readings were repeated work. The sample video went from
  242 to 64 seconds with an NVIDIA card, and from roughly 25 minutes to 6 without
  one. On footage with continuous motion there is nothing to save, but nothing to
  lose either: the block fingerprint costs microseconds.
- The result is unchanged: the final verification still reports zero readable
  data in both cases.

**Distribution**

- The installer is now 3.6 MB. The heavy libraries are downloaded by the app on
  first launch, picking the build that matches the machine: CUDA when an NVIDIA
  card is present, CPU otherwise.
- A dedicated first-run setup page reports real progress, including during
  package installation — which would otherwise stay silent for minutes.
- No project source code ships inside the package: the code travels as bytecode
  and the interface is embedded in the executable.

**Interface**

- Five-step flow: Source, Data to hide, Engine, Processing, Result. Processing
  and result used to share a single step.
- A pixel-art mascot, used as the application icon, in the brand mark and on the
  loading screens.
- The AI work is named where it actually happens: phases, activity badge and
  final summary.

**Behaviour**

- The masked video is saved next to the original as `filename_blur1.mp4`, with a
  counter so nothing is ever overwritten.
- A single version number for the app and the installer, with a check that stops
  the build when anything is out of sync.

## 1.0.0 — 20 August 2026

First complete release.

- Redaction engine: neural OCR, rules for personal data, term learning and scene
  memory.
- Automatic final verification that re-reads the produced video.
- HTTP service with streaming progress, a queue and cancellation.
- Web interface and desktop application.
- H.264 output that plays anywhere, original audio preserved.
