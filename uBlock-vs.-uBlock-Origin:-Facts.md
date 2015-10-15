#### uBlock is the main branch, uBlock Origin is just bug fixes

Instance: _"If you're currently using uBlock Origin, you're welcome to move over to the **main uBlock project**"_ ([ublock.org's FAQ](https://www.ublock.org/faq/)).

Completely false.

Compare release history of both projects:
- [uBlock](https://github.com/chrisaljoudi/uBlock/releases)
- [uBlock Origin](https://github.com/gorhill/uBlock/releases)

Summary ([as per Wikipedia](https://en.wikipedia.org/wiki/UBlock)):

| uBlock | uBlock Origin |
|--------|---------------|
| | manual editing of per-site switches |
| | [per-site cosmetic filtering switch](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#no-cosmetic-filtering) |
| [cosmetic filtering thru Inspector (FF)](https://github.com/chrisaljoudi/uBlock/issues/1211#issuecomment-91652206) | |
| [UI changes](https://github.com/chrisaljoudi/uBlock/releases/tag/0.9.3.5) (reskin) | |
| [elimination of font based icons](https://github.com/chrisaljoudi/uBlock/issues/1181) | |
| [~~per-site switches~~](https://github.com/chrisaljoudi/uBlock/issues/1306) ([removed](https://github.com/chrisaljoudi/uBlock/commit/fa3666f85d7dddfc274f6f27d20c6787d8bc43b8#diff-305c2fdde2804d752c9bfde050f38df9)) | |
| [~~strict blocking~~](https://github.com/chrisaljoudi/uBlock/issues/1306) ([removed](https://github.com/chrisaljoudi/uBlock/commit/fa3666f85d7dddfc274f6f27d20c6787d8bc43b8#diff-6e66de32e163ae59682ad852a7ca3762)) | |
| | [color-blind mode](https://github.com/chrisaljoudi/uBlock/issues/467#issuecomment-95177219) |
| | [unified logger](https://github.com/gorhill/uBlock/wiki/The-logger) |
| | cosmetic filters in request logger |
| [toolbar support for legacy Firefox](https://github.com/chrisaljoudi/uBlock/pull/1321) | |
| [inline-script blocking for Safari](https://github.com/chrisaljoudi/uBlock/commit/82118cb075732549289d3accb8cf3ea6d9f9d9fc) | |
| cosmetic filters in request logger | |
| | [dynamic URL filtering](https://github.com/gorhill/uBlock/wiki/Dynamic-URL-filtering) |
| [network filtering thru Inspector (FF)](https://github.com/chrisaljoudi/uBlock/pull/1324) |
| | [privacy: block browser pre-fetching](https://github.com/gorhill/uBlock/wiki/Dashboard:-Settings#disable-pre-fetching) |
| | [privacy: block hyperlink auditing/beacon](https://github.com/gorhill/uBlock/wiki/Dashboard:-Settings#disable-hyperlink-auditingbeacon) |
| | [create static filters thru logger](https://github.com/gorhill/uBlock/wiki/The-logger#static-network-filters) |
| | [per-site switch to disable remote fonts](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#no-remote-fonts) |
| | [filter list identification for static filters](https://github.com/gorhill/uBlock/wiki/The-logger#finding-from-which-lists-a-static-filter-originates) |
| | [toolbar support for legacy Firefox](https://github.com/gorhill/uBlock/issues/264)  |
| | [privacy: prevent local IP address leak through WebRTC](https://github.com/gorhill/uBlock/wiki/Dashboard:-Settings#prevent-webrtc-from-leaking-local-ip-address)  |
| | [DOM inspector](https://github.com/gorhill/uBlock/releases/tag/1.0.0.0)  |
| | [cloud storage support](https://github.com/gorhill/uBlock/wiki/Cloud-storage)  |
| | [inline script tag filtering](https://github.com/gorhill/uBlock/wiki/Inline-script-tag-filtering) |

Bug/issue fixing is as important -- if not more -- as adding useful features, especially for a project which represents itself as being under active development.

Reported [issues have been, and continue to fixed in uBlock Origin](https://github.com/gorhill/uBlock/issues?q=is%3Aissue+is%3Aclosed+sort%3Aupdated-desc).

As of writing (2015-08-28), uBlock development has been essentially stalled for weeks now, and this includes [bug fixing](https://github.com/chrisaljoudi/uBlock/issues?q=is%3Aissue+is%3Aclosed+sort%3Aupdated-desc) (despite the maintainer's claim that the _"uBlock team works to develop and design uBlock"_ on his [donation page](https://donorbox.org/ublock)).

***

#### "uBlock Origin is more efficient than uBlock" or "uBlock is more efficient than uBlock Origin"

Nonsense.

What makes uBlock efficient is the core filtering engine, which is composed of many parts. The filtering engine was mature at the time of the fork, and aside [some refactoring in uBlock Origin](https://github.com/gorhill/uBlock/commit/2234933b82d1c17af42ba574b6515937c7515029#diff-522a16ddeed280252d7c3a351261b441) to fix [issue #58](https://github.com/gorhill/uBlock/issues/58) and [issue #59](https://github.com/gorhill/uBlock/issues/59), the core filtering engine is essentially the same in both branches, i.e. virtually same performance. **Update** (2015-08-28): static filtering engine is further diverging with [fix to uBlock Origin issue #621](https://github.com/gorhill/uBlock/issues/621).

- [uBlock: `static-net-filtering.js`](https://github.com/chrisaljoudi/uBlock/commits/master/src/js/static-net-filtering.js) vs [uBlock Origin `static-net-filtering.js`](https://github.com/gorhill/uBlock/commits/master/src/js/static-net-filtering.js)
- [uBlock: `cosmetic-filtering.js`](https://github.com/chrisaljoudi/uBlock/commits/master/src/js/cosmetic-filtering.js) vs [uBlock Origin `cosmetic-filtering.js`](https://github.com/gorhill/uBlock/commits/master/src/js/cosmetic-filtering.js)
- [uBlock: `contentscript-end.js`](https://github.com/chrisaljoudi/uBlock/commits/master/src/js/contentscript-end.js) vs [uBlock Origin `contentscript-end.js`](https://github.com/gorhill/uBlock/commits/master/src/js/contentscript-end.js)

***

#### Chris Aljoudi is "the creator of uBlock"

Instances: [here](https://twitter.com/thenickde/status/614503721590898688).

Completely false.

[Chris Aljoudi](https://github.com/chrisaljoudi) was [one of the lesser contributors](https://github.com/gorhill/uBlock/graphs/contributors) when he was handed over **maintainership** on April 1st:

![a](https://cloud.githubusercontent.com/assets/585534/8421391/cbd59f96-1e9b-11e5-886d-278a00a32792.png)

Before being handed over **maintainership**, he was taking care to further develop the Safari port of uBlock, which was first [brought entirely](https://github.com/gorhill/uBlock/commits/master/platform/safari?page=3) to [life originally](https://github.com/gorhill/uBlock/commits/98464a56fe4fa2a28372018640d648a1f772ea36/meta/safariextz) by another developer, [Deathamns](https://github.com/Deathamns).

Since being handed over the project, his _own_ uBlock work has _mostly_ consisted of [re-skinning uBlock](https://github.com/chrisaljoudi/uBlock/releases).

So to call him the "creator of uBlock" is a quite low blow to those who actually did all the real hard work to make uBlock what it is today.

#### "Raymond Hill [left] the project only to come back about a week later"

Instances: [here](http://ubuntuforums.org/showthread.php?t=2284427).

Completely false.

I handed over **maintainership**, upon which I _immediately_ created a fork of my own project so that I could continue to work in a more quiet environment -- as my own time had become dedicated to answer spurious issues on GitHub.

See my [commit history](https://github.com/gorhill/uBlock/commits/master): at no point did I stop working on uBlock. And as far as I am concerned, this worked, as I finally could immediately find the time to do actual code and work to finally resolve [long](https://github.com/gorhill/uBlock/issues/58) [standing](https://github.com/chrisaljoudi/uBlock/issues/68) [issues](https://github.com/chrisaljoudi/uBlock/issues/308), while bringing in new features. See [release history](https://github.com/gorhill/uBlock/releases) for details (the fork occurred right before 0.9.3.0).

#### uBlock Origin "is more chrome focused"

Instances: [here](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/reviews/722444/) [I've seen more, will add them]

Completely false.

I don't shy away at [working on the Firefox code base](https://github.com/gorhill/uBlock/commits/master/platform/firefox) (including refactoring where needed):
- [987a8d2b644ea445a0d64e78d7c2ab9c4d5da989](https://github.com/gorhill/uBlock/commit/987a8d2b644ea445a0d64e78d7c2ab9c4d5da989)
- [b084d796b50a4c5f930e5fbf9217a49322687c9e](https://github.com/gorhill/uBlock/commit/b084d796b50a4c5f930e5fbf9217a49322687c9e), [6470216530548cd3dfecdce7d9aa94816d10d863](https://github.com/gorhill/uBlock/commit/6470216530548cd3dfecdce7d9aa94816d10d863)
- [53fc1063f9281ebbe6d5c5c50ef6ba37bb22ffe9](https://github.com/gorhill/uBlock/commit/53fc1063f9281ebbe6d5c5c50ef6ba37bb22ffe9), [c285ace7d84115fdcac3e2b6009a481e4dc34b91](https://github.com/gorhill/uBlock/commit/c285ace7d84115fdcac3e2b6009a481e4dc34b91)
- [d41408ebbc8b14b77effaa40254a280c42390a3e](https://github.com/gorhill/uBlock/commit/d41408ebbc8b14b77effaa40254a280c42390a3e)