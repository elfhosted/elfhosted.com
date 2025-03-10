### Connect Aars to Jellyfin 

When Radarr / Sonarr have added content to your library, they'll need to "reach out" to Jellyfin (using an API key) to request that it scan and update your libraries, so that the content can be streamed.

1\. In Jellyfin, click on the Account icon

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/ea8999c0-da5a-47f5-88ee-52510f521c18/ascreenshot.jpeg?tl_px=0,0&br_px=2116,1538&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=1043,-7)


2\. Click "Dashboard"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/84139ff8-d345-4749-8b3f-27d2f4e0f9b4/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=157,433)


3\. Click "API Keys"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/9c533609-a0b0-457b-b4c1-e8325107bc7c/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=29,574)


4\. Click the `+` button to add a new API key

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/20ec0bd8-0dab-46fa-8ed7-27e43ee55ddc/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=2116,1538&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=370,45)


5\. Name your key (I used "Aars"), and click `OK`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/2677746e-1c3d-4bf1-8b03-1ee1488ea79a/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=510,726)


6\. Copy your API key to the clipboard

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/fb6f2ec7-d81d-48ff-9c1c-835564cb4fdc/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=2116,1538&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=511,288)


7\. Click "Settings"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/7080c120-db99-4338-9e14-d07b36f91dfa/ascreenshot.jpeg?tl_px=0,60&br_px=2116,1599&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=33,371)


8\. In your Aar, click on `Settings` -&gt; `Connect`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/ba6bf414-19ba-4be6-a06b-43124e51deea/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=64,533)


9\. Pick `Emby / Jellyfin`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/2d4e610b-5f39-4c84-b730-6c4b77813639/ascreenshot.jpeg?tl_px=0,42&br_px=2116,1581&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=370,371)


10\. Name the connection `Jellyfin`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/d2a3193d-dd0a-4424-8a56-ed1eaa52ff89/ascreenshot.jpeg?tl_px=0,0&br_px=2116,1538&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=563,192)


11\. Un-check `On Application Update` (optional)

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/99ff596b-6fd5-49a0-9e51-b8bcb811937e/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=185,458)


12\. Press [[cmd]] + [[v]]


13\. Set the following values, and click `Test`, then `Save`\
\
`Host`: `jellyfin`\
`API Key` : `<paste from clipboard>`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/ed62509c-7b1e-465e-a99d-93909ba840d8/user_cropped_screenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=845,699)


14\. The connection is added!

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-02-05/56ced6f7-2b45-4106-9679-ab5ad899a4fb/ascreenshot.jpeg?tl_px=0,111&br_px=2116,1650&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=667,510)


15\. Repeat this process for every instance of Radarr / Sonarr (the same API key can be used)