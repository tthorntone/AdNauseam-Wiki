#### Easy way to find out what other blockers do not block what they should block

Since version 0.2.0.0, when the popup blocker code was added, µBlock decides whether a request should be cancelled during `chrome.webRequest.onBeforeSendHeaders`. Before 0.2.0.0, the evaluation of filters was done earlier in the pipeline, during `chrome.webRequest.onBeforeRequest`. This was required because the popup blocker code needs the HTTP referrer header to do its job.

Net requests can be cancelled as effectively using `chrome.webRequest.onBeforeSendHeaders`, so it's not an issue. There is a side effect though, which can actually be quite useful: you can find out what another blocker does not block. Other blockers typically cancel requests during `chrome.webRequest.onBeforeRequest`, which means by the time µBlock's handler at `chrome.webRequest.onBeforeSendHeaders` time kicks in, many, if not all, net requests have been blocked by the other blocker(s).

So in such case, if you notice µBlock actually blocks something, it's actually everything the other blocker(s) did **not** block. Thus, µBlock can also be used to find out what other blockers are missing.

