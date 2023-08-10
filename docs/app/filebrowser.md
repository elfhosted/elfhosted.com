---
title: sElfHosted Filebrowser 🪄 FREE
description: File Browser lets you interact with your files through a quick and beautiful web interface.
slug: Filebrowser
upstream: https://filebrowser.org
---

# {{ page.meta.slug }}

File Browser lets you interact with your files through a quick and beautiful web interface.

File Browser is particularly useful for:

* Viewing app logs / config in `/config`
* Launching [ElfBot][elfbot]

{% include 'app_access.md' %}
{% include 'app_footer.md' %}

## Solutions to common issues

### No folders appear

If no folders appear at all in FileBrowser, then some of the network storage may have been detached (*perhaps a trasient issue with the provider*). Use [ElfBot][elfbot] to restart FileBrowser itself, with `elfbot restart filebrowser`, and then refresh the UI in a few minutes to confirm whether the storage has appeared.

### Unable to move files (401 error)

Filebrowser [can't](https://github.com/filebrowser/filebrowser/issues/1177#issuecomment-740522710) **move** files between `/storage/` mounts. Perform a copy, and then a separate delete. However, take care when attempting to copy large files, since (a) storage can be slow, and (b) FileBrowser doesn't give you any feedback re the status of your task, so it's impossible to know whether it's completed a copy or not.