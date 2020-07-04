AdNauseam's required permissions are based on those of [uBlock Origin](https://github.com/gorhill/uBlock/wiki/Permissions). We add one additional permission ("Monitor extension usage and manage themes") which we use to check for other addons that may conflict with AdNauseam, and then to issue a warning. These are AdNauseam's required permissions:
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

<br/>

#### "Monitor extension usage and manage themes"

AdNauseam adds this additional permission to check which addons you have installed and enabled in your browser, so that we can show you a warning message if you have installed other extensions that might cause conflicts with AdNauseam. Here is a link to the [relevant code](https://github.com/dhowe/AdNauseam/blob/master/platform/chromium/vapi-background.js#L1690)


#### See uBlock's documentation on how specific permissions are used below:

* ["Access your data on all web sites"](https://github.com/gorhill/uBlock/wiki/Permissions#access-your-data-on-all-web-sites) 
* ["Access your tabs and browsing activity"](https://github.com/gorhill/uBlock/wiki/Permissions#access-your-tabs-and-browsing-activity) 
* ["Access IP address and hostname information"](https://github.com/gorhill/uBlock/wiki/Permissions#access-ip-address-and-hostname-information) 
* ["Store unlimited amount of client-side data"](https://github.com/gorhill/uBlock/wiki/Permissions#access-ip-address-and-hostname-information) 
* ["Change your privacy-related settings"](https://github.com/gorhill/uBlock/wiki/Permissions#change-your-privacy-related-settings) 

