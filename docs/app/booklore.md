---
title: 🧝 Hosted BookLore
slug: BookLore
description: BookLore is a web app for hosting, managing, and exploring books, with support for PDFs, eBooks, reading progress, metadata, and stats.
works_with:
- Readarr
- OpenBooks
upstream: https://github.com/adityachandelgit/BookLore
sponsorship: 
- name: TBC
  uri: https://github.com/adityachandelgit/BookLore/issues/359
links:
- name: GitHub Discussions
  uri: https://github.com/adityachandelgit/BookLore/discussions
---

# {{ page.meta.slug }}

BookLore is a web app for hosting, managing, and exploring books, with support for PDFs, eBooks, reading progress, metadata, and stats. 

[Get a 7-day trial of ElfHosted {{ page.meta.slug }}! :magic_wand:](https://store.elfhosted.com/product/{{ page.meta.slug | lower }}/){ .md-button .md-button--primary }

![Screenshot of {{ page.meta.slug }}](/images/screenshots/{{ page.meta.slug | lower }}.gif){ loading=lazy }

Key Features:

* 📚 Organized Book Management - Categorize books with Libraries and Shelves for easy discovery and structured organization.
* 🧠 Smart Metadata Handling - Automatically fetch book details from Goodreads, Amazon, and Google Books, or edit them manually with fine-grained control.
* 👥 Multi-User Support - Admins can create accounts, assign libraries, and manage permissions for metadata edits, uploads, and downloads.
* 📖 Built-in PDF & ePub Reader - A fast, feature-rich reader for PDFs and ePubs, with customizable reading settings and a clean UI.
* 🌐 OPDS 1.2 Support - Browse and download books through the Open Publication Distribution System – compatible with many reading apps.
* 🔐 Optional OIDC Authentication - Secure access with OpenID Connect, supporting both local JWT authentication and external providers like Authentik.
* 📤 Multi-Book Uploads - Upload multiple books at once with metadata auto-detection and file organization.
* 📧 Send Books via Email - Share books directly with others by sending them via email – quick and easy.
* 🚀 Continuous Improvements - Frequent updates with new features, performance enhancements, and UI improvements. BookLore is perfect for self-hosters who want complete control over their digital library. Stay tuned for updates!

{% include 'app_access.md' %}
{% include 'app_footer.md' %}