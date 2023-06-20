# Audiobookshelf

## What is it?

Audiobook and podcast streaming server, with native [Android](https://play.google.com/store/apps/details?id=com.audiobookshelf.app) / iOS([testflight](https://testflight.apple.com/join/wiic7QIW) apps

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


## How do I use it?

Once you've enabled audiobookshelf in [your account](https://elfhosted.com/tenant/apps/0), launch the app via your dashboard. 

Upon launch, you'll be prompted to create a username/password. Once this is completed, you'll be able to access the app, and configure your users, libraries, etc.

By default, `/media/audiobooks` is the intended location for audiobooks (*note this is separate from `/media/books` intentionally*)

To connect to other apps, refer to [Interconnecting-Apps](/Reference/Interconnecting-Apps)
  
## Integrating with Readarr

While [Readarr](/Apps/Readarr) is able to search for and download both ebooks and audio books, having both formats in one target folder (`/media/books`) causes import errors due to Calibre integration, and results in a messy Audiobookshelf library. 

A cleaner solution is to install our `Readarr (Audio)` app, which is simply another instance of Readarr, intended to be dedicated to audio books. `Readarr (Audio)` is pre-configured with the "Spoken" profile, and `/media/audiobooks` as root media folder.

You can now manually add desired audiobooks to `Readarr (Audio)`, or configure a list import to automatically sync your regular Readarr library, so that you effectively end up with 2 Readarr instances, one searching for ebooks, and the other searching for audio books.

## How do I get support?

1. For general use of the application itself, refer to the [upstream project docs](https://www.audiobookshelf.org/docs/), or the upstream [Discord server](https://discord.com/invite/pJsjuNCKRq)
2. For specific support re your ElfHosted configuration / account, either consult the #[elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303) channel, or call for [#elf-care](https://discord.com/channels/396055506072109067/1119478614287712337).

## Useful links

* https://www.audiobookshelf.org
* https://www.reddit.com/r/audiobookshelf/