uBlock comes with a network request logger, which gives the ability to inspect network requests, whether they were blocked or allowed, and which filter, if any, matched a network request.

To access the network request logger, click on the _list_ icon of µBlock's popup UI:

![Figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1c-1.png)

The request logger will open in a new tab:

![Figure 2](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-01.png)

Take note that the network request logger in uBlock is a forward-looking logger: this means only future requests can be logged. In the spirit of efficiency, uBlock will log network requests for a tab if and only if there is a logger opened for that tab.

***

### Components

![Figure 2](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-02.png)

The drop-down selector is to choose for which tab network requests should be logged. Each network request logger can log only one tab at a time, in order to identify clearly all the network requests which originate from a specific web page.

You may have multiple network request loggers open at the same time though -- there is no limit.

The big refresh button aside the tab selector is to refresh the content of the selector. When tabs are added or closed, you need to refresh explicitly the selector so that its content reflects the current tabs.

Note in the figure above the entry named "Behind the scene": selecting this entry allows you to see behind-the-scene network requests, i.e. those network requests which do not originate from a specific tab. [More about this here](https://github.com/gorhill/uBlock/wiki/Behind-the-scene-network-requests).

***

![Figure 3](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-03.png)

This is to force a refresh of the tab which is currently being observed.

***

![Figure 4](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-04.png)

This is to remove all the logged entries.

***

![Figure 6](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-06.png)

You can filter entries in the logger using filter expressions. Log entries which do not match _all_ filter expressions will be hidden from view. Syntax for a filter expression:

- Enter `foo` to only show entries which have a string `foo`.
- Enter `|foo` to only show entries which have a field starting with `foo`.
    - Tip: use `|--` to show only entries which were blocked (`--` may work for the most part, but there could be false positives).
- Enter `foo|` to only show entries which have a field ending with `foo`.
- Enter `|foo|` to only show entries which have exactly a field with `foo`.
- Prefix any expression with `!` to reverse the meaning of the expression.
    - `!foo` means display only entries which do not have the string `foo` in it.
    - `!|--` means display only entries which were **not** blocked.
- When more than one filter expression appear, a logical _and_ between the expressions is implied.
- You can _or_ multiple expressions together:
    - `css || image` means display entries which match either `css` or `image`.
    - `!css || image` means display entries which do not match either `css` or `images` (equivalent to `!css !image` really).
    - Warning: With _or_'ed expressions, the _not_ (`!`) operator can only apply to the resulting _or_'ed expression.
- A special keyword can be used to filter behind-the-scene requests: `bts`, or `|bts` for a stricter filtering.

Examples:

- `!|-- facebook`: show only non-blocked entries with the string `facebook` in it.
- `|xhr google`: show only entries of type `XMLHttpRequest` with the work `google` in it.
- `!|image !|css`: show only entries which are not of type `image`, neither `css`.

***

![Figure 5](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/rlogger-05.png)

This is the maximum number of entries allowed in the request logger. When the maximum is reached, the oldest entries at the bottom will be removed to make place to newest entries at the top.

This is useful to be sure the request logger does not unduly consume a huge amount of memory if left open for long period of time. Usually, the most recent entries are the ones of interest. When this value is not set, there is a built-in limit of 25,000 entries.

One could leave the logger opened for long period of time with the _"Behind the scene"_ selected to find out what the browser and other installed extensions are doing behind the scene.