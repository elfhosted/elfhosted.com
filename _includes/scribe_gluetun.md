### Adding a VPN to your ElfHosted stack with gluetun

Gluetun is a flexible container which supports many VPN providers. By attaching a gluetun config to VPN-compatible apps in your ElfHosted stack, you can have these apps take advantage of your existing VPN provider (some apps, like AllDebrid, require this functionality in order to work)

1\. Start from your ElfHosted dashboard


2\. In a new tab, navigate to <https://docs.elfhosted.com/app/gluetun/>


3\. The documentation illustrates how a VPN works, and provides a sample ConfigMap to get you started. Copy the YAML for the ConfigMap to your clipboard

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/62ea9d31-1770-4928-bc9b-444b37c1212e/ascreenshot.jpeg?tl_px=0,136&br_px=1719,1098&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=978,222)


4\. Back on your ElfHosted dashboard, click "Kubernetes Dashboard"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/c9344e6f-a5d4-4523-bee9-1deb8008c108/ascreenshot.jpeg?tl_px=0,664&br_px=1719,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=223,304)


5\. If you're prompted for an auth token, click "Skip" (you already have the necessary privileges)

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/a4c4afe1-e240-4528-90cc-91f6567216a7/ascreenshot.jpeg?tl_px=0,631&br_px=1719,1592&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=168,276)


6\. Click the plus sign in the top right to add a resource

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/1a9c17b1-0bd9-496f-834b-6e9339da8b1f/ascreenshot.jpeg?tl_px=402,0&br_px=2122,961&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=895,4)


7\. In the blank text entry window, paste the ConfigMap YAML you copied from <https://docs.elfhosted.com/app/gluetun/>

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/b71983be-3e35-4960-826a-2496675e657c/ascreenshot.jpeg?tl_px=72,317&br_px=1791,1278&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=524,276)


8\. Review the instructions for your VPN provider at <https://github.com/qdm12/gluetun-wiki/tree/main/setup/providers>, and alter the necessary ENV vars, then click "Upload"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/01b5342f-9c20-4340-94f0-bb88f2d198bc/ascreenshot.jpeg?tl_px=0,664&br_px=1719,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=380,444)


Alert: Don't use DNS names for your VPN_ENDPOINT_IP value. Gluetun only works with IP addresses, to avoid DNS leakage.


9\. To confirm that the VPN has started correctly (it often won't, on your first attempt), navigate to [[Pods]], find the pod you're connecting to gluetun ("rclonealldebrid" in the example below), scroll to the right, and click on the 3 dots for more options

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/192279e6-8b55-4e63-bfc4-b5233647787e/ascreenshot.jpeg?tl_px=1177,684&br_px=2725,1549&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=1007,205)


10\. Click "[[Logs]]" to see the pod's logs

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/ec611bbc-f437-4e2e-a391-8d7073a04a0c/ascreenshot.jpeg?tl_px=1184,681&br_px=2732,1546&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=936,277)


11\. Click the name of the container in "Logs from" to select which container logs to view

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/a3d3aeb3-e703-4212-9624-dbafacbe6d09/ascreenshot.jpeg?tl_px=43,0&br_px=1590,865&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=524,215)


12\. Pick the "[[gluetun]]" container

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/cd4aa210-3324-4f0e-9585-cc6013baf463/ascreenshot.jpeg?tl_px=0,31&br_px=1547,896&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=510,277)


13\. The logs will either indicate that the VPN is healthy, or they will show logs to help you to diagnose the fault

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/f36f8584-344f-4baf-90d1-be904a5e48d4/ascreenshot.jpeg?tl_px=246,760&br_px=1793,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=524,483)


14\. If you need to change the ENV vars, navigate to "Config and Storage" -&gt; Config Maps, find the "gluetun-config" ConfigMap, and click the 3 dots for more options. 

From the list of options, choose "Edit"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/2aeeac03-2c92-4de9-b942-2565d0db2a04/ascreenshot.jpeg?tl_px=75,482&br_px=2121,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=960,478)


15\. Make any changes required to the ENV vars under the "data" section

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/46bc2555-45b2-4679-9711-62c6b32d0369/ascreenshot.jpeg?tl_px=0,181&br_px=1719,1142&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=490,277)


Tip: Always quote integer or boolean (true, false) values


16\. Click "Update" to apply your changes. The affected pod should restart.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-12-11/90b2d3f5-d809-49a8-a777-ed265dacde32/user_cropped_screenshot.jpeg?tl_px=0,664&br_px=1719,1626&force_format=jpeg&q=100&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/50762E_standard.png&wat_pad=179,424)


17\. Examine the pod logs again, iterate until your VPN is healthy!