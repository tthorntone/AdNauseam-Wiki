AdNauseam's required permissions are based on those of uBlock. These are AdNauseam's required permissions:
```
"permissions": [
    "contextMenus",
    "dns",
    "privacy",
    "storage",
    "tabs",
    "unlimitedStorage",
    "webNavigation",
    "webRequest",
    "webRequestBlocking",
    "management",
    "<all_urls>",
],
```
#### "Monitor extension usage and manage themes"

AdNauseam adds this additional permission to check which extensions you have installed and enabled in your browser, so that we can show you a warning message if you have installed other extensions that might cause conflicts with AdNauseam.

See code:
[vAPI.getAddonInfo](https://github.com/dhowe/AdNauseam/blob/master/platform/chromium/vapi-background.js#L1690)


***

#### ["Access your data on all web sites"](https://github.com/gorhill/uBlock/wiki/Permissions#access-your-data-on-all-web-sites) 
#### ["Access your tabs and browsing activity"](https://github.com/gorhill/uBlock/wiki/Permissions#access-your-tabs-and-browsing-activity) 
#### ["Access IP address and hostname information"](https://github.com/gorhill/uBlock/wiki/Permissions#access-ip-address-and-hostname-information) 
#### ["Store unlimited amount of client-side data"](https://github.com/gorhill/uBlock/wiki/Permissions#access-ip-address-and-hostname-information) 
#### ["Change your privacy-related settings"](https://github.com/gorhill/uBlock/wiki/Permissions#change-your-privacy-related-settings) 

