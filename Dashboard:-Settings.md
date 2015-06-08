![c](https://cloud.githubusercontent.com/assets/585534/8024482/4c6f01b0-0d03-11e5-942c-64fe9e2a3686.png)

### Below more details for the non-self-explanatory items

#### Make use of context menu where appropriate

If checked, this gives permission for uBlock to add items in the context menu which are meant to improve convenience. Currently, only one item is added to the context menu, _"Block element"_, which purpose is to launch the element picker in order to filter out a specific element on a page.

#### Color-blind friendly

Currently mostly useful for users who checked _"I am an advanced user"_ (see below).

#### I am an advanced user

If you check this, this will enable [uBlock's dynamic filtering](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering), and the dynamic filtering pane will become available from uBlock's popup UI.

Unchecking this disable dynamic filtering, and the dynamic filtering pane in the popup UI will no longer be available.

_Advanced user_ mode also enables the ability to filter [behind-the-scene network requests](https://github.com/gorhill/uBlock/wiki/Behind-the-scene-network-requests).

#### Disable pre-fetching

Checking this will disable prefetching in your browser. When prefetching is enable, the browser _can_ still establish connections to remote servers even if the resource from these remote servers are meant to be blocked by uBlock.

This prevent the browser from bypassing uBlock's filtering engine before establishing connections to remote servers.

Mozilla's [_"Link prefetching FAQ"_](https://developer.mozilla.org/docs/Web/HTTP/Link_prefetching_FAQ):

> **Privacy implications** Along with the referral and URL-following implications already mentioned above, prefetching will generally cause the cookies of the prefetched site to be accessed.

Google's [_"Make webpages load faster"_](https://support.google.com/chrome/answer/1385029):

> If you turn this setting on in Chrome, websites (and any of their embedded resources) that are prerendered or prefetched may set and read their own cookies as if you had visited them before -- even if you don’t visit the prerendered or prefetched pages after all.

#### Disable hyperlink auditing/beacon

Checking this will prevent hyperlink auditing/beacon. _Hyperlink auditing_ and _Send beacon_ are best summarized as "phone home" features (or even "phone anywhere"). The details are well explained [here](http://www.wilderssecurity.com/threads/hyperlink-auditing-aka-a-ping-and-beacon-aka-navigator-sendbeacon.364904/).

**Important note:** _"Send beacon"_ can not be disabled in Chromium. Advanced users can filter behind-the-scene network requests, where the beacon-related network requests show up.

#### Backup/restore section

The bottom-most section is for you to easily backup/restore/reset all settings in uBlock.

It is suggested you backup all your settings regularly.