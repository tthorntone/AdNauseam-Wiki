For conciseness, "uBlock Origin" shortened as "uBlock" below.

#### 10 Ad Blocking Extensions Tested for Best Performance

<sup>Link: <https://www.raymond.cc/blog/10-ad-blocking-extensions-tested-for-best-performance/></sup>

The author of the benchmark mentions that the default settings of all tested blockers were used, except for Ghostery, which was set to block "advertising blocking option" only.

The fact that default settings were used for all blockers does put uBlock at an advantage and also at a disadvantage:

- The more stuff blocked the more likely this will improve page load time.
- The more filters are parsed and enforced, the more likely this will increase CPU and memory footprint.

uBlock is **uncompromisingly pro-user interests**, and as such its default installation is to block ads, trackers, malwares, etc.<sup>[1]</sup> As of writing, uBlock's default installation consists of loading into memory over 46,000 network filters and over 34,000 cosmetic filters.

Such a high amount of filters will cause uBlock to block more than any of the other blockers when used with their default settings.

On the other hand, this will also put uBlock at a disadvantage resource-wise when compared to a blocker which just block ads -- which is how the other blockers in the benchmark were set up, it's their default settings<sup>[2]</sup>. For comparison, in the benchmark, only ~1,000 filters were enforced in Ghostery.

And yet, uBlock was the best or among the best performers CPU- and memory-wise. Had uBlock and the other blockers been set to block roughly equally, the contrast between uBlock's efficiency and other blockers would have been even more pronounced in favor of uBlock, as the CPU- and memory-footprint of the other blockers would have increased if set to block as much as uBlock with its default settings.

uBlock was written from scratch with efficiency in mind, and whatever new features is added to uBlock is done in a way that never compromise uBlock's efficiency -- being resource-efficient is a primary feature of uBlock, something not to be messed up.

***

[1] What does "uncompromisingly pro-user" mean? Here is [an example](https://github.com/chrisaljoudi/uBlock/issues/564#issuecomment-70843550).

[2] Adblock Plus, Adguard will actually prevent many ads from being blocked with default settings, through their "acceptable ads" feature, which is enabled by default. I consider "acceptable ads" to be an anti-user feature, and as such this has no place in uBlock (see [this](https://github.com/gorhill/uBlock/blob/master/MANIFESTO.md), [this](https://github.com/chrisaljoudi/uBlock/issues/66). [this](https://github.com/gorhill/uBlock/issues/541#issuecomment-126721395)).