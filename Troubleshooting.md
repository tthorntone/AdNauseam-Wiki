I am going to collect here common usage issues users may face.

***

#### Unable to open links in new tab

- Are you using the [no-popups switch](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#no-popups)?
- Are you using a Chromium-based browser?

If you answer "yes" to both questions above, this is your problem (from link above):

> **Caveat for Chromium-based browsers:** Due to Chromium API limitations, it's not possible for uBlock to determine for sure whether a new tab being opened is that of a popup, or is the result of a legitimate click on a link by the user. So if the no-popups switch is in use, you won't be able to open a link in a new tab through the context menu.

***

#### Links to social networks are blocked

Because you enabled _"Fanboy’s Social Blocking List"_, or one of the filter lists which includes it, like _"Fanboy’s Annoyance List"_ or _"Fanboy+Easylist-Merged Ultimate List"_.

***

#### My antivirus flags uBlock

False positive.

uBlock ships with malware filter lists, and this causes [false positives](https://github.com/gorhill/uBlock/issues/199) in some antiviruses.