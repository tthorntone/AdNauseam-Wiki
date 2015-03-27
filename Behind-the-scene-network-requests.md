The filtering of behind-the-scene network request is available to [advanced users](https://github.com/gorhill/uBlock/wiki/Behind-the-scene-network-requests).

### What are behind-the-scene network requests

_Behind-the-scene_ network requests are those network requests which uBlock can not associate with a specific tab opened in your browser: these requests come from _somewhere_, but uBlock is missing information to report exactly from where.

All network requests without a specific origin are classified as _behind-the-scene_. Typically, all blockers will ignore and automatically whitelist behind-the-scene network requests.

For the Chromium browser, examples of behind-the-scene network requests:

- from the browser to update extensions
- from the browser because of specific functionality, like the setting _"Use a prediction service to help complete searches and URLs typed in the address bar"_
- as a result of web pages using [`navigator.sendBeacon()`](https://developer.mozilla.org/en-US/docs/Web/API/navigator.sendBeacon), [hyperlink auditing](http://www.wilderssecurity.com/threads/hyperlink-auditing-aka-a-ping-and-beacon-aka-navigator-sendbeacon.364904/), etc.
- made by installed extensions for good or not so good reasons (uBlock makes such requests, to fetch the filter lists when they need to be updated)
- etc.

### How to inspect behind-the-scene network requests

Starting with version uBlock 0.8.6.0, you can inspect behind-the-scene network requests using the network request logger. Just select the _"Behind the scene"_ entry in the drop down list.

![c](https://cloud.githubusercontent.com/assets/585534/5888630/0691e7ee-a3d5-11e4-8510-ed0955f39deb.png)<br><sup>Various extensions installed just to show that that these too make behind-the-scene requests</sup>

Typically, you will leave the network request logger opened for a long duration in order to catch all and any behind-the-scene network requests.

The ability to inspect behind-the-scene network requests is available to all users, i.e. you do not need to enable _"advanced user"_ mode.

### How to filter behind-the-scene network requests

**Important:** The blocking of behind-the-scene network requests can cripple important functionality of your browser or installed extensions. **If you decide to block some behind-the-scene network requests, you are entirely responsible for the consequences.**

The ability to filter behind-the-scene network requests is only available when _"advanced user"_ is enabled.

Also, the _behind-the-scene_ virtual tab is whitelisted by default, i.e. no filtering will occur even after you enable _"advanced user"_ mode.

To access the filtering settings for the behind-the-scene network requests is simple a matter of opening popup UI in the network request logger while the _"Behind the scene"_ entry is selected:

![Behind-the-scene popup](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/behind-the-scene-popup.gif)<br><sup>The popup UI will be filled with the settings/data of whatever tab is being currently inspected in the request logger.</sup>

The picture above shows what happen when you navigate through Github: Github makes use of `navigator.sendBeacon()` to send data to Google Analytics, which results in the firing of behind-the-scene requests in Chromium browser.

**Important:** Filter behind-the-scene requests at your own risk. I will close without further comment any reported issue which is a direct consequence of blocking behind-the-scene network requests.

Remember that if you block indiscriminately, you could cripple the ability of your browser to update parts of itself properly, ability to update extensions, ability of extensions to work properly, etc. This is why this is deemed an advanced user feature.
 
To turn off the filtering of behind-the-scene requests is just a matter of whitelisting the _"Behind the scene"_ scope, or to turn off _"advanced user"_ mode.

To whitelist the behind-the-scene scope: add `behind-the-scene` as a whitelist directive, in the _Whitelist_ tab of uBlock's dashboard.

If there are only very specific behind-the-scene network requests you would like to filter, a good approach to minimize potential problems is to use dynamic filtering: set a local rule for the `all` cell to _allow_ (green) (i.e. `behind-the-scene * * allow`). This will ensure nothing is blocked in the behind-the-scene scope, just as if uBlock is disabled for that scope. Then proceed to create _block_ rules for the specific hostnames for which you want to block all network requests.