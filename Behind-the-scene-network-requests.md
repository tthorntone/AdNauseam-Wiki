**The filtering of behind-the-scene network request is available to advanced users.**

### What are behind-the-scene network requests

_Behind-the-scene_ network requests are those network requests which µBlock can not associate with a specific tab opened in your browser: these requests come from _somewhere_, but µBlock is missing information to report exactly from here.

All network requests without a specific origin are classified as _behind-the-scene_. Typically, all blockers will ignore and automatically whitelist behind-the-scene network requests.

For the Chromium browser, examples of behind-the-scene network requests:

- from the browser to update extensions
- from the browser because of specific functionality, like the setting _"Use a prediction service to help complete searches and URLs typed in the address bar"_
- fired by through [`navigator.sendBeacon()`](https://developer.mozilla.org/en-US/docs/Web/API/navigator.sendBeacon), [hyperlink auditing](http://www.wilderssecurity.com/threads/hyperlink-auditing-aka-a-ping-and-beacon-aka-navigator-sendbeacon.364904/), etc.
- made by installed extensions for good or bad reasons (µBlock makes such requests, to fetch the filter lists when they need to be updated)
- etc.

