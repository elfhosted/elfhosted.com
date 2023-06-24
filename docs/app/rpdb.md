---
slug: RPDB
description: RPDB-Folders monitors media folders and adds images with ratings (*poster.jpg / background.jpg*) from the RPDB API
upstream: https://github.com/RatingPosterDB/rpdb-folders
links:
- name: patreon
  uri: https://www.patreon.com/rpdb/posts
---

# {{ page.meta.slug }}

RPDB-Folders monitors media folders and adds images with ratings (*poster.jpg / background.jpg*) from the RPDB API.

{% include 'app.md' %}
{% include 'app_access.md' %}

## How do I use it?

You'll need to subscribe to RPBD via Patreon in order to get an [API key](https://ratingposterdb.com/api-key/).

Once you've entered your API key into the UI, use the "Add Movie Folder" or "Add Series Folder" button to add a folder.

Instead of browsing for a folder, click in the text box illustrated below..

![Right-clicking a folder in RPDB](/images/rpbd-1.png)

Manually type in the path to your movie/series folder (starting with `/storage/elfhosted`), and click "Save Location":

![Choosing a location for a movies/series folder in RPDB](/images/rpdb-2.png)

{% include 'app_footer.md' %}