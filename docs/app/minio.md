# Minio

## What is it?

Minio is an enterprise-scale object storage platform with an S3-compatible API and a polished web console

## How do I use it?

Once you've enabled it in [your account](https://elfhosted.com/tenant/apps/0), launch the console via your dashboard. 

> Make sure SSO/Auth0 is **disabled** for your minio app, or you won't be able to connect via the console, or via clients like mc or rsync
{.is-warning}

Login with your username and **initial** password (*not synced with auth0*)

From the console, you can navigate your media data.

## Changing your password

Since Minio is exposed directly to the internet without SSO, it's wise to change your password ASAP, to avoid minio's endpoint being used to brute-force your account password (*initially your ElfHosted and Minio passwords are the same*).

Minio console doesn't allow an administrator to change their own password, but there's a simple workaround...

1. Log into Minio console using your existing (*initially chosen*) credentials
2. Navigate to Identity -> Users, and create a new, temporary user. Give this temporary user the `consoleAdmin` policy.
3. Log out, and log into Minio as the temporary user you created
4. Navigate to Identity -> Users, and change the password for your initial admin user
5. Log out, and log into Minio as your intial admin user with a the new password
6. Delete the temporary user.


## Sharing a file/folder externally

Minio features the ability to generate a unique, shareable link to individual files. Check the box next to the file, and choose "Share "from the action list which pops up to the right:

![minio-share.png](/minio-share.png)

If you have lots of files to share, you could combine this feature with [PrivateBin](/Apps/PrivateBin) to share a long list of download links, prettified with Markdown! :thumbsup:

## S3 Browser
- https://s3browser.com/

Be sure Account type says [S3 Compatible Storage]

The REST endpoint is your Minio URL
- eg [username].minio.elfhosted.com

The Access Key ID is your username (not email)
The Secret Access Key is your password for Minio from how you login

Account configuration
![s3browser1.png](/s3browser1.png)

## Transferring with mc
- https://docs.min.io/docs/minio-client-quickstart-guide.html
Download the correct client for your OS

1. Once downloaded, you'll need to open command prompt and `cd` to the correct folder mc is stored in.  Run a `mc.exe --help` (assuming you're using Windows) to verify it can see it. 
2. Set your alias to your Minio client. 
`.\mc.exe alias set ElfHosted https://[username].minio.elfhosted.com [username] [password] --api S3v4`
3. Run a `ls` to verify you can see the Minio buckets
`.\mc.exe ls ElfHosted`
![mc-ls-ElfHosted.png](/mc-ls-ElfHosted.png)
4. After that it's just as simple as doing a `.\mc.exe cp [source file] ElfHosted/[folder]`
More examples can found directly on the Minio site - https://docs.min.io/docs/minio-client-complete-guide.html#cp

## Transferring with rclone

- Append this to your rclone config file to access your buckets remotely. The remote name is `spl`. For more information on what commands can be run, visit https://rclone.org/

  `[spl]`
  `type = s3`
  `provider = Other`
  `access_key_id = <username>`
  `secret_access_key = <password>`
  `endpoint = https://<username>.minio.elfhosted.com`

### Never setup rclone before? 
- Process is straight forward for any OS you're using. 
	Download and install for your OS here - https://rclone.org/downloads/

1. Once installed run `rclone config` to start the server setup process

`n)` New Remote
name> `Minio` (or whatever you want)
Storage> `5` (Amazon S3 Compliant Storage)
provider> `22` (Other compatible S3 Storage)
> Do not select Minio as the provider, else you'll get cert errors
{.is-warning}

env_auth> `1`
access_key_id> `your username`
secret_access_key> `your minio password`
region> `leave blank`
endpoint> `https://username.minio.elfhosted.com`
location_constraint> `leave blank`
acl> `1`
server_side_encryption> `1`
sse_kms_key_id> `leave blank`
Edit advanced config? `n`
Then Keep - `y`
Quit config - `q`

![minio-rclone.png](/minio-rclone.png)

2. Your connection is configured you can run a command to list the buckets (folders) in your client
- `rclone lsd Minio:`

![minio-rclone-list-buckets.png](/minio-rclone-list-buckets.png)

3. You can now start transfering content over via `copy` or `sync` commands. 

![minio-rclone-copy.png](/minio-rclone-copy.png)

> If you recieve a 409 conflict error, try adding the `--s3-no-check-bucket` parm
{.is-warning}

- You can play with `--transfers 1` `--fast-list` and `--checkers 50` to speed up some transfers. The obvious limiting factor will be your upload speed from your provider in how fast data is transfered to Minio. 

> If you receive 429 errors, you are making too many simultaneous requests to your Minio backend. Use `--tpslimit=5 --tpslimit-burst=10` (See https://rclone.org/docs/#tpslimit-float for details)
{.is-warning}


## Other clients for Minio connections
Some users have reported better success than S3 Browser with the following clients, but please be aware they have not been tested by support. 

- http://martins.ninja/RcloneBrowser/

## How do I get support?

1. For general use of the application itself, refer to the [upstream project](https://min.io) or the [subreddit](https://www.reddit.com/r/minio).
2. For specific support re your ElfHosted configuration / account, either consult the #[elf-friends](https://discord.com/channels/396055506072109067/1118645576884572303) channel, or call for [#elf-care](https://discord.com/channels/396055506072109067/1119478614287712337).

## Useful links

* https://min.io
* https://www.reddit.com/r/minio/