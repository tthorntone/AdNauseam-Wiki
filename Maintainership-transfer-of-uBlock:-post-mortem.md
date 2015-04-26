**Update (2015-04-25)**: issue resolved, see <https://github.com/gorhill/uBlock/issues/130#issuecomment-96321347>:

> The issue has been fixed, and we can all move on. I didn't know @chrisaljoudi was that young, so given this I will assume it was a fumble with no real bad intent.

***

On April 1st, when I transferred **maintainership** of uBlock<sup>[1]</sup>, as far as I am concerned, I was transferring to the [The uBlock Development Team](https://github.com/chrisaljoudi/uBlock/commit/50e621d4ee46479b40e36319cbab68985d7527a5). In practice, of course I had to transfer to one of the member of the [The uBlock Development Team](https://github.com/chrisaljoudi/uBlock/commit/50e621d4ee46479b40e36319cbab68985d7527a5), which happened to be @chrisaljoudi.

Things did not turn out as expected. A few days afterward, I learned that @chrisaljoudi had proceeded to _immediately_ misrepresent (and still does as of April 24th) the project on [his home page](https://chrismatic.io/ublock/) with _"made [...] by Chris"_. uBlock is _not_ made by @chrisaljoudi, it is made by [The uBlock Development Team](https://github.com/chrisaljoudi/uBlock/commit/50e621d4ee46479b40e36319cbab68985d7527a5)<sup>[2]</sup>, of which @chrisaljoudi was one of the developers<sup>[3]</sup>. This misrepresentation is made worst by the fact that it was coupled with a plea for donations.<sup>[4]</sup>

I have nothing against developers asking for donations for writing free and open source software, this is very common and there is nothing wrong with this. It's a personal choice. However, I don't tolerate too well misrepresentation in order to financially benefit from the work of others, which I now conclude is the case here -- there is so much assumption of good faith one can give.

Before @chrisaljoudi took over the project, his github contribution stats were ["2,397 ++ / 2,734 --"](https://github.com/gorhill/uBlock/graphs/contributors) (meaning "2,397 lines removed, 2,734 lines added" -- and this covers more than just actual coding work). Currently, his github contribution stats on <https://github.com/chrisaljoudi/uBlock> stand at ["22,057 ++ / 15,483 --"](https://github.com/chrisaljoudi/uBlock/graphs/contributors).

You might be fooled into thinking there is a lot of work contributed since he took over in these stats, but the reality is that most of these "contributions" (17,827 ++ / 10,542 --) are the results of running the `assets/update-3rdparties.sh` script, which purpose is to pull and commit changes in the 3rd-party filter lists (EasyList, EasyPrivacy, Peter Lowe's, etc.), so these are really other people contributions -- the maintainers of filter lists.<sup>[5]</sup>

I am perplexed as to why @chrisaljoudi as been currently updating the 3rd-party assets so often, there is no real need for doing so, as the cached filter lists will be updated by uBlock itself every 4-5 days on the user side, so it is rather pointless to update the repo -- and this even bad, as this causes uBlock to see the filter lists as obsolete and pull again what might just have been pulled an hour ago. The best time to run the `assets/update-3rdparties.sh` script is when a package is created for a new release.

So anyways, removing the contributions from the automated script, this means @chrisaljoudi's git contributions become 1,833 ++ / 2,207-- since he took over maintainership. Now my point is not to understate the work done, rather to be sure it is not (conveniently) **overstated** -- given development work is used as an argument in seeking donations.<sup>[7]</sup>

Now factor in that many commits were actually to commit pull requests from other contributors, add to this that some of his changes were to actually [**remove** code](https://github.com/chrisaljoudi/uBlock/commit/fa3666f85d7dddfc274f6f27d20c6787d8bc43b8#diff-305c2fdde2804d752c9bfde050f38df9) ([per-site switches are gone](https://github.com/chrisaljoudi/uBlock/issues/1306)), and add to this that @chrisaljoudi pulled development work from my branch with [authorship stripped](https://github.com/gorhill/uBlock/issues/69)<sup>[6]</sup> (which would likely fool an outsider into thinking he worked to develop the code<sup>[7]</sup>)

I have exhausted all assumption of good faith I could give, this is currently what I see about the [chrisaljoudi/uBlock](https://github.com/chrisaljoudi/uBlock) repo:

- uBlock is _still_ the product of a whole lot of work by _many_ different contributors
- Removing authorship information
- Misrepresentation: uBlock is _"made [...] by Chris"_
- To me it does appear most of the work by @chrisaljoudi since taking over has been to [_market_](https://chrismatic.io/ublock/) uBlock.
- @chrisaljoudi actively seeking donations to _"make uBlock happens"_<sup>[8]</sup>
- On December 13th 2014, @chrisaljoudi wrote me, he was interested to "send over [...] < $1,000 to support the work on the Safari version"<sup>[9]</sup>

Bluntly said, my opinion from what I have observed, and in hindsight, I now believe @chrisaljoudi's _primary_ motivation is to cash in on uBlock.

For insight, look at [RequestPolicy Continued](https://requestpolicycontinued.github.io/), which is the continuation of [RequestPolicy](https://github.com/RequestPolicy/requestpolicy). See the glaring differences in the spirit of the project.

Given all this, I will just keep developing uBlock Origin as if I was working on the original repo.

I will just ensure now that it doesn't turn into a customer support outlet for filter lists and endless requests for features (to keep throwing "features" at a piece of software is a good way to sabotage it -- so I am currently _extremely_ selective).

uBlock is mature, most issues encountered nowadays are with the filter lists, and this could be taken care by volunteers elsewhere than on the github repo (I think there is a reddit section somewhere now).

***

[1] Because most of my own time had become invested in "customer support" rather than development work.

[2] More accurately, "All the uBlock contributors", which is [something I corrected in my own branch](https://github.com/gorhill/uBlock/commit/4a02246bfeb531b95a2a12102375aee73c0fba38).

[3] To work on, and improve the Safari port, which was originally brought to life by @Deathamns. 

[4] Hence the reason I tried [to reclaim uBlock's original name](https://github.com/gorhill/uBlock/commit/581bc66509e8bf94d65a7ee54ba850116cede3c0).

[5] @chrisaljoudi [**immediately** toned down my original emphasis on the contributions of filter list maintainers](https://github.com/chrisaljoudi/uBlock/commit/f256801344a5178261cad5130a7f4be1ec061343
) upon taking over maintainership of uBlock.

[6] I undestand sometimes it may be desirable to import manually changes, in such case the solution is [to document where the code comes from](https://github.com/gorhill/uBlock/commit/63d9143d6bfdac1d603b5f8f62f99aecc67371d2).

[7] <https://chrismatic.io/ublock/>: "your donations keep development possible"

[8] uBlock is _already_ a reality _and_ mature, it already "happened".

[9] I had **completely forgotten** about that email. I never answered to it because it annoyed me at the time and I just dismissed it immediately: the Safari port was [already done by @Deathamns](https://github.com/chrisaljoudi/uBlock/tree/857acaf2d2cc02b446f64d8958f31421e9d01c3b/platform), and it bothered me that he was offering to pay me (which I clearly mention not wanting in the project), and worst, to pay _me_ for the work of someone else (@Deathamns). I never answered back and dismissed the email as yet another annoying unsolicited uBlock-related email. I found this email I had forgotten when uBlock Origin was pulled from the Chrome store, I was trying to find the email notification supposedly sent by the Chrome store. In retospect, I now see very well the point of his offer: to cash in on a Safari version of uBlock.