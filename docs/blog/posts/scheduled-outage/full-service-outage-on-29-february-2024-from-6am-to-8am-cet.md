---
date: 2024-02-26
categories:
  - infrastructure
title: Full service outage from on 29 February 2024 between 6:00 AM and 8:00 AM (CET)
description: We're going to "hibernate" to avoid a Hetzner-planned maintenance to our core storage connectivity
---
# Full service outage on 29 February 2024 between 6:00 AM and 8:00 AM (CET)

!!! danger "Full service outage on 29 February 2024 between 6:00 AM and 8:00 AM (CET)"
    All ElfHosted services will be affected. Your pods will be shutdown at 6AM, and restored at 8AM
    
We've received [notice from Hetzner](https://status.hetzner.com/incident/7f4f801c-4279-40e7-a1e1-2f8c08396e9f) that they'll be undertaking maintenance on the switch which connects our 10Gbps "goblin" nodes, providing all of the shared storage for our `/config` volumes. The maintenance is [scheduled for 29 February 2024 between 6:30 AM and 7:30 AM](https://status.hetzner.com/incident/7f4f801c-4279-40e7-a1e1-2f8c08396e9f/calendar.ics) (CET)

Given the criticality of these nodes, and the amount of #chaos which would ensue if they all went away simultaneously, we'll be taking all customer workloads down 30 minutes prior to the scheduled maintenance, and bringing them back again 30 minutes afterwards.

This means that for ElfHosted customers, the actual service outage will be a total of **2 hours**, from 6:00 AM to 8:00 AM (CET).

{% raw %}
<script>(function(d, s, id) { var js, pjs = d.getElementsByTagName(s)[0]; if (d.getElementById(id)) return; js = d.createElement(s); js.id = id; js.src = "//www.tickcounter.com/static/js/loader.js"; pjs.parentNode.insertBefore(js, pjs); }(document, "script", "tickcounter-sdk"));</script><a data-type="countdown" data-id="4943019" class="tickcounter" style="display:block; left:0; width:100%; height:0; position:relative; padding-bottom:25%; margin:0 auto;" title="Time to 2-hour full service shutdown" href="//www.tickcounter.com/">Time to 2-hour full service shutdown</a>
{% endraw %}

In summary..

!!! danger "Full service outage on 29 February 2024 between 6:00 AM and 8:00 AM (CET)"
    All ElfHosted services will be affected. Your pods will be shutdown at 6AM, and restored at 8AM