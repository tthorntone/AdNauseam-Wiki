µBlock comes with a network request logger, which gives the ability to inspect network requests, whether they were blocked or allowed, andwhich filter, if any, matched a network request.

To access the network request logger, click on the _eye_ icon of µBlock's popup UI:

![Figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1c.png)

The request logger will open in a new tab:

![Figure 2](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-01.png)

***

### Components

![Figure 2](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-02.png)

The drop-down selector is to choose for which tab network requests should be logged. Each network request logger can log only one tab at a time, in order to identify clearly all the network requests which originate from a specific web page.

You may have multiple network request loggers open at the same time though -- there is no limit.

The big refresh button aside the tab selector si to refresh the content of the selector. When tabs are added or closed, you need to refresh explicitly the selector so that its content reflects the current tabs.

***

![Figure 3](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-03.png)

This is to force a refresh of the tab which is currently being observed.

***

![Figure 4](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-04.png)

This is to remove all the logged entries.

***

![Figure 6](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-06.png)

This is to filter the entries to display. The entries which are remove from view are not removed from the logger, they are just hidden according to the filter expression.

Some details about how to filter logged entries:

If the first character is:
- `-`: display only blocked requests
- `+`: display only allowed-through-exception-filter requests
- `!`: negate the rest of the expression

A matching filtering expression is one which matches from left-to-right the text in an entry. Examples of filtering expression:

- `- script`: show all blocked requests of type `script`
- `+ xhr`: show all force-allowed requests of type `xhr` (XHMHttpRequest)
- `!-`: show all non-blocked requests
- `script google`: show all requests containing the strings "script" then "google"

The filter expression can be a plain regular expression:

- `/image|css/`: show all requests which type is `image` or `css`
- `!/image|css/`: show all requests which type is not `image` neither `css`

***

![Figure 5](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-05.png)

This is the maximum number of entries allowed in the request logger. When the maxium is reached, the oldest entries at the bottom will be removed to make place to newest entries at the top.