Back to [Wiki home](https://github.com/gorhill/uBlock/wiki)

***

The per-site switches allows you to control uBlock's behavior on a per-site basis.

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1g.png)

- [No popups](#no-popups)
- [No strict blocking](#no-strict-blocking)
- [No cosmetic filtering](#no-cosmetic-filtering)
- [No remote fonts](#no-remote-fonts)

***

##### No popups

By default popups are allowed unless there is a filter to block them. When this setting is enabled, **all** popups will be unconditionally blocked for the current site, regardless of filters:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1i.png)<br><sup>No popups for the current site: [Try it](http://jessehakanen.net/adblockpluspopupaddon/test.html)</sup>

Blocking popups depends on whether the proper filters are present in the selected filter lists, so this feature is most useful when a site creates popups for which there are no filters to take care of them in 3rd-party filter lists.

**Caveat for Chromium-based browsers:** Due to Chromium API limitations, it's not possible for uBlock to determine for sure whether a new tab being opened is that of a popup, or is the result of a legitimate click on a link by the user. So if the no-popups switch is in use, you _may_ not be able to open a link in a new tab through the context menu.

***

##### No strict blocking

The second icon is to turn off strict blocking for the current site. By default, strict blocking is enabled in uBlock (this is the opposite of Adblock Plus).

Adblock Plus only blocks secondary resources (see [web pages _themselves_ are **never** filtered](https://adblockplus.org/forum/viewtopic.php?t=18774#p85439)).

So if you were to create a filter such as `||example.com^`, and then navigate to <https://example.com>, Adblock Plus would not prevent you from connecting and loading the web page itself served at `https://example.com`, though all secondary resources pulled by that web page would be subject to filtering.

uBlock respected that semantic until version 0.9.3.0. With version 0.9.3.0, uBlock will subject web pages themselves to filtering. This means that using the same test case above, **uBlock will block the web page** served by a server found in one of the malware list (unlike Adblock Plus):

![Page was fully blocked](https://cloud.githubusercontent.com/assets/585534/8160013/14466ca0-133a-11e5-8d3c-28169288f35a.png)

Why the change? Because [issue #1013](https://github.com/chrisaljoudi/uBlock/issues/1013) brought forth why it is desirable sometimes to completely block a web site, as opposed to what the ABP-filtering semantic dictates.

In the end, the chosen solution is to now have web page themselves subject to filtering, just like all secondary resources.

In the figure above, the user will be given the choice to go back by closing the window or proceed to the web page by disabling strict blocking by selecting either:

- Temporarily - The site will be temporarily allowed for a limited time (currently set at 60 seconds).
- Permanently - The site will be permanently allowed.

If the user disagrees that a web page proper should be blocked (because of a false positive for example), then they can turn off _strict blocking_ for that site:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1h.png)<br><sup>No strict blocking for the current site.</sup>

This will prevent the web page proper for the site from being blocked by uBlock in the future: the filtering of the site will be done exactly as per ABP-filtering semantic, and just like with uBlock pre-0.9.3.0.

There are many benefits to strict blocking. For example, there is no good reason one should want to connect _at all_ to any of the sites present in any one of the malware domain lists. Strict blocking will prevent this from happening.

**Important note:** Keep in mind that when the above warning occurs, it doesn't necessarily mean the site is harmful, it just means that there is a matching filter in the selected filter lists. You decide whether the site is safe, and whether disabling strict blocking permanently for the site is appropriate.

Strict blocking is commonly disabled for sites in [Badware risks](https://github.com/gorhill/uBlock/wiki/Badware-risks).

**Tip:** If you wish, you may entirely disable strict blocking everywhere by adding the rule `no-strict-blocking: * true` to the _My rules_ pane in the dashboard (don't forget to click _Commit_ to make the rule stick).

***

##### No cosmetic filtering

You can easily toggle on/off cosmetic filtering for a given site:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1j.png)<br><sup>No cosmetic filtering for the current site.</sup>

When present, the badge number indicates the number of elements hidden on the page by uBlock as a result of cosmetic filtering. If you disable cosmetic filtering while there are hidden elements on the page, these elements will become visible/hidden as you toggle off/on cosmetic filtering.

Cosmetic filtering is always enabled by default.

**Tip:** It is often suggested adding a custom static filter such as `@@||example.com^$elemhide` to prevent "adblock" detection by specific sites ([example](https://adblockplus.org/forum/viewtopic.php?f=2&t=30763#p124225)). You can accomplish the same goal more simply by just toggling off cosmetic filtering using this switch while on the problematic site.

**Tip:** This switch can help uBO to further lower its CPU-cycle footprint, which might be beneficial on devices with limited CPU-cycle resources -- and thus helping extend battery life and speed up page load times. The idea is to disable cosmetic filtering everywhere by default, and to enable it only for those sites which really benefit from it. To disable cosmetic filtering everywhere by default, enter the following rules in the _"My rules"_ pane in the dashboard:

    no-cosmetic-filtering: * true

Click _Save_, then _Commit_ to make the rule permanent. From then on, cosmetic filtering will be turned off everywhere by default, and to turn it on for a specific site where it is really needed, just enable it using the switch in the uBO's panel.

***

##### No remote fonts

You can prevent web fonts from being downloaded for the current site:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1k.png)<br><sup>No remote fonts for the current site.</sup>

Because of security and privacy concerns, many prefer to block all web fonts by default. You can do this by adding the following rule directly in the _"My rules"_ pane in the dashboard:

    no-remote-fonts: * true

This will block all web fonts everywhere by default, and in this case you can toggle off the switch to allow web fonts on a per-site basis.

**Caveat for Chromium-based browsers:** Chromium's webRequest API [does not specifically report requests of type `font`](https://developer.chrome.com/extensions/webRequest#type-ResourceType), fonts are reported as type `other`. Whether a request is for a font resource is inferred by uBlock using the "extension" of the path part of a URL. However a URL can be anything really, regardless of request type, so for Chromium-based browsers, uBlock **may** have to block a font **after** the request is made, when the response headers are received from the remote server -- as the response headers allow to identify for sure the type of a resource.