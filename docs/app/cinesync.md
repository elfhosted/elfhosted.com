---
title: 🧝 Hosted CineSync 📚
slug: CineSync
description: CineSync uses smart symlinking to organize your debrid libraries for tidy streaming from Plex
upstream: https://github.com/sureshfizzy/CineSync
links:
- name: Discord
  uri: https://discord.gg/BtZYTCQtAR
sponsorship: 
- name: Buy Me A Coffee
  uri: https://buymeacoffee.com/Sureshfizzy
- name: Patreon
  uri: https://patreon.com/sureshs
- name: PayPal
  uri: https://www.paypal.me/sureshfizzy
---

# {{ page.meta.slug }}

CineSync is a Python-based library management system designed to efficiently organize debrid libraries for Movies & TV shows, eliminating the need for [Sonarr][sonarr]/[Radarr][radarr]. Users downloading from [Debrid Media Manager (DMM)](https://debridmediamanager.com) can seamlessly sort their library into seasons, whether it's a single file or a folder. 

CineSync streamlines the organization of your library and creates symbolic links, providing full control over your data locally. While highly optimized for debrid platforms, CineSync is also versatile and works effectively with non-debrid platforms.

{% include 'app.md' %}

Features

- **Library Organization:** Easily sort your library into seasons, regardless of file or folder structure.
- **Faster Scan:** CineSync has been optimized for faster file and directory scanning. Improved directory checks, file handling, and multi-threaded processing (controlled by `MAX_PROCESSES`) help speed up the scan process, especially for large libraries.
- **Symbolic Link Creation:** Create symbolic links to organize your library without moving or duplicating files.
- **Real-Time Monitoring for Files:** Monitor the watch directory for any new files and automatically create symbolic links for them, ensuring your library stays updated in real-time. (Configurable monitoring interval via `SLEEP_TIME`).
- **Support for Single Symlinks Creation:** CineSync now supports creating symbolic links for single files or folders, providing flexibility in managing your library.
- **Ability to Skip Already Present Symlinks:** CineSync includes the ability to skip the creation of symbolic links for files or folders that are already present, even if the folder name is different. This feature ensures efficient management of your library by preventing duplicate symlinks.
- **Rename Files:** Properly rename your files based on TMDb data when `RENAME_ENABLED=true`.
- **Cross-Platform Support:** Works on both Linux and Windows operating systems.
- **Movie Collection-Based Separation:** Organize movies into collections based on TMDb or IMDb data, ensuring that all movies from the same collection are grouped together. (Enabled via `MOVIE_COLLECTION_ENABLED`).
- **Docker Support:** Easily deploy CineSync in a Docker container for consistent and isolated environments.
- **TMDb/IMDB/TVDB ID Integration:** Utilize TMDb/IMDB/TVDB IDs for more precise organization and naming of your media files.
- **Automatic Separation of Extras and Resolutions:** Automatically separate extras from main episodes and sort files based on resolution (e.g., 720p, 1080p, 4K), ensuring a well-organized library. (Configurable via `SKIP_EXTRAS_FOLDER`).
- **Resolution-Based File Sorting:** Separate files based on resolution (e.g., 720p, 1080p, 4K) for easier organization. If resolution-based separation is not enabled, files will be organized based on the source folder structure.
- **Database Configuration:** Optimized for efficient database operations with configurable throttle rates, retry mechanisms, and batch processing to manage media metadata and symlink creation. (Controlled via `DB_*` variables).
- **Rclone Mount Verification:** CineSync supports checking if rclone mount points are available before processing files. This feature is useful for managing remote storage and ensures the mount is active before symlink creation. (Enabled via `RCLONE_MOUNT`).

{% include 'app_access.md' %}

## How to use CineSync

Point your Plex libraries to `/storage/symlinks/CineSync/Movies` and `/storage/symlinks/CineSync/Shows`.

An explanation of the various ENV var can be found [here](https://github.com/sureshfizzy/CineSync/wiki/Configuration), but sensible, ElfHosted defaults have been pre-applied. 

The only value you **need** to set, is your Plex token (*generate one [here][plex-token]*), by running `elfbot env cinesync PLEX_TOKEN=<your generated plex token>`

Your `SOURCE_DIR` will be pre-setup, based on your ElfHosted debrid storage mounts, although you can override this using `elfbot env cinesync SOURCE_DIR=whatever`.

{% include 'app_footer.md' %}
