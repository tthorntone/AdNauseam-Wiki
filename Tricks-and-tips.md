#### Easy way to find out what other blockers do not block what they should block

Since version 0.2.0.0, when the popup blocker code was added, µBlock decides whether a request should be cancelled during `chrome.webRequest.onBeforeSendHeaders`. Before 0.2.0.0, the cancellation of net requests was done earlier in the pipeline, during `chrome.webRequest.onBeforeRequest`. The change was required because the popup blocker code needs the HTTP referrer header to do its job.

Net requests can be cancelled as effectively using `chrome.webRequest.onBeforeSendHeaders`, so it's not an issue. There is a side effect though, which can actually be quite useful: you can find out what other blockers do not block.

Other blockers typically cancel requests during `chrome.webRequest.onBeforeRequest`, which means by the time µBlock's handler kicks in, many, if not all, net requests have been blocked by the other blocker(s).

So in such case, if you notice µBlock actually still ends up blocks something, it's actually everything the other blocker(s) did **not** block. Thus, µBlock can also be used to find out what other blockers are missing.

Here is an example. ABP with _EasyList_ and _EasyPrivacy_. µBlock blocks one request, thus something not blocked by ABP:

![Did not block](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/tips-n-tricks-001.png)

I really thought _EasyPrivacy_ was blocking Google Analytics.