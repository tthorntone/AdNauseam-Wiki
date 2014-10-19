#### "Access your data on all web sites"

- To be able to inspect all net requests so that they can be cancelled if needed.
- Only on `http`- and `https`-based URL addresses.

See code:
- <https://github.com/gorhill/uBlock/search?q=%22chrome.webRequest%22&type=Code>

#### "Access your tabs and browsing activity"

This is necessary to be able to:

- Create new tabs (when you click on a filter list, to see its content)
- To detect when a tab is added or removed:
    - To update badge
    - To flush from memory internal data structures
- To find out which tab is currently active (to fill popup menu with associated stats/settings)
- To be able to inject the element picker script
- To implement the popup-blocker

See code:
- <https://github.com/gorhill/uBlock/search?q=%22chrome.tabs%22&type=Code>
- <https://github.com/gorhill/uBlock/search?q=%22chrome.webNavigation%22&type=Code>

#### "Manage your downloads"

- To be able to save your filters locally (in the _"Your filters"_ tab in the dashboard)
- To be able to save your whitelist sites locally (in the _"Whitelist"_ tab in the dashboard)
- To be able to back up all your data (from the _"About"_ tab, just like in HTTP Switchboard)

See code:
- <https://github.com/gorhill/uBlock/search?q=%22chrome.downloads%22&type=Code>