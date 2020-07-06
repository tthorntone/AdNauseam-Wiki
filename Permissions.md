AdNauseam's required permissions are based on those of [uBlock Origin](https://github.com/gorhill/uBlock/wiki/Permissions). We add one additional permission ([monitor extension usage and manage themes](https://support.mozilla.org/en-US/kb/permission-request-messages-firefox-extensions)) which we use to check for other addons that might conflict with AdNauseam, and then to issue a warning for the user. Here is a link to the [relevant code](https://github.com/dhowe/AdNauseam/blob/master/platform/chromium/vapi-background.js#L1690).

These are the required permissions as specified in AdNauseam's manifest:

```
"permissions": [
    "privacy",
    "storage",
    "tabs",
    "unlimitedStorage",
    "webNavigation",
    "webRequest",
    "webRequestBlocking",
    "<all_urls>",
    "management",
    "contextMenus (chromium-only)",
    "menus" (firefox-only),
    "dns" (firefox-only),
]
```

<br>

**See uBlock's documentation on how specific permissions are used below:**

* ["Access your data on all web sites"](https://github.com/gorhill/uBlock/wiki/Permissions#access-your-data-on-all-web-sites) 
* ["Access your tabs and browsing activity"](https://github.com/gorhill/uBlock/wiki/Permissions#access-your-tabs-and-browsing-activity) 
* ["Access IP address and hostname information"](https://github.com/gorhill/uBlock/wiki/Permissions#access-ip-address-and-hostname-information) 
* ["Store unlimited amount of client-side data"](https://github.com/gorhill/uBlock/wiki/Permissions#access-ip-address-and-hostname-information) 
* ["Change your privacy-related settings"](https://github.com/gorhill/uBlock/wiki/Permissions#change-your-privacy-related-settings) 

