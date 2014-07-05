### 0.1.3.4
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.3.4.zip) date: 5 July 2014
- Fixed <https://github.com/gorhill/uBlock/issues/46>: "uBlock blocking behind the scene requests while it should not".
    - This was breaking the ability to log in a user's Google account from the browser's _Apps_ page (`chrome://apps`, or `chrome://chrome-signin`).

***

### 0.1.3.3
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.3.3.zip) date: 5 July 2014
- Fixed <https://github.com/gorhill/uBlock/issues/44>: "EasyList Czech and Slovak moved".
- Fixed <https://github.com/gorhill/uBlock/issues/41>: "Extremely generic element hiding selectors are current performance bottleneck".
    - Probably users won't notice this performance improvement, as the test case used was a demanding one:
        - Tested page, heavily bloated front page of <http://www.si.com> ([a demanding page](http://www.youtube.com/watch?v=1NmQvv7MGbE) for cosmetic filters)
        - I used many lists with cosmetic filters in them: _EasyList_, _EasyPrivacy_, _Fanboy Annoyance_, _Fanboy Enhanced Tracking_, _Fanboy Anti-Facebook_.
        - The improvement cuts µBlock's cosmetic filters implementation overhead from 90ms to 60ms per page load for that particularly demanding page (over 2,500 HTML elements), with the above lists (representing over 33,500 cosmetic filters).
        - So if µBlock can do well with this one page, it most certainly can do very well with almost everything else.

***

### 0.1.3.2
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.3.2.zip) date: 2 July 2014
- Translation [work](/gorhill/uBlock/commit/c1421d04236eca315c63704b2e4be9a1f55dd888) by [tlu1024](/tlu1024) (German)
- Fixed <https://github.com/gorhill/uBlock/issues/42>: "Filters using the `~example.com` syntax for the `domain=` option are broken".

***

### 0.1.3.1
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.3.1.zip) date: 2 July 2014
- Translation [work](/gorhill/uBlock/commit/a0a3f5b30b1abae610a14606b6cf3991487e4775) by [faye925](/faye925) (Chinese Simplified)
- Translation [work](/gorhill/uBlock/commit/bdcd1ceadad2fe45136a2fb0b419a798bbdf3214) by [tailHey](/tailHey) (French)

***

### 0.1.3.0
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.3.0.zip) date: 2 July 2014
- New _"Statistics"_ tab in the dashboard: to see which requests were blocked on a particular page.
    - Optional, disabled by default in order to prevent overhead such a feature introduce for users who will never care about this level of details.
    - If enabled, there will be a small eye icon in the popup to easily access the tab.
- Translation work by [Ginohax](/Ginohax) (Italian).
- Fixed <https://github.com/gorhill/uBlock/issues/37>: "Avoid avoidable overhead in contentscript_end.js ..."
- Fixed <https://github.com/gorhill/uBlock/issues/12>: "Possibility to view blocked elements + corresponding filters"

***

### 0.1.2.0
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.2.0.zip) date: 30 June 2014
- Translation work by [Ginohax](/Ginohax) (Italian).
- Added exception filters [to make hpHosts more usable](/gorhill/uBlock/issues/17).

***

### 0.1.1.1
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.1.1.zip) date: 29 June 2014
- Translation work by [tailHey](/tailHey) ([French](/gorhill/uBlock/commits?author=tailHey)) and [tlu1024](/tlu1024) ([German](https://github.com/gorhill/uBlock/commits?author=tlu1024)).
- Fixed <https://github.com/gorhill/uBlock/issues/33>: "Need translation of detailed description: German".
- Fixed <https://github.com/gorhill/uBlock/issues/28>: "Parse and enforce Adblock+ element hiding filters option not working properly".

***

### 0.1.1.0
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.1.0.zip) date: 27 June 2014
- **New setting:** In _"Settings"_ tab of the dashboard: _"Hide placeholders of blocked elements"_.
    - Check to prevent blocked images and frames to take space on the page.
- [Translation work](/gorhill/uBlock/pull/24) by [tlu1024](/tlu1024) (German)
- Fixed <https://github.com/gorhill/ublock/issues/25>: "Add the new Fanboy's "Anti-Facebook Filters".
- Fixed <https://github.com/gorhill/ublock/issues/7>: "Blocked contents don't always disappear properly".

***

### 0.1.0.11
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.0.11.zip) date: 27 June 2014
- Fixed <https://github.com/gorhill/ublock/issues/21>: "Have uBlock maintain its own list of filters to unbreak sites".
- Fixed <https://github.com/gorhill/ublock/issues/20>: "Cannot directly access forum on xda-developers.com from front page".

***

### 0.1.0.10
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.0.10.zip) date: 26 June 2014
- Fixed <https://github.com/gorhill/ublock/issues/18>: "Conflict with HTTPS Everywhere extension in Chrome".
    * In order to fix this, I had to reverse the partial solution put in place to fix [issue #7](/gorhill/uBlock/issues/7#issuecomment-47301344), "Blocked contents don't always disappear properly".
- [Fixed bad test](/gorhill/uBlock/commit/a6496e5cfb76d1a13d3ca8836cb21d5969b49ae7) in request handler.

***

### 0.1.0.9
- Release date: Not released yet
- Fixed <https://github.com/gorhill/ublock/issues/16>: "Changelog links wrong".
    * The link was right, problem was an issue with mixing jQuery's `$()` with `window.addEventListener('load', ...)`.

***

### 0.1.0.8
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.0.8.zip) date: 25 June 2014
- Fixed <https://github.com/gorhill/ublock/issues/14>: "Twitter glitches when using Fanboy’s Annoyance List".

***

### 0.1.0.7
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.0.7.zip) date: 25 June 2014
- Fixed <https://github.com/gorhill/ublock/issues/13>: "Google ads on Google.com".

***

### 0.1.0.6
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.0.6.zip) date: 24 June 2014
- Partially addressed <https://github.com/gorhill/ublock/issues/7> and <https://github.com/gorhill/ublock/issues/11>: Redirecting to no-op contents whenever possible.

***

### 0.1.0.5
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.0.5.zip) date: 24 June 2014
- Added a hint in the popup about the purpose of the power button. See <https://github.com/gorhill/uBlock/commit/225bc2d33c5743f0ce1394e2dac9aa0c37c14e48?

***

### 0.1.0.4
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.0.4.zip) date: 24 June 2014
- Fixed <https://github.com/gorhill/ublock/issues/1>: "It blocks playing music on soundcloud.com".

***

### 0.1.0.0
- [Release](/gorhill/ublock/blob/master/dist/ublock_0.1.0.0.zip) date: 23 June 2014
- First release.