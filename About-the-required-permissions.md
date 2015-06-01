### "Access your data on all web sites" (since v0.1.0.0)

- To be able to inspect all net requests so that they can be cancelled if needed.
    - Only on http- and https-based URL addresses.

See code:

- [chrome.webRequest](https://github.com/gorhill/uBlock/search?q=%22chrome.webRequest%22&type=Code)

### "Access your tabs and browsing activity" (since v0.1.0.0)

This is necessary to be able to:

- Create new tabs (when you click on a filter list, to see its content)
- To detect when a tab is added or removed:
- To update badge
- To flush from memory internal data structures
- To find out which tab is currently active (to fill popup menu with associated stats/settings)
- To be able to inject the element picker script
- To implement the popup-blocker

See code:

- [chrome.tabs](https://github.com/gorhill/uBlock/search?q=%22chrome.tabs%22&type=Code)
- [chrome.webNavigation](https://github.com/gorhill/uBlock/search?q=%22chrome.webNavigation%22&type=Code)

### "Change your privacy-related settings" (since v0.9.8.2)

This is necessary to be able to:

- Disable _"Prefetch resources to load pages more quickly"_
    - This will ensure no TCP connection is opened **at all** for blocked requests.
    - For pages with lots for blocked requests, this will actually _remove_ overhead from page load (if you did not have the setting already disabled)

![c](https://cloud.githubusercontent.com/assets/585534/7914528/924b9314-0845-11e5-8012-f67e4b1814cd.png)

See code:

- [chrome.privacy.network](https://github.com/gorhill/uBlock/commit/e65c2939757f09db646d277b82da8690aaf3adbc)