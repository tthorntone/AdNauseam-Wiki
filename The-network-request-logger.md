µBlock comes with a network request logger, which gives the ability to inspect network requests, whether they were blocked or allowed, andwhich filter, if any, matched a network request.

To access the network request logger, click on the _eye_ icon of µBlock's popup UI:

![Figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1c.png)

The request logger will open in a new tab:

![Figure 2](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-01.png)

### Components

#### Dropdown tab selector

The drop-down selector is to choose for which tab network requests should be logged. Each network request logger can log only one tab at a time, in order to identify clearly all the network requests which originate from a specific web page.

You may have multiple network request loggers open at the same time though -- there is no limit.

The big refresh button aside the tab selector si to refresh the content of the selector. When tabs are added or closed, you need to refresh explicitly the selector so that its content reflects the current tabs.