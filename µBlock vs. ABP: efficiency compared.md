Here is a quick illustrated comparison of efficiency using various angles. Each extension were tested alone, as the only extension present. Benchmarking was performed with Chromium on Linux Mint 64-bit.

- [Own memory footprint](#own-memory-footprint)
- [Added CPU overhead to each net request](#added-cpu-overhead-to-each-net-request)
- [Added memory footprint to web pages](#added-memory-footprint-to-web-pages)
- [Added CPU overhead to web pages](#added-cpu-overhead-to-web-pages)

By the way, I need to dispel a silly myth given how often it surfaces: [Adblock Edge uses Adblock Plus filtering engine](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/abp-abe.png), so it is **not** more efficient as ABP.

### Own memory footprint

These screenshots show the memory footprint of ABP and µBlock _after_ they have gone through this rather [demanding benchmark](https://github.com/gorhill/uBlock/wiki/Reference-benchmark). Once the benchmark was completed, I forced the browser to garbage collect the memory in each extension by clicking the trash icon (in dev console) a couple of times -- this is an _important step_, or else the shown memory footprint is not too reliable.

##### Adblock Plus
![ABP](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/abp-own-mem.png)

##### µBlock
![uBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ublock-own-mem.png)

Both extensions had _EasyList_, _EasyPrivacy_, _Peter Lowe's Ad Server_ list, and malware protection (there are more filters in µBlock for this last one).

### Added CPU overhead to each net request

ABP and µBlock need to evaluate the URL of each net request against their dictionary of filters, and eventually tell the waiting browser whether the request should be cancelled or not. Since the browser is waiting for an answer, this is a time critical part and determining whether the request should be allowed or not must be done as fast as possible.

Below are the average time it takes for each extension to handle a net request in their respective `chrome.webRequest.onBeforeRequest` handler, using the same [benchmark](https://github.com/gorhill/uBlock/wiki/Reference-benchmark).

##### Adblock Plus
    ABP > onBeforeRequest: 0.286 ms (19448 samples)
    ABP > onBeforeRequest: 0.286 ms (19697 samples)
    ABP > onBeforeRequest: 0.286 ms (19890 samples)
    ABP > onBeforeRequest: 0.285 ms (20157 samples)
    ABP > onBeforeRequest: 0.284 ms (20675 samples)
    ABP > onBeforeRequest: 0.284 ms (20790 samples)
    ABP > onBeforeRequest: 0.284 ms (20956 samples)
    ABP > onBeforeRequest: 0.284 ms (21112 samples)
    ABP > onBeforeRequest: 0.283 ms (21279 samples)
    ABP > onBeforeRequest: 0.283 ms (21472 samples)

##### µBlock
<sup>[Note: The overhead was [further minimized](https://github.com/gorhill/uBlock/issues/238) with subsequent versions of µBlock]</sup>

    µBlock > onBeforeRequest: 0.173 ms (18913 samples)
    µBlock > onBeforeRequest: 0.172 ms (19177 samples)
    µBlock > onBeforeRequest: 0.172 ms (19354 samples)
    µBlock > onBeforeRequest: 0.172 ms (19681 samples)
    µBlock > onBeforeRequest: 0.171 ms (20139 samples)
    µBlock > onBeforeRequest: 0.171 ms (20311 samples)
    µBlock > onBeforeRequest: 0.171 ms (20461 samples)
    µBlock > onBeforeRequest: 0.171 ms (20610 samples)
    µBlock > onBeforeRequest: 0.171 ms (20756 samples)
    µBlock > onBeforeRequest: 0.171 ms (20933 samples)

Note that the results above are the tail end of running the complete benchmark (60 front pages of high traffic web sites, repeated 3 times). 

Also noteworthy, ABP uses a cache mechanism to possibly avoid having to test a URL by trying to reuse a prior
result for that same URL, which would cause ABP timing to be quite low (at the expense of memory footprint). It's unclear to me how much this mechanism kicked in with the current benchmark. µBlock doesn't use such mechanism, so whether a web page is visited repeatedly or not doesn't influence timing.

### Added memory footprint to web pages

Extensions have their own memory footprint, but they also cause increased memory footprint in web pages. Below you can see the added memory footprint in a very simple web page, [Hacker News](https://news.ycombinator.com/). First screenshot is when no extension at all is used, so consider it as the reference memory footprint for this web page, other screenshots show the increased memory footprint caused by each extension. The browser was left on idle after loading the page in order to allow the garbage collector to kick in.

**No extension:**<br>
![No extension](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/hn-alone.png)

**Adblock Plus:**<br>
![ABP](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/hn-abp.png)

**µBlock:**<br>
![uBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/hn-ublock.png)

Now keep in mind this is the added footprint for a very simple web page which has no embedded frames. You can multiply the added footprint on the main page by the number of frames embedded on a page, so page with frames can end up consuming a _lot_ more memory than they would have otherwise. For instance, a very simple web page with a couple of `iframe` in it, [The Acid3 Test](http://acid3.acidtests.org/):

![uBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/acid3test-mem.png)<br>
<sup>Added memory footprint: Left = no extension. Middle = Adblock Plus. Right = µBlock.</sup>

A good stress test which further demonstrate this is the [infamous vim test](https://github.com/gorhill/httpswitchboard/wiki/Adblock-Plus-memory-consumption).

##### µBlock vs. Adblock: memory usage differential during reference benchmark

![µBlock vs. Adblock: memory usage differential during reference benchmark](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/media/ublock-vs-abp-cpu-2.png)

Above picture gives an overview of how much more memory Adblock Plus consumes over µBlock. It represents the **extra memory** ABP consumes relative to µBlock -- so essentially µBlock is the horizontal axis. If memory consumption of ABP and µBlock were exactly the same, there would be no graph. The [reference benchmark](/gorhill/uBlock/wiki/Reference-benchmark) was used, which consists of visiting 60 front pages of high traffic web sites.

The vertical axis represents MB. The horizontal axis is time in seconds, and the data was tediously extracted from [this video](https://www.youtube.com/watch?v=DKM78oV_ftg) (consider the video to be the raw data -- [here is the spreadsheet](https://github.com/gorhill/uBlock/blob/master/doc/benchmarks/ublock-vs-abp-timeline.ods) so people can double check in doubt).

The blue area represents how much more ABP itself consumes more memory than µBlock. The orange area represents how much more ABP causes the web pages themselves to consume more memory. ABP systematically causes web pages to consume more memory, and often quite a lot, north of 100 MB for some sites. This kind of added short term memory overhead is not cheap, as it also means the CPU is working harder.

### Added CPU overhead to web pages

This is the benchmarks comparing CPU usage in the background page when loading [si.com](http://www.si.com) ten times (so you can shift one decimal to the left for per page figures). Each page load was triggered after the previous page load completed.

**Top:** Adblock Plus 1.8.3. **Bottom:** µBlock 0.5.1.0.

![CPU benchmark](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/bgpage-cpu-si.comx10.png)

I did measure CPU usage for content scripts (above benchmarks are for background pages), but given the web page used for the benchmark is quite a bloated one, the useful figures were drowned in a sea of noise. But the fact that ABP inserts 14,000+ CSS rules caused the CPU to used be much more than µBlock (2-3 to 1 ratio) when comparing content script CPU usage (again, above is background page CPU usage).

Also, the amount of work µBlock does in its content scripts is proportional to the complexity of a web page. So given µBlock did much better CPU-wise than ABP in its content script for such a bloated web site means it was a worst-case scenario for µBlock, and yet it did its job of hiding elements between 2 and 3 times faster.

### Related wiki pages

- [Counterarguments: Who care about efficiency, I have 8 GB](https://github.com/gorhill/uBlock/wiki/Counterarguments#who-care-about-efficiency-i-have-8-gb)
- [Net request filtering efficiency: HTTP Switchboard vs. Adblock Plus](https://github.com/gorhill/httpswitchboard/wiki/Net-request-filtering-efficiency:-HTTP-Switchboard-vs.-Adblock-Plus)
- [Adblock Plus memory consumption](https://github.com/gorhill/httpswitchboard/wiki/Adblock-Plus-memory-consumption)