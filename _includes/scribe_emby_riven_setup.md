This guide illustrates how to connect Riven to Emby. At present, this is not as polished a process as the Riven/Plex setup, and requires manual generation of an API key in Emby, and configuration directly into the Riven settings.json (*i.e., it's not configurable via the Riven frontend*)

1\. From your ElfHosted dashboard, launch Emby

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/cfdebf78-2686-4a86-97dc-f99cfcdac939/ascreenshot.jpeg?tl_px=0,719&br_px=1719,1680&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=174,277)


2\. Select your preferred display language and click "Next"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/6435428f-79d4-4951-9ac1-e2e9921cda19/ascreenshot.jpeg?tl_px=0,177&br_px=1426,1138&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=928,341)


3\. Create your first user

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/0f59358d-dfa5-42ce-9c76-7f4e29e2ccf9/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=930,455)


4\. Click "New Library"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/bfb738e9-c93d-428e-8e2d-d5e47ac6facd/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=551,177)


5\. Select the "Movies" option.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/73372606-4206-49bd-9b44-ce5728ae9042/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=347,311)


6\. Click "Add"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/7b5b5e01-433e-46fe-a2c0-6152aa34df3b/ascreenshot.jpeg?tl_px=0,297&br_px=1426,1258&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=315,341)


7\. Choose "/storage/symlinks"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/40056446-5e4d-4f0c-bc2a-dad79ab93fd6/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=395,395)


8\. Click "movies"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/b02efe68-b847-4df0-b365-6da07e9a4871/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=362,395)


9\. Click "OK"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/4d978070-2f74-4da2-b3fe-fe7ae44c7b14/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=461,583)


10\. Ensure video preview thumbnails are set to [[Never]]

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/3124ac8c-612d-42c7-86b1-4ba9b3dbe592/user_cropped_screenshot.jpeg?tl_px=0,200&br_px=1426,1161&force_format=jpeg&q=100&width=1120.0)


11\. Click "OK"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/222ee4ad-8de3-493c-9c11-2caa8aa51347/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=501,594)


12\. Repeat to add TV shows - Click "New Library"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/065744d2-8db7-4fb0-914a-64a56fbb3750/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=564,163)


13\. Select the "TV shows" option.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/1b4af764-1269-4b83-b6d4-6cd838317d59/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=465,301)


14\. Click "Add"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/2dc8eb46-37df-469e-b6ec-15f2cbd07c02/ascreenshot.jpeg?tl_px=0,309&br_px=1426,1270&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=328,341)


15\. Click "/storage/symlinks"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/71747b5e-4f2f-45ed-94b6-95151d52b7f6/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=333,360)


16\. Click here.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/3a7459d4-13ad-4115-afc2-4f2d166b5295/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=213,375)


17\. Click "OK"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/2bfd327d-6d86-4125-a5e4-970f5642c5f3/user_cropped_screenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=498,576)


18\. Ensure that both Video Preview Thumbnails and Markers are set to [[Never]] (incompatible with remote mounted media)

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/aa018bd6-6fe0-420b-b25a-a646996e7971/user_cropped_screenshot.jpeg?tl_px=0,200&br_px=1426,1161&force_format=jpeg&q=100&width=1120.0)


19\. Click "OK"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/66e34ad0-537e-4ce3-afed-83c301fd31ff/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=499,568)


20\. Click "Next"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/de26139a-b2f0-48e5-b328-7bae2b619695/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=604,376)


21\. Click "Next"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/cdb1ceb0-32b7-4c2c-9e9a-ad39b97b299f/ascreenshot.jpeg?tl_px=0,55&br_px=1426,1016&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=923,341)


22\. Accept the terms and click "Next"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/a727c060-15d6-49b8-8dfb-9cb9a8faa193/ascreenshot.jpeg?tl_px=0,161&br_px=1426,1122&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=900,341)


23\. Click "Finish"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/1e877fc5-eaa4-4f0a-a679-0693ac250b89/ascreenshot.jpeg?tl_px=0,147&br_px=1426,1108&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=931,341)


24\. Perform a manual login

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/f6d5c40f-d7a0-4ed1-a921-7288d72c3d5e/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=408,227)


25\. Sign in with chosen credentials

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/debcd0f8-2551-4171-a5e7-a65699aea006/ascreenshot.jpeg?tl_px=0,229&br_px=1426,1190&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=493,341)


26\. Click on the account icon

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/0f3fb2ec-c6fe-4d7c-afce-bfefb0349793/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=1016,23)


27\. Click "Manage Emby Server"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/040113f4-2799-49d8-a244-0319db72cdab/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=787,317)


28\. Click the menu icon

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/b8d4e28a-cb9c-4b85-9e62-36da3e88179c/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=80,17)


29\. Scroll down and click "Api Keys"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/d100fdae-58bc-45dc-a860-fec848476b7b/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=81,345)


30\. Click "New Api Key"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/fc6eace6-5325-497b-81d8-e2ad27edb647/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=515,127)


31\. Name your app "Riven", and click Submit

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/4d577772-68e7-4987-9345-6e1a552f5142/ascreenshot.jpeg?tl_px=0,400&br_px=1426,1362&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=488,406)


32\. Click the menu icon

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/11983c2c-6d61-44d4-9882-d85fbf80d192/ascreenshot.jpeg?tl_px=0,0&br_px=1426,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=985,238)


33\. Click "Copy to Clipboard"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/f87c06a8-211b-4592-978c-d1fc0b915dfa/ascreenshot.jpeg?tl_px=0,187&br_px=1426,1148&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=859,341)


34\. Back on your ElfHosted dashboard, click "FileBrowser"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/0d70213f-60bf-480c-b278-9bb0875631c2/ascreenshot.jpeg?tl_px=0,381&br_px=1426,1342&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=190,341)


35\. Double-click "config"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/4703a031-bce6-465a-95bd-577d6c241e8b/ascreenshot.jpeg?tl_px=0,161&br_px=1426,1122&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=127,341)


36\. Double-click "riven"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/6b54a55a-e464-416f-a10b-59ae41f8c8e9/ascreenshot.jpeg?tl_px=0,0&br_px=1719,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=438,203)


37\. Double-click "settings.json"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/629efacc-56cf-458d-a71d-bf859d04080b/ascreenshot.jpeg?tl_px=0,675&br_px=1719,1636&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=460,276)


38\. Edit the updaters section, disabling Plex (the default), and enabling emby. Paste in the API key, and set the emby URL to `http://emby:8096`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/55b0880c-21ad-4a5f-8e75-adbb7228c874/user_cropped_screenshot.jpeg?tl_px=198,344&br_px=1917,1305&force_format=jpeg&q=100&width=1120.0)


39\. Click "save", and then close

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/7110ec42-bf52-40de-a216-4a9fc12cb90a/ascreenshot.jpeg?tl_px=969,0&br_px=2116,640&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=1027,32)


Tip: Sometimes FileBrowser's saves don't apply. As a best-practice, re-open `settings.json` and confirm that your changes have been effected!


40\. From the ElfHosted apps dashboard, launch [[Riven (backend)]]

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/b6a09ada-4ab5-4590-b10c-54965d964bad/ascreenshot.jpeg?tl_px=154,89&br_px=1873,1050&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=524,277)


Tip: Changes made to the backend directly via `settings.json` are not automatically applied, you need to restart Riven's backend with [[CTRL-C]] and [[ENTER]] to restart


41\. Hit [[CTRL-C]] to stop Riven's backend

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/ebe02b43-f6ac-425f-a134-968bec62eff8/user_cropped_screenshot.jpeg?tl_px=198,344&br_px=1917,1305&force_format=jpeg&q=100&width=1120.0)


42\. When prompted, hit return to reconnect

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/15251da7-7f0e-45f5-aa89-14b175462052/ascreenshot.jpeg?tl_px=190,477&br_px=1909,1438&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=524,277)


43\. Wait for the database reset prompt to expire

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/19fa9b93-5e45-4679-9d12-0f90e1734608/ascreenshot.jpeg?tl_px=0,0&br_px=1719,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=177,116)


44\. Confirm that Riven has initialized the [[Emby Updater]]

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-13/4d3eab54-94a2-4d80-963e-c06d0ac17cfe/user_cropped_screenshot.jpeg?tl_px=270,202&br_px=1417,843&force_format=jpeg&q=100&width=1120.0)


Tip: That's it! Riven will now use the API key to advise Emby to rescan the symlink folders whenever new content is available!