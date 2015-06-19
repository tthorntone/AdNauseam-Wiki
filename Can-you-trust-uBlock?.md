After I added the `privacy` permission in order to make uBlock Origin  reliable when it comes to blocking network requests, a lot of people questioned uBlock Origin 's trustworthiness.

First, uBlock Origin is completely developed in full public view. All the sources and the changes to the sources are fully accessible on GitHub.


Second, uBlock Origin does not have a dedicated server, it can't "phone home" with your browsing data, there is only GitHub, and GitHub is completely unrelated to uBlock Origin.

I think it's time I give examples of how requiring _less_ permissions is **not** a sign a higher trustworthiness.

#### Web Protector - Reliable Phishing Protection

Chrome store: [Web Protector - Reliable Phishing Protection](https://chrome.google.com/webstore/detail/web-protector-reliable-ph/kfecnpmgnlnbmipaogfhoacoioifjgko).

This extension requires the same permission as uBlock, minus the `privacy` one. Some might be inclined that it can thus be more trusted than uBlock, which requires the `privacy` permission.

However, Web Protector has a home server, and it does "phone home" as opposed to uBlock. For **every** web page you visit, you can see Web Protector sending behind-the-scene network requests to `webovernet.com`:

![c](https://cloud.githubusercontent.com/assets/585534/8253895/fe92dd8c-1661-11e5-9134-5c2b9159a57c.png)
