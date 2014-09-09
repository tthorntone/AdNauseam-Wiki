µBlock is quite memory efficient compared to most other blockers. However, users will often report that this is not the case, or not as impressive as "advertised" by the official documentation.

I already wrote about this [here](https://github.com/gorhill/uBlock/wiki/Myth:-%C2%B5Block-consumes-over-80MB). I will add more details here, as there is more than just garbage collection to factor in. 

When I run my benchmarks, the methodology used is to reproduce what I believe is the most common scenario: a user launches his/her browser with µBlock already fully configured to his/her liking, without further changes to the selection of filter lists. The launch-and-forget scenario. I also benchmark this way for all other blockers.

However there are specific operations which will cause µBlock to churn through lot of short-term memory (let's call this "memory-churning"), and although all that short-term memory is freed by µBlock once the specific operation is completed, not all that freed memory will be garbage-collected by the browser for whatever reasons. Memory fragmentation is possibly a factor.

Memory-churning operations lead to a permanently higher memory baseline for µBlock, as can be seen in the browser's _Task Manager_.

So in essence you won't obtain the same memory figures which I used in my published benchmarks if you caused µBlock to go through memory-churning before looking at the memory figures, even after letting the browser's garbage collector do its job.

Reloading all the filters is the most severe memory-churning operation in µBlock. Here are operations which causes all the filters to be reloaded:

- Launching or restarting µBlock (obviously).
- Changing the selection of filter lists.
- Adding removing custom filters.
- Updating the filter lists (this may be done automatically if _Auto-update_ is enabled).

Additionally, with version 0.6+, µBlock is able to create a selfie to improve its load time next time the browser is launched, and creating a selfie is also a memory-churning operation. However for this one particular operation, once the selfie is created, the reward is that subsequent launch of µBlock will become very efficient CPU- and memory-wise -- as all the downloading/parsing of filters from raw text files will be completely bypassed, causing µBlock to be fully loaded and ready in a fraction of the time it takes when no good selfie is available.

The time at which a selfie is created is at µBlock's discretion. Currently, this will happen some minutes after the filter lists has been loaded, so as to avoid launching memory-churning selfie creation operations before there is a good likelihood the user is done tampering with his selection of filters.

Take note that all the benchmarks appearing on the main page are quite dated at this point, a lot of code has been added or changed in µBlock. So for version 0.6 I ran the reference benchmark to find out where µBlock stands memory efficiency-wise -- along with ABP 1.8.3 for comparison.

Without a selfie available (one was created during the benchmark):<br>
![Without selfie](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ublock-vs-abp-memory-201409-a.png)

With a selfie available:<br>
![With selfie](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ublock-vs-abp-memory-201409-b.png)

Benchmark details:
- Google Chrome 37 64-bit on Linux Mint.
- µBlock: default filter lists
- ABP: _EasyList_, _EasyPrivacy_, _Malware Domains_. _"Acceptable ads"_ disabled
- Screenshots taken at least 15 minutes after running [reference benchmark](https://github.com/gorhill/uBlock/wiki/Reference-benchmark) and closing all web pages except the _Extensions_ page.