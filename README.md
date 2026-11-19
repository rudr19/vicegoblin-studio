# ViceGoblin Studio

**Turn long videos, streams and podcasts into captioned vertical Shorts. Free, private, runs on your own Windows PC.**

[![Latest release](https://img.shields.io/github/v/release/rudr19/vicegoblin-studio?label=latest&color=ff4a1c)](../../releases/latest)
[![Downloads](https://img.shields.io/github/downloads/rudr19/vicegoblin-studio/total?color=121110)](../../releases)
![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-121110)
![Price](https://img.shields.io/badge/price-free-d4ff3a)
[![Sponsor](https://img.shields.io/badge/Sponsor-GitHub%20Sponsors-ea4aaa?logo=githubsponsors&logoColor=white)](https://github.com/sponsors/rudr19)

### [Download for Windows](../../releases/latest/download/ViceGoblinStudio-Setup.exe)

No account. No subscription. No terminal. Everything is included in one installer.

**Free, and it stays free.** If it helps you, you can [♥ sponsor it from $1](https://github.com/sponsors/rudr19), monthly or one-time. Nothing is locked behind it.

![Clip editor](docs/editor.jpg)

## What it does

1. **Drop in a long video.** Upload a file or paste a link to a video you own.
2. **Get your best moments.** It transcribes the speech on your PC, scores the strongest moments and cuts vertical clips with a hook and a title.
3. **Edit anything.** Drag the trim handles, fix the captions, change caption style and layout, add your own voice-over, re-render one clip in seconds.
4. **Post it your way.** Download the clip, grab its subtitle file, or connect your own YouTube channel and queue a batch of Shorts hours apart. Nothing uploads until you confirm.

| | |
|---|---|
| ![Projects](docs/project.jpg) | ![New project](docs/new-project.jpg) |
| ![Settings](docs/settings.jpg) | <img src="docs/mobile.jpg" alt="Phone-width view" width="300"> |

## Features

**Captions**
- **Word-by-word captions** in Clean, Bounce or Hype style, powered by Whisper speech recognition (a model is built in, so it works offline).
- **Dozens of languages**, including English, Hindi, Spanish, Portuguese and Arabic. Hindi (Devanagari), Tamil and Bengali are drawn with proper letter shaping (other Indian scripts have not been checked yet). Accuracy differs by language, accent and audio quality. Pick your language in Settings for the best accuracy.
- **Fix captions:** correct a misheard word or a name, then re-render.
- **Subtitle files:** download a clip's captions as `.srt` or `.vtt`.
- **Words to spell right:** list your names, brands and slang and the captions try to spell them your way.
- **Caption size and position:** small, medium or large; automatic, top, middle or bottom.
- **Clean cuts:** a clip starts and ends on a sentence boundary instead of in the middle of a sentence (you can switch this off).

**Editing**
- **Three vertical layouts:** whole frame on a blurred fill, gameplay plus facecam, or follow the action.
- **Timeline and transcript editing** with per-clip re-render.
- **Voice-over mixing** that lowers the original audio under your voice.
- **Style presets:** save the clip count, length, caption style, layout and caption size and position under a name and apply them in one click.
- **Download pack:** one zip per clip with the video, a cover picture, the title, the description and the captions.
- **Audio track choice:** if a video has several audio tracks (for example game plus microphone), the app picks the one with the most speech, tells you which one it used, and lets you switch.
- **Videos with no sound** still make clips, picked from the parts that move, with a short note that no speech was found.
- **Where this clip fits:** shows which platforms (Shorts, Reels, Facebook Reels, Moj/Josh/ShareChat) suit the clip's length. Platform limits change, so check each app before posting.

**Getting clips from anywhere**
- **Upload a file** or **paste a link** to a video you own, or choose a very large file on your PC and the app reads it where it is, without copying it.
- **Try the demo video:** a one-minute demo comes with the app so you can see a result in a minute.
- **Watch folder** (off by default): new videos dropped into a folder you choose become projects by themselves, one at a time. Your originals are copied, never moved.
- **Live recording** from Twitch or YouTube, with a live preview picture, a running timer and a hotkey (F8) to mark great moments. On a slow connection it adapts by itself and never goes below 720p.
- **Optional AI clip picking** with a free Gemini key (or your own Claude Code login).

**Publishing**
- **Batch scheduling to YouTube** with your own Google key. You confirm every upload.

**Looks after itself**
- **Its own window:** the app opens like a normal Windows program, with a start screen, a first-run welcome and a taskbar icon. Closing it quits the app. A recording keeps running while you use other pages, and the sidebar says so.
- **Retry or resume** a failed or interrupted project from its saved video without waiting for transcription again, and **time left** while clips render.
- **Plain-language file errors:** a file open in another program, missing, disk full or damaged gets one clear sentence and a next step.
- **Diagnose and fix:** if something fails, one button explains in plain words what probably went wrong and applies the fix (set up YouTube support, update the downloader, pick a browser sign-in). It can also make a report you can copy and send, with links and your Windows user name hidden.
- **Storage:** see disk use per project and delete a project's big original video to free space.
- **Download quality** of 720p or 1080p.
- **In-app updates, signed.** From 1.2.5 the app installs an update only when it carries the publisher's signature, and refuses anything unsigned, altered, signed by someone else, or older than what you have.
- **Plain-language downloader errors** with a next step (private video, age restriction, sign-in needed, not available in your country, local address, no internet), and no internal addresses or file paths in messages.
- **Lighter 4K:** 4K video renders with about 4 to 5 times less memory in its first step.
- **Uninstall** asks whether to delete your projects and settings (default: keep) and always removes the access key.

**Private and safe by design**
- Your videos, settings and keys never leave your computer. Saved keys are encrypted with Windows' own protection.
- The access key changes every time the app starts and reaches your browser through a one-time ticket, so it never appears in a web address or on a command line.
- The app only answers to its own shortcut. Web pages and other devices on your network are blocked, and the key file can only be read by your own Windows account. A program running as the same Windows user as you can read the access token file, so this does not protect you from malware that is already running under your account.
- **Update check:** by default the app asks `api.github.com` whether a newer version exists and fetches a tiny signed settings file for the downloader from `raw.githubusercontent.com` (normal web requests, no personal data, at start and every few hours). Turn it off in Settings, under About; neither request is made then.
- **Mobile-friendly interface.**

## Install

1. Download `ViceGoblinStudio-Setup.exe` from the [latest release](../../releases/latest).
2. Run it. Windows may say **Unknown publisher** because the installer is new and not yet code-signed. Choose *More info*, then *Run anyway*.
3. Open **ViceGoblin Studio** from the Start menu. It checks that every tool is ready, then opens in its own window.

**Requirements:** Windows 10 or 11 (64-bit; tested on Windows 11), about 8 GB RAM, 5 GB free disk space. The app window uses Microsoft Edge WebView2, which comes with Windows 11; if it is missing the app opens in your browser instead. Mac and Linux are not available yet.

Each release lists a SHA-256 checksum so you can verify your download. From 1.2.5 each release also carries `manifest-<version>.json` and `manifest-<version>.json.sig`: the signed description (version, installer checksum, size) that the app checks by itself when it updates. You normally do not need to do anything with them.

## FAQ

**Is it really free?** Yes. It runs on your PC, so there are no servers to pay for.

**Are my videos uploaded anywhere?** No. Transcription, clipping and rendering all happen on your computer. The only things that leave it are what you choose to send: a YouTube upload you confirm, or text for the optional AI picker.

**What can I clip?** Your own videos, or ones whose owner has given you permission. Reusing someone else's video without permission can get your channel a copyright strike.

**Why does YouTube ask me to sign in?** For some links YouTube wants a login. In Settings, choose the browser you are signed in with. Or just upload the file.

**Why did my live recording capture less than the whole stream?** Live video has to arrive as fast as it plays. If the connection between your PC and YouTube is slower than the stream, the app can only keep part of it. It keeps 720p quality rather than dropping lower, so the clips are made from what was captured. Signing in with a browser (Settings), waiting a while, or using a faster network usually helps. The Diagnose and fix button on a failed project explains what happened.

**The window says it lost connection.** The studio app was closed or updated. Open ViceGoblin Studio from the Start menu again; the page reconnects by itself.

**The app says it cannot verify an update.** It only installs updates signed by the publisher. If a signature is missing or does not match, nothing is installed. Download the installer from the [latest release](../../releases/latest) instead and compare its SHA-256 checksum.

## Support the project

ViceGoblin Studio is free and always will be. Nothing is locked behind a payment. If it saves you time and you would like to help keep it improving, you can [sponsor the project on GitHub](https://github.com/sponsors/rudr19): any amount from **$1**, monthly or one-time. Support would help pay for things like a code-signing certificate (to remove the "Unknown publisher" warning), testing on real PCs and more languages.

Starring the repository and telling a creator friend helps just as much.

## Versions

Releases follow [Semantic Versioning](https://semver.org/). See [Releases](../../releases) for notes on every version, or the [changelog](CHANGELOG.md).

## Help and feedback

Questions and ideas: [Discussions](../../discussions). Bugs: [Issues](../../issues). When you report a bug, press **Diagnose and fix**, then **Copy report**, and paste it in.

---

Licence: shown during install and kept in the install folder (`LICENSE.txt`). Open-source components are listed in `THIRD-PARTY-NOTICES.txt`.
This repository contains release downloads only. ViceGoblin Studio is an independent product and is not affiliated with YouTube or Google.
