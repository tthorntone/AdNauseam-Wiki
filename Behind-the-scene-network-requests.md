**The filtering of behind-the-scene network request is available to advanced users.**

### What are behind-the-scene network requests

_Behind-the-scene_ network requests are those network requests which µBlock can not associate with a specific tab opened in your browser: these requests come from _somewhere_, but µBlock is missing information to report exactly from here.

All network requests without a specific origin are classified as _behind-the-scene_. Typically, all blockers will ignore and automatically whitelist behind-the-scene network requests.

For the Chromium browser, examples of behind-the-scene network requests:

- from the browser to update extensions
- from the browser because of specific functionality, like the setting _"Use a prediction service to help complete searches and URLs typed in the address bar"_
- as a result of web pages using [`navigator.sendBeacon()`](https://developer.mozilla.org/en-US/docs/Web/API/navigator.sendBeacon), [hyperlink auditing](http://www.wilderssecurity.com/threads/hyperlink-auditing-aka-a-ping-and-beacon-aka-navigator-sendbeacon.364904/), etc.
- made by installed extensions for good or bad reasons (µBlock makes such requests, to fetch the filter lists when they need to be updated)
- etc.

### How to inspect behind-the-scene network requests

Starting with version µBlock 0.8.6.0, you can inspect behind-the-scene network requests using the network request logger. Just select the _"Behind the scene"_ entry in the drop down list.

![c](https://cloud.githubusercontent.com/assets/585534/5888630/0691e7ee-a3d5-11e4-8510-ed0955f39deb.png)

Typically, you will leave the network request logger opened for a long duration in order to catch all and any behind-the-scene network requests.

### How to filter behind-the-scene network requests

**Important:** The blocking of behind-the-scene network requests can cripple important functionality of your browser or installed extensions. **If you decide to filter some behind-the-scene network requests, you are entirely responsible for the consequences.**