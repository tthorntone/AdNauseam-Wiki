[Back to Wiki home](https://github.com/gorhill/uBlock/wiki)

***

AdNauseam comes with a logger (based on the uBlock Origin logger), which gives the ability to inspect what AdNauseam is doing with network requests and DOM elements, whether something is blocked or allowed, and which filter, if any, matched a network request or DOM element.

The logger is the tool of choice to see, understand, diagnose and fix the functioning of uBlock.

To access the logger, click on the _list_ icon of uBlock Origin's popup UI:

![Figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1c-1.png)

The request logger will open in a new tab (which was moved to its own window below):

![Figure 2](https://cloud.githubusercontent.com/assets/585534/8034785/0cb141bc-0db9-11e5-9365-1e45ccc50263.png)

Take note that the network request logger in uBlock is a forward-looking logger: this means only future requests can be logged.

In the spirit of efficiency, uBlock will log entries **IF AND ONLY IF** the logger is opened. Otherwise, if the logger is not opened, no CPU/memory resources are consumed by uBlock for logging purpose.

***

- [Page selector](#page-selector)
- [Reload](#reload)
- [Expand](#expand)
- [Void log entries](#void-log-entries)
- [Clear](#clear)
- [Filtering the logger output](#filtering-the-logger-output)
- [Maximum number of entries](#maximum-number-of-entries)
- [Accessing popup UI of a specific page](#accessing-popup-ui-of-a-specific-page)
- [Finding from which list(s) a static filter originates](#finding-from-which-lists-a-static-filter-originates)
- [Creating filters](#creating-filters)
    - [Dynamic URL filtering rules](#dynamic-url-filtering-rules)
    - [Static network filters](#static-network-filters)

***

### Components

***

#### Page selector

![Figure 3](https://cloud.githubusercontent.com/assets/585534/8034873/fc489536-0db9-11e5-86ab-fb013ed91181.png)

The drop-down selector is to display log entries which are related to a specific page. This will hide from view all log entries which are not related to the selected page. By selecting _All_ again, all log entries will be displayed again.

Note in the figure above the entry named _"Behind the scene"_: selecting this entry allows to show only behind-the-scene network requests. Behind-the-scene network requests are requests which do not originate from any specific tab, and are denoted by the _eye-slash_ icon in the second column. More about [behind-the-scene network requests](https://github.com/gorhill/uBlock/wiki/Behind-the-scene-network-requests) here.

***

#### Reload

![Figure 4](https://cloud.githubusercontent.com/assets/585534/8035141/f5e4cc80-0dbb-11e5-9bb4-03a33c647c2f.png)

The big reload button aside the page selector is to force a reload of the content of the selected page. This button is enabled only for when a specific page is selected.

***

#### Expand

![Figure 5](https://cloud.githubusercontent.com/assets/585534/8035192/663e6932-0dbc-11e5-9df6-dd3143495bf8.png)

By default log entries in the logger are collapsed so as to take no more than one line. Some log entries however might be truncated as a result. This button is to force all those entries with truncated extraneous information to be fully visible.

***

#### Void log entries

![Figure 6](https://cloud.githubusercontent.com/assets/585534/8035264/fc8f467c-0dbc-11e5-8832-a2baf889af23.png)

The logger is _unified_, i.e. it display all network requests from all tabs at once. If you close a tab for which there are entries in the logger, these entries will be marked as _void_, i.e. a bold `X` will appear in the second column of these entries, to indicate the tab for these entries does not exist anymore.

The `X` button in the toolbar allows you to remove those void entries from the logger.

***

#### Clear

![Figure 7](https://cloud.githubusercontent.com/assets/585534/8035480/1735ce04-0dbf-11e5-91f4-d20be43af4a9.png)

This is to clear the logger, to remove all entries from the selected context (Ars Technica tab in this example).

***

#### Filtering the logger output

![Figure 8](https://cloud.githubusercontent.com/assets/585534/8035538/66077c8a-0dbf-11e5-9a1a-f2c6204ebbf7.png)

You can visually filter entries in the logger using filter expressions. Log entries which do not match _all_ filter expressions will be hidden from view. Syntax for a filter expression:

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
    - `xhr || other |http:` means display entries which match either `xhr` or `other` and have a field which starts with `http:`.
    - `!css || image` means display entries which do not match either `css` or `images` (equivalent to `!css !image` really).
    - Warning: With _or_'ed expressions, the _not_ (`!`) operator can only apply to the resulting _or_'ed expression.
- A special keyword can be used to filter behind-the-scene requests: `bts`, or `|bts` for a stricter filtering.

Examples:

- `!|-- facebook`: show only non-blocked entries with the string `facebook` in it.
- `|xhr google`: show only entries of type `XMLHttpRequest` with the word `google` in it.
- `!|image !|css`: show only entries which are not of type `image`, neither `css`.

***

#### Maximum number of entries

![Figure 9](https://cloud.githubusercontent.com/assets/585534/8035568/aecf93d0-0dbf-11e5-8435-75960644c0c9.png)

This is the maximum number of entries allowed in the logger. When the maximum is reached, the oldest entries at the bottom will be removed to make place to newest entries at the top.

This is useful to be sure the logger does not unduly consume a huge amount of memory if left open for long period of time. Usually, the most recent entries are the ones of interest. When this value is not set, there is a built-in limit of 5,000 entries.

***

#### Accessing popup UI of a specific page

![Figure 10](https://cloud.githubusercontent.com/assets/585534/8037059/aa2717f4-0dc9-11e5-991e-e6381ef3400c.png)

You can access the popup UI of a specific tab by clicking the second cell in a log entry.

This will cause all entries in the logger which are unrelated to the currently opened popup to be dimmed.

***

#### Finding from which list(s) a static filter originates

You can find out from which filter list(s) a static filter originates, by simply clicking on it:

![c](https://cloud.githubusercontent.com/assets/585534/8145767/e2d4eafe-11e3-11e5-9af3-6692531403fa.png)

![a](https://cloud.githubusercontent.com/assets/585534/8145768/e431716a-11e3-11e5-859c-794d37c7c41e.png)

***

#### Creating filters

![Figure 11](https://cloud.githubusercontent.com/assets/585534/8037213/8bac33f8-0dca-11e5-8610-010d0f9ed030.png)

Clicking on the 4th cell of a log entry will give you access to the filtering tools dialog (modal), from where you can easily create dynamic URL filtering rules or just standard static filters, and launch the element picker.

***

##### Dynamic URL filtering rules

![Figure 12](https://cloud.githubusercontent.com/assets/585534/8037337/31bf8a2e-0dcb-11e5-8a23-aef78f943727.png)

Point-and-click to create dynamic URL filtering rules. These rules are temporary by default, you need to click the padlock if you want them to be permanent. Useful to find out which network requests need to be blocked or allowed on a page in order, to fix a broken page, or to further block more useless resources from a page.

See [_"Overview of uBlock's network filtering engine: details"_](https://github.com/gorhill/uBlock/wiki/Overview-of-uBlock's-network-filtering-engine:-details) for more details about where dynamic URL filtering fits in the overall filtering engine.

***

##### Static network filters

![Figure 13](https://cloud.githubusercontent.com/assets/585534/8037377/6ed2d4d4-0dcb-11e5-826c-e5109f72b86b.png)

This dialog will assist you in creating static filters compatible with [ABP filter syntax](https://adblockplus.org/filter-cheatsheet). Note that creating static filters incur a significant overhead relative to dynamic URL filtering rules. Typically, you will first use dynamic URL filtering rules to quickly diagnose which network requests need to be allowed/blocked.

See [_"Overview of uBlock's network filtering engine: details"_](https://github.com/gorhill/uBlock/wiki/Overview-of-uBlock's-network-filtering-engine:-details) for more details about where static filtering fits in the overall filtering engine.
