[Back to Wiki home](https://github.com/gorhill/uBlock/wiki)

***

This is µBlock's popup UI when you click on µBlock's icon in the toolbar:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png)

***

#### The title bar

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1a.png)

Click the title bar of the popup to go to µBlock's dashboard.

***

#### The large green button

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1b.png)

Click the large green button to turn off µBlock **for the current site** (a.k.a. _whitelist_ the current site). This will be remembered the next time you visit the site.

Alternatively, you can also `<Ctrl>`-click to turn off µBlock only for the current page.

For more advanced whitelisting control, see ["How to whitelist a web site"](https://github.com/gorhill/uBlock/wiki/How-to-whitelist-a-web-site).

***

#### The number of requests blocked

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1c.png)

This shows the number of network requests which were blocked on the current page. Also, less useful, but people like this kind of thing, the number of network requests blocked since install.

Click the eye-dropper icon to enter [element picker mode](https://github.com/gorhill/uBlock/wiki/Element-picker), which allows to create a filter by interactively picking an element on a page, in order to have the element permanently removed from the page.

Click the eye icon to bring up the [network request logger](Quick-guide:-network-request-logger), which will open in a separate tab. This allows to inspect real-time network traffic on a given page.

***

#### The number of domains connected

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png)

The number of distinct domains with which a network connection was established, out of all connections (established + blocked). The domains are derived using the official [Public Suffix List](https://publicsuffix.org/).

In general, it must be assumed that each distinct domain is managed by a distinct administrative authority. In practice, it is not uncommon to have a couple distinct domains which are under the same administrative authority (for example: `google.com`, `ajax.googleapis.com` and `gstatic.com`, or `wikipedia.org` and `wikimedia.org`).

That said, this statistic has to be seen this way: the more distinct domains your browser connects to, the larger the privacy exposure.

In a best-case scenario, the number of distinct domains to which a web page connects should be **only one**, i.e. that of the remote server from which the web page was fetched.

**The higher the number, the higher your are exposing yourself privacy-wise.**

There is a good correlation between _domains connected_ count and: undue page bloat, high privacy exposure, likelihood of being the target of data mining.

Example, a web page on <http://www.ibtimes.com/> (which could be read all fine in all cases by the way):

 µBlock's mode | turned off | default settings | [default-deny](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)
--- | --- | --- | ---
domains connected | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1e.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1f.png)
privacy exposure | very high | medium | very low
bloat | ridiculously high | medium | very low

And I had click-to-play enabled in all cases, i.e. it could have been worst (except for default-deny)...