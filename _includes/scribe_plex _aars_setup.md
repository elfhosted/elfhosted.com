### Connect Aars to Plex

After Radarr/Sonarr add content to your library, we need them to tell Plex about the change, so that Plex can rescan/update the library and make the new content available for streaming.

The following guide illustrates the high-level process to establish this connection.

1\. Navigate to the Sonarr / Radarr instance (*this will need to be repeated for each Arr instanc*e)


2\. Click on `Settings` -&gt; `Connect` , and on the `+` sign to add a connection

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/c7f3eac2-ece2-4fed-9006-d19f187a82ed/ascreenshot.jpeg?tl_px=0,0&br_px=2116,1538&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=387,221)


3\. Choose "Plex Media Server"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/38795558-6b76-4f22-8233-5e3db6c48222/ascreenshot.jpeg?tl_px=0,0&br_px=2116,1538&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=690,269)


4\. In the `Host` field, type in `plex` (*this is the hostname of your Plex instance from the perspective of the Aar*)

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/4bab30ac-8287-4712-aa9b-cf004dae60f5/ascreenshot.jpeg?tl_px=0,0&br_px=2116,1538&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=232,339)


5\. Click "Authenticate with [Plex.tv](http://Plex.tv)"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/0a7cf7c6-12cd-4eba-af85-c301326279c7/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=256,566)


6\. Sign in and approve the connection

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/9cc28e53-bc38-4cb0-8624-4f28d5477ca4/user_cropped_screenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=526,524)


7\. Click "Test"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/9b8e4235-3b7b-4442-8722-fb62b2cf9cf4/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=669,701)


8\. Click "Save"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/c1febf27-a0b5-4717-baac-582b68c3d354/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=835,695)


9\. Confirm that the **only** connection configured is `Plex Media Server` (*if "Autoscan" exists, then delete it*)

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/f18942b1-29ff-47b8-8b09-e2a648d4ae62/ascreenshot.jpeg?tl_px=0,50&br_px=2116,1589&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=442,371)


10\. Repeat this process for each Radarr / Sonarr instance!