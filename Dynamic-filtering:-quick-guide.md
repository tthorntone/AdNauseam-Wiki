No wall of text, let's cut to the chase.

Dynamic filtering pane ([available only to advanced users](https://github.com/gorhill/uBlock/wiki/Advanced-user-features)):

![figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-01.png)

***

#### Important

_Static filtering_ refers to the filters which comes from the filter lists, i.e. _EasyList_, _EasyPrivacy_, hpHosts, etc. _Dynamic filtering_ are those filtering rules which have an air of firewall rules.

***

First column: what is to be dynamically filtered:

![figure 2](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-02.png)

As you can see, you can create dynamic filtering rules for object types, or hostnames according to their origin.

The color of an entry indicate whether all requests were blocked (reddish), all requests were allowed (greenish), or some were blocked some were allowed (yellowish).

In bold, domain names. Domain names are hostnames, but hostnames are not necessarily domain names from µBlock's point of view: domain names are extracted as per [Mozilla Public Suffix list](https://publicsuffix.org/).

Second column: global dynamic filtering rules, i.e. whatever rule appears in this column applies everywhere, on all sites:

![figure 3](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-03.png)

Third column: local dynamic filtering rules, i.e. whatever rule appears in this column applies to the current site only:

![figure 4](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-04.png)

The cells in the third column gives an overview of how many requests were blocked/allowed:

- `-` or `+` = between 1-9 network requests were blocked or allowed, respectively
- `--` or `++` = between 10-99 network requests were blocked or allowed, respectively
- `---` or `+++` = 100 or more network requests were blocked or allowed, respectively
- blank cell = no network requests occurred for the specific hostname

So there are **global** dynamic filtering rules, and **local** dynamic filtering rules.

Sensible security- and privacy-wise: blocking all 3rd-party frames by default everywhere: 

![figure 5](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-05.png)

***

#### Important

_Dynamic filtering_ override _static filtering_. This means a _block_ dynamic rule will override any existing _allow_ static filters. This means you can block with 100% certainty using dynamic filtering rules. Similarly, an _allow_ dynamic filtering rule will override any existing _block_ static filters, i.e. you can allow with 100% certainty with dynamic filtering (useful to un-break sites broken by some static filters).

***
All embedded 3rd-party frames were blocked on the page. Good. However it appears there was an embedded Youtube video in the article:

![figure 6](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-06.png)

If you want to block all 3rd-party frames by default, except for embedded Youtube videos on that particular site, two solutions.

##### First solution

Create a local  _noop_ rule for 3rd-party frames:

![figure 7](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-07.png)

It works, the embedded Youtube video can now be played.

However the above rule would result in all 3rd-party frames to be unblocked. Not so good.

##### Second solution

Create a local _noop_ rule for `youtube.com`:

![figure 8](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-08.png)

This will prevent dynamic filtering rules to apply to anything from `youtube.com`.

***

#### Important

Remember that _noop_ rules bypass **only** broader dynamic filtering rules, static filtering is left completely intact, which means you won't see ads in the embedded Youtube videos.

***

What if you want to block 3rd-party frames everywhere by default, but want whatever embedded Youtube video to not be blocked by default?

It is just a matter of creating a global _noop_ rule for `youtube.com`:

![figure 9](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-09.png)

Which means: do not apply any dynamically filtering rule to `youtube.com` by default (i.e. everywhere).

***

#### Important

Local dynamic filtering rules override global ones.

More specific dynamic filtering rules override less specific ones. For example, dynamic filtering rules for `youtube.com` (specific) override dynamic filtering rules for `3rd-party frames` (generic).

***

We covered the _block_ and _noop_ dynamic filtering rules. What about the _allow_ rule?

The dynamic filtering _allow_ rule is most useful to un-break sites broken by some static filters.

[Someone found out](https://twitter.com/r3volution11/status/549584186320117760) Boldchat site was broken when using µBlock:

![figure 10](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-10.png)

The content of the dynamic filtering pane makes it clear that there is a static filter somewhere blocking network requests to `boldchat.com`. Turned out there was static filter `boldchat.com` in _"Peter Lowe's Ad Server"_ list.

Using a local  _allow_ dynamic filtering rule fixes the breakage:

![figure 11](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-qg-11.png)

It is easier for a user to point-and-click for a quick fix then to actually craft an exception static filter like `@@||boldchat.com$~third-party` and force a reload of all static filters (big memory churning).

***

#### Important

Typically, use only narrow _allow_ dynamic filtering rules to un-break sites. As these _allow_ rules override any static filtering, this means if you use a too broad _allow_ dynamic filtering rule you could start to allow in ads/trackers/annoyances.

***

More: [Take control of your privacy in your own hands](https://github.com/gorhill/uBlock/issues/433#issuecomment-68488686) (will move this here eventually, I need a break)