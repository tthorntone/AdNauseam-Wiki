Here is a quick illustrated comparison of efficiency using various angles. Each extension were tested alone, as the only extension present.

### Own memory footprint

These screenshots show the memory footprint of ABP and µBlock _after_ they have gone through this rather [demanding benchmark](https://github.com/gorhill/uBlock/wiki/Reference-benchmark). Once the benchmark was completed, I forced the browser to garbage collect the memory in each extension by clicking the trash icon a couple of times -- this is an _important step_, or else the shown memory footprint is not too reliable.

##### Adblock Plus
![ABP](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/abp-own-mem.png)

##### µBlock
![uBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ublock-own-mem.png)

Both extensions had _EasyList_, _EasyPrivacy_, _Peter Lowe's Ad Server_ list, and malware protection (there are more filters in µBlock for this last one).

### Added overhead to each net request

ABP and µBlock need to process the URL of each net request against all the filters, and eventually tell the waiting browser whether the request should be cancelled or not. Since the browser is waiting for an answer, this is a time critical part and determining whether the request should be allowed or not must be done as fast as possible.

Below are the average time it takes for each extension to handle a net request in their respective `chrome.webRequest.onBeforeRequest` handler, using the same [benchmark](https://github.com/gorhill/uBlock/wiki/Reference-benchmark).

##### Adblock Plus
![ABP](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/abp-obr.png)

##### µBlock
![uBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ublock-obr.png)

Fun fact: µBlock will actually execute more efficiently if you enable _ hpHosts’s Ad and tracking servers_, the timing of `chrome.webRequest.onBeforeRequest` goes below 185 ms when this list is enabled. The key is that filters made of plain hostnames are processed in a very efficient way in µBlock.

### Added memory footprint to web pages

Extensions have their own memory footprint, but they also causes increased memory footprint in web pages. Below you can see the added memory footprint in a very simple web page, [Hacker News](https://news.ycombinator.com/). First screenshot is when no extension at all is used, so consider it as the reference memory footprint for this web page, other screenshots show the increased memory footprint caused by each extension.

##### No extension
![No extension](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/hn-alone.png)

##### Adblock Plus
![ABP](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/hn-abp.png)

##### µBlock
![uBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/hn-ublock.png)

Now keep in mind this is the added footprint for a very simple web page which has no embedded frames. You can multiply the added footprint on the main page by the number of frames embedded on a page, so page with frames can end up consuming a _lot_ more memory than they would have otherwise. A good stress test which demonstrate this is the [infamous vim test](https://github.com/gorhill/httpswitchboard/wiki/Adblock-Plus-memory-consumption).