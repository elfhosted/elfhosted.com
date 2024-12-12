# Connect ElfHosted to AllDebrid

1\. Start at your ElfHosted dashboard

2\. Click "Riven (backend)"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/d6ffca49-5ba7-4a99-bfef-a911a2114387/ascreenshot.jpeg?tl_px=456,0&br_px=2176,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=524,103)


3\. Confirm that the Riven backend starts, but pauses due to missing configuration. Ensure that the symlinks path reflects your chosen debrid provider

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/a3373014-39cf-4e68-b163-77680b8ab014/user_cropped_screenshot.jpeg?tl_px=506,332&br_px=2226,1293&force_format=jpeg&q=100&width=1120.0)


4\. Back on your dashboard, launch Riven

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/10b1d269-60ad-44a1-b15a-1231bd0e0171/ascreenshot.jpeg?tl_px=438,359&br_px=2158,1320&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=524,277)


5\. Click "Settings"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/90ec5279-f388-4780-b423-2dc31ae3d5a4/ascreenshot.jpeg?tl_px=1012,0&br_px=2732,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=714,39)


6\. Paste in your AllDebrid API key

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/954b2ee9-3680-418c-ba5e-8e35d25426c3/ascreenshot.jpeg?tl_px=0,664&br_px=1719,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=464,330)


7\. Enable the All-Debrid Proxy option

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/3ff8e6fe-394c-48e4-aa5a-b944d51736c4/user_cropped_screenshot.jpeg?tl_px=0,664&br_px=1719,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=406,382)


8\. A new field appears:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/9a4ddbc3-93b3-42af-8bde-83fd8fd21022/ascreenshot.jpeg?tl_px=0,664&br_px=1719,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=434,464)


9\. 


10\. Type <http://alldebrid:8888> (this forces Riven to use our VPN-connected AllDebrid proxy to access their API, which is otherwise blocked due to our datacenter IPs)

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/ceebf965-b0fa-47d0-b748-977e099355fe/user_cropped_screenshot.jpeg?tl_px=1012,664&br_px=2732,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=827,481)


11\. Click "Save changes"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/c3a74642-6226-4d44-8443-4281d9df741a/File.jpeg?tl_px=1011,664&br_px=2731,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=827,481)


12\. Wait for "Settings saved!" to appear. Riven is now configured for AllDebrid (you can confirm this on the Riven backend logs)

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/0007bb76-f9d4-4fe9-ad0f-463dabf62ec0/ascreenshot.jpeg?tl_px=1012,664&br_px=2732,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=708,540)