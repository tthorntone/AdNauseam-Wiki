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

![c](https://cloud.githubusercontent.com/assets/585534/5888630/0691e7ee-a3d5-11e4-8510-ed0955f39deb.png)<br><sup>Various extensions installed just to show that that these too make behind-the-scene requests</sup>

Typically, you will leave the network request logger opened for a long duration in order to catch all and any behind-the-scene network requests.

### How to filter behind-the-scene network requests

**Important:** The blocking of behind-the-scene network requests can cripple important functionality of your browser or installed extensions. **If you decide to block some behind-the-scene network requests, you are entirely responsible for the consequences.**

The ability to filter behind-the-scene network requests is only available when _"advanced user"_ is enabled.

Also, the _behind-the-scene_ virtual tab is whitelisted by default, i.e. no filtering will occur even after you enable _"advanced user"_ mode.

To access the filtering settings for the behind-the-scene network requests is simple a matter of opening popup UI in the network request logger while the _"Behind the scene"_ entry is selected:

![Behind-the-scene popup](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/behind-the-scene-popup.gif)<br><sup>The popup UI will be filled with the data of whatever tab is being currently inspected in the request logger.</sup>

**Important:** Filter behind-the-scene requests at your own risk. I will close without further comment any reported issue which are a direct consequence of blocking behind-the-scene network requests.

To turn off the filtering of behind-the-scene requests is just a matter of whitelisting the _"Behind the scene"_ scope, or to turn off _"advanced user"_ mode.