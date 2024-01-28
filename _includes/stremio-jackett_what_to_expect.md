## What to expect

When you search in stremio, Stremio-Jackett will get to work - because the results are not cached, it may take 10-20s before they're presented in Stremio, but a successful search will look like this:

![](/images/stremio-jacket-example-search.png)

!!! question "Why is searching so slow?"
    It depends wildly on your indexers. If you've added 20 indexers, Jacket will have to query **each** of them before presenting a result back to Stremio-Jackett. This may take longer than Stremio's addon timeout period, and so you may see no results.

    Further, if you're using indexers which require [Flaresolverr][flaresolverr], then this solving process will also add further delay.

    For optimal results, limit Jackett to as few, high-quality indexers as possible, ideally without Flaresolverr.

    You can check the the logs of all the pods involved by using [Kubernetes Dashboard][kubernetes-dashboard]
