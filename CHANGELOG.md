# Changelog

All notable changes to ViceGoblin Studio are recorded here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project uses
[Semantic Versioning](https://semver.org/): MAJOR.MINOR.PATCH.

- MAJOR: changes that break how you use the app or your saved projects.
- MINOR: new features that keep working with your existing projects.
- PATCH: bug fixes and small improvements.

## [Unreleased]

## [1.2.4] - 2026-11-18

### Fixed
- **Download button really works now.** It was dimmed and ignored every click until "I watched it" was ticked, so the "Download it anyway?" prompt added in 1.2.2 could never appear. The button is now normal and asks if you have not watched the clip yet.

## [1.2.3] - 2026-11-18

### Added
- **Diagnose and fix** button right on failed project cards, and **Delete failed projects** in one click on the Projects page.

### Changed
- **Quality never drops below 720p.** The download quality choices are now 720p and 1080p, and a live recording on a slow connection can fall back from 1080p to 720p but never lower. Older settings of 480p or 360p now mean 720p.

### Fixed
- **Black console windows no longer flash while the app works.** Helper programs (ffmpeg, the downloader, the recorder) now start hidden.
- **Projects page no longer flickers:** the clip thumbnails were redrawn on every refresh, so they kept reloading and showing blank. The list now only redraws when something actually changes.
- One clip failing to render no longer throws away the clips already made; the others are kept and a note says which failed.
- Render errors now say why (for example "Invalid data found in input") instead of showing a command line.
- An expired YouTube sign-in (Google ends it after 7 days for apps in Testing mode) is forgotten with a clear message, so the app asks you to Connect again instead of failing every upload.
- Scheduled uploads show a note that YouTube may keep them private if your Google app is unverified.
- The upload queue can no longer miss an item added just as it finishes, and the app page cannot be shown inside another website's frame.

## [1.2.2] - 2026-11-18

### Fixed
- **Download looked broken:** the Download button did nothing until "I watched it" was ticked, and the only hint was a 2-second popup. It now asks "Download it anyway?" and downloads.
- The "tick the box" step before Publish and batch uploads now highlights the box with a message that stays until you tick it, instead of a brief popup.
- Popup messages stay on screen longer when they are long.
- When the app has been closed or updated, the page now shows a clear banner (and reconnects by itself) instead of "Failed to fetch".

## [1.2.1] - 2026-11-18

### Added
- **Diagnose and fix:** a failed project now has a button that explains in plain words what probably went wrong (slow internet, YouTube sign-in, missing YouTube support, a stream that was not live, low disk space) and applies the fix with one click (set up YouTube support, update the downloader, install missing tools, pick a browser sign-in, lower the default quality). It also builds a copy-and-send report with links and your Windows user name hidden.
- Each project keeps a short event log (what the app did and when), shown in that report.
- **Live recording adapts to your internet speed:** if the connection cannot keep up with the stream, the app steps down from 720p to 480p, 360p or 240p by itself in the first minutes instead of recording almost nothing.

### Fixed
- **Live recording from a YouTube link:** a pasted watch, live or youtu.be link now records that stream directly instead of first asking YouTube which channel it belongs to (that lookup failed with "Could not tell which YouTube channel"). If a link cannot be read but a channel is typed, the typed channel is used. When YouTube is limiting the PC, the message now says so in plain words. YouTube lives are now recorded with yt-dlp using your chosen browser sign-in (more reliable than before), and a failed recording explains why.

## [1.2.0] - 2026-11-18

### Added
- **Fix captions:** correct spelling or names in a clip's captions, then re-render (Transcript tab).
- **Subtitle files:** download a clip's captions as .srt or .vtt.
- **Where this clip fits:** shows which platforms (Shorts, Reels, Facebook Reels, Moj/Josh/ShareChat) the clip length suits.
- **Download quality** setting (480p, 720p, 1080p) for people on slow data plans.
- **Storage** card in Settings: see disk use per project and delete a project's big original video to free space.

## [1.1.2] - 2026-11-18

### Security
- The app now needs a private key that its own shortcut passes to your browser. Other programs on the PC, or other Windows users, can no longer control it (publish to your YouTube, read your videos, change settings).
- Project, clip and channel names from requests are now strictly checked, closing ways to delete or read files outside the app's own folders.
- A pasted link must start with http:// or https:// and is passed to the downloader safely.
- The updater accepts only github.com and githubusercontent.com addresses, checks the version name, and will not restart the app while a recording, render or upload is running.
- The optional Claude Code helper now runs with all tools turned off in an empty folder.

### Fixed
- **Stop and Quit now really stop a live recording** (the recorder used to keep running and filling the disk).
- A new live recording can no longer re-cut the previous recording's video.
- Clips no longer stay stuck on "rendering" or "uploading" after the app was closed in the middle.
- Settings, YouTube tokens and projects are saved safely, so a crash or full disk cannot leave a half-written file.
- Bad video-range requests no longer cause errors, and a bad upload request no longer leaves a huge temporary file behind.

## [1.1.1] - 2026-11-18

### Fixed
- **Only one copy of the app runs at a time.** Opening the app a second time (for example a double click on the shortcut) used to start a second copy that shared the same address, so projects seemed to vanish and Quit only closed one copy. A second launch now just opens the running app.

### Security
- Saved keys (Gemini, Claude, and the YouTube client secret and tokens) are now stored encrypted with Windows' own protection (tied to your Windows account) instead of plain text. Older files are upgraded automatically the first time the new version starts.

### Improved
- Easier to read: the green, amber and red status labels, links and form labels now meet accessibility contrast and size guidelines in both light and dark mode, and small buttons are larger.
- Each screen has its own page title.
- The Quit button is now a quiet text button, so it is harder to click by accident.

## [1.1.0] - 2026-11-18

### Added
- Quit button (sidebar and Settings) so the app can be closed properly.
- Rotating log file and a "Copy diagnostics" button for bug reports (no keys or file contents are included).
- Speech model manager: download Small, Medium or Large models with a progress bar, cancel, remove, and stall detection. If a download fails, the job continues with the built-in model.
- "Update downloader" button that updates yt-dlp inside the app when YouTube changes break link downloads.
- "Update now": when a new version is out, the app downloads it, checks its SHA-256 checksum, and installs it for you.
- Indian-language captions: the caption font is chosen per script (Devanagari, Bengali, Gurmukhi, Gujarati, Tamil, Telugu, Kannada, Malayalam use Nirmala UI; Arabic script uses Segoe UI). Conjuncts and vowel signs were verified to render correctly.
- Smart defaults for YouTube sign-in: the app lists only the browsers installed on the PC (Firefox recommended). If a link needs a sign-in, the failed project shows one-click buttons that save the choice and retry. Failed link downloads also get a "Try again" button and now show the real reason instead of a generic error.
- Automated tests (`tests/test_core.py`).

### Fixed
- Speech model downloads no longer hang on networks where the Xet transfer protocol stalls (plain HTTPS is used).

### Changed
- **Smaller download and install.** The installer went from 283 MB to about 194 MB, and a fresh install takes about 463 MB on disk instead of about 770 MB. ffprobe, the bundled Deno runtime, PyAV's copy of ffmpeg libraries and unused packaging tools are no longer shipped. Link downloads from YouTube set up Deno once, the first time they need it (about 40 MB). Upgrading removes the old extras automatically.
- Video length is now read with ffmpeg itself, so ffprobe is not needed.
- Third-party notices now state that the bundled ffmpeg is a GPL v3 build and give the source location.

## [1.0.1] - 2026-11-18

### Changed
- Neutral defaults for everyone: clip titles are now "<source> - moment at mm:ss" and descriptions no longer carry any channel-specific disclaimer or game hashtags. Description footer is a new setting, "Default hashtags" (starts as `#Shorts`).
- Uploaded files now name the project after the file instead of "my video".

### Fixed
- Videos with no speech now say "No speech was found" instead of the misleading "No whisper found".

## [1.0.0] - 2026-11-18

First public release.

### Added
- One-click Windows installer with everything included: video engine (ffmpeg), speech recognition (faster-whisper) with a bundled `base` model, link downloader (yt-dlp), live recorder (streamlink) and the Deno runtime YouTube needs. No admin rights, no terminal.
- "Getting everything ready" start-up screen: the app checks every tool and only opens when all are ready.
- Projects, and a clip editor with a timeline trim, transcript view, caption styles (Clean, Bounce, Hype, None), three vertical layouts, voice-over mixing and per-clip re-render.
- Language and accuracy settings for captions.
- YouTube connection with your own Google key: publish a clip, or batch-schedule several clips at set times. Nothing uploads without your confirmation.
- Optional AI clip picking with a Gemini key or the Claude Code login.
- Mobile-friendly layout.
- In-app version number and "update available" notice (can be turned off in Settings).
- Licence agreement and third-party notices in the install folder.

### Security
- The app code ships compiled, with no readable source in the install folder.
- Keys and projects stay in the install folder's `app\data` and are never sent to us.
