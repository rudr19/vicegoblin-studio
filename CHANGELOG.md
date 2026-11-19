# Changelog

All notable changes to ViceGoblin Studio are recorded here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project uses
[Semantic Versioning](https://semver.org/): MAJOR.MINOR.PATCH.

- MAJOR: changes that break how you use the app or your saved projects.
- MINOR: new features that keep working with your existing projects.
- PATCH: bug fixes and small improvements.

## [Unreleased]

## [1.2.6] - 2026-11-19

### Added
- **The app opens in its own window**, like a normal Windows program: its own title bar, icon and taskbar button, a short start screen, and a full-window welcome the first time. Closing the window quits the app (it asks first if clips are being made or a recording is running). Starting the app a second time brings the open window to the front. The window uses Microsoft Edge WebView2, which comes with Windows 11; if it is missing the app opens in your browser as before, and `--browser` forces that.
- **Clips start and end on a sentence boundary.** A cut that would begin or stop in the middle of a sentence moves by up to 3 seconds to the nearest clean start or end (never into another clip). On by default, with a switch in Settings.
- **Words to spell right:** a list of names, brands and slang in Settings that the captions try to spell your way.
- **Caption size and position** (small, medium, large; automatic, top, middle, bottom) in Settings.
- **Style presets:** save the clip count, length, caption style, layout and caption size and position under a name and apply them in one click.
- **Download pack:** one zip per clip with the video, a cover picture, the title, the description and the captions, ready to post.
- **Try the demo video:** a one-minute demo video comes with the app so a new user can see a result in a minute.
- **Open a file where it is:** "Choose a file on this PC (no copy)" reads a very large video in place instead of copying it into the app first. The app never moves, copies or deletes the original.
- **Watch folder** (off by default): new videos dropped into a folder you choose become projects by themselves, one at a time. Videos already there when you switch it on are ignored; originals are copied, never moved.
- **Live preview of a recording:** the Live recording page shows a recent picture from the stream (a new one every few seconds), how long it has run, the file size and how many marks you pressed, so you can see it is really going on. The sidebar shows the running time too, and running projects show how long they have run. The preview is read-only and adds no load to the recorder; a stream that sends a picture only every 8 seconds or more may show "waiting for the first picture".
- **Time left** while clips render, worked out from the clips already finished.
- **Plain-language messages for source-file problems** (file open in another program, missing, disk full, damaged, out of memory), with a next step and no file paths.
- **Retry or resume** any failed or interrupted project from its saved video, reusing the saved transcript so you do not wait again.
- **Hook and title suggestions from what is said** in each clip, without an AI key (switch in Settings; your own text is never replaced).
- The project says in one sentence **why fewer clips were made** than you asked for.

### Improved
- **The demo video** is now a designed, animated explainer (scenes, moving graphics, a live waveform and a computer voice made on the build PC) instead of a plain gradient; it is still original, with no third-party footage or music.
- **Settings page** redone: six sections with a jump bar and a save bar that says when changes are not saved.
- **Motion:** the app fades in, pages slide up a little and buttons answer touches (all switched off if Windows is set to reduce motion).
- **A recording is visible on every page:** a red "Recording ... keeps going" pill in the sidebar and a mark in the window title, so it never looks stopped when you are on another page.
- **Text you typed** in the link box and the Live recording fields is kept when you switch pages; leaving Settings with unsaved changes asks first.

### Fixed
- The first-run welcome screen almost never appeared on a normal install (the app opened before it had decided to show it).
- A very short clip no longer fails to get a cover picture.

### Notes
- Google sign-in for YouTube still opens in your normal browser (Google does not allow it inside an app window); the browser gets a one-time ticket first so it can finish the sign-in.
- Tested on Windows 11. The app window needs WebView2.
- This build adds about 7 MB of components for the window.


## [1.2.5] - 2026-11-19

### Security
- **Signed updates.** From this version on, the app only installs an update whose release manifest is signed with the publisher's key, and it refuses anything unsigned, tampered, signed with a different key, or older than the version you have. Updating *to* 1.2.5 still works as before; updates *after* it need the signature.
- **The access key changes every launch** and is handed to your browser through a one-time ticket, so it never appears in a web address or on a command line. The key file can only be read by your own Windows user. A program running as you can still read it: this protects against web pages, other devices and other Windows users, not against malware already on your account.
- A request that is rejected (wrong header or no sign-in) no longer risks a "connection aborted" error instead of a clear refusal.
- The README now says plainly who can read the access key and that the update check contacts `api.github.com` by default (you can turn it off in Settings, under About).

### Added
- **Videos with no audio** now make clips from the parts that move, with a one-sentence note that no speech was found, instead of failing with a blank message.
- **Audio track choice:** when a video has several audio tracks (for example game plus microphone), the app picks the one with the most speech, tells you which one it used, and lets you switch.
- **Uninstall** asks whether to delete your projects and settings (default: keep, with the folder size shown) and always removes the access key.
- **Downloader fixes without a reinstall:** the format choices for the downloader live in a small signed settings file that the app can refresh (only when the update check is on). A bad or unsigned file is ignored and the built-in copy keeps working.

### Improved
- **Plain-language downloader errors** with a next step (private video, age restriction, login needed, not available in your country, local or network address, no internet, too many requests). Internal addresses, tracebacks and file paths no longer appear in messages.
- **4K video uses far less memory** while rendering: the first step peaked at about 2,054 MB before and 361 to 530 MB now, and a 4K clip renders noticeably faster.

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
