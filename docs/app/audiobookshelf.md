---
title: 🧝 Hosted AudioBookshelf 🎧 from $0.05/day
slug: Audiobookshelf
upstream: https://www.audiobookshelf.org
sponsorship: 
- name: GitHub Sponsors
  uri: https://github.com/sponsors/advplyr
links:
- name: Official Subreddit 
  uri: https://www.reddit.com/r/audiobookshelf
- name: Discord server
  uri: https://discord.com/invite/pJsjuNCKRq
- name: GitHub repo
  uri: https://github.com/advplyr/audiobookshelf
- name: App (Google Play)
  uri: https://play.google.com/store/apps/details?id=com.audiobookshelf.app
- name: iOS app (Testflight)
  uri: https://testflight.apple.com/join/wiic7QIW
title: Audiobookshelf
description: Audiobookshelf is an audiobook and podcast streaming server, with native Android / iOS apps
---

# {{ page.meta.slug }}

Audiobookshelf is an audiobook and podcast streaming server, with native [Android](https://play.google.com/store/apps/details?id=com.audiobookshelf.app) / iOS ([testflight](https://testflight.apple.com/join/wiic7QIW)) apps.

{% include 'app.md' %}

Features include:

* Fully open-source, including the android & iOS app (in beta)
* Stream all audio formats on the fly
* Search and add podcasts to download episodes w/ auto-download
* Multi-user support w/ custom permissions
* Keeps progress per user and syncs across devices
* Auto-detects library updates, no need to re-scan
* Upload books and podcasts w/ bulk upload drag and drop folders
* Backup your metadata + automated daily backups
* Progressive Web App (PWA)
* Chromecast support on the web app and android app
* Fetch metadata and cover art from several sources
* Chapter editor and chapter lookup (using Audnexus API)
* Merge your audio files into a single m4b
* Embed metadata and cover image into your audio files (using Tone)
* Basic ebook support and e-reader (experimental)
  
{% include 'app_access.md' %}

## How do I use it?

Upon launch, you'll be prompted to create a username/password. Once this is completed, you'll be able to access the app, and configure your users, libraries, etc.

By default, `/storage/elfstorage/audiobooks` is the intended location for audiobooks (*note this is separate from `/storage/elfstorage/books` intentionally*)

To connect to other apps, refer to [this documentation][connect-apps]
  
## Integrating with Readarr

While [Readarr][readarr] is able to search for and download both ebooks and audio books, having both formats in one target folder (`/storage/elfstorage/books`) causes import errors due to [Calibre][calibre] integration, and results in a messy Audiobookshelf library.

A cleaner solution is to install our `Readarr (Audio)` app, which is simply another instance of Readarr, intended to be dedicated to audio books. `Readarr (Audio)` is pre-configured with the "Spoken" profile, and `/storage/elfstorage/audiobooks` as root media folder.

You can now manually add desired audiobooks to `Readarr (Audio)`, or configure a list import to automatically sync your regular Readarr library, so that you effectively end up with 2 Readarr instances, one searching for ebooks, and the other searching for audio books.

{% include 'app_footer.md' %}