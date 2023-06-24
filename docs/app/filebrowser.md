---
slug: Filebrowser
upstream: https://filebrowser.org
---

# {{ page.meta.slug }}

File Browser lets you interact with your files through a quick and beautiful web interface.

File Browser is particularly useful for:

* [Viewing app logs][view-logs]
* Launching [ElfBot][elfbot]

{% include 'app.md' %}
{% include 'app_access.md' %}
{% include 'app_footer.md' %}

## Solutions to common issues

### No folders appear

If no folders appear at all in FileBrowser, then some of the network storage may have been detached (*perhaps a trasient issue with the provider*). Use [ElfBot][elfbot] to restart FileBrowser itself, with `elfbot restart filebrowser`, and then refresh the UI in a few minutes to confirm whether the storage has appeared.