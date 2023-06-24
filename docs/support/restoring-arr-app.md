## Summary

You can use [File Browser](/Apps/File_Browser) to restore backups when your Arr apps complain about malformed databases!

## Process

Many apps will create regular, scheduled backups.

Before you restore, **uninstall** the app via your [account](https://elfhosted.com/tenant/apps/0), to avoid any conflict re the restored files. 

Next, in File Browser, navigate to `/config/<app>/.migrated-to-tmpfs`. These are copies of the (corrupt) database stored in the event of an unhealthy pod shutdown. Delete the contents of `/config/<app>/.migrate-to-tmpfs` (*else the corrupted files will just be restored on the next app start*).


In `/config/<app>/Backups`, identify and the most recent backup by sorting the files by date:

![Download compressed backup files](/readarr-2.png)

Download and unpack the backup locally, then navigate to the root of the app's directory in `/config/<app>`, and upload the unpacked backup files:

![Upload uncompressed backup files](/readerr-3.png)

You'll be prompted to overwrite the existing files (this indicates that you're restoring to the correct directory)

![Overwrite existing files with backup](/readarr-4.png)

Finally, **install** the app again via your [account](https://elfhosted.com/tenant/apps/0) :thumbsup:

