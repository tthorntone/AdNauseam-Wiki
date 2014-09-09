µBlock is quite memory efficient compared to most other blockers. However, users will often report that this is not the case. I already wrote about this [here](https://github.com/gorhill/uBlock/wiki/Myth:-%C2%B5Block-consumes-over-80MB). I will add more details here, as there is more than garbage collection to factor in. 

When I run my benchmarks, the methodology used is to reproduce what I believe is the most common scenario: a user launches his/her browser with µBlock already fully configured to his/her liking, without further changes to the selection of filter lists. The launch-and-forget scenario. I also benchmark this way for all other blockers.

However there are specific operations which will cause µBlock to churn through lot of short-term memory (let's call this "memory-churning"), and although all that short-term memory is freed by µBlock once the specific operation is completed, not all that freed memory will be garbage-collected by the browser for whatever reasons. Memory fragmentation is possibly a factor.

So in essence you won't obtain the same memory figures which I used in my published benchmarks if you caused µBlock to go through memory-churning before looking at the memory figures.

Reloading all filters causes is quite a memory-churning operation. Here are operations which causes all the filters to be reloaded:

- Launching or restarting µBlock (obviously).
- Changing the selection of filter lists.
- Adding removing custom filters.
- Updating the filter lists.

Additionally, with version 0.6+, µBlock can make selfie to improve its load time next time the browser is launched, and making a selfie is also a memory-churning operation. However for this one particular operation, once the selfie is made, the reward is that subsequent re-launch of µBlock will become very efficient CPU- and memory-wise -- as all the downloading/parsing of filters will be completely bypassed.

Also, take note that all the benchmarks appearing on the main page are quite dated at this point, a lot of code has been added or changed in µBlock. So for version 0.6. I ran the reference benchmark to find out where µBlock stands memory efficiency-wise -- along with ABP 1.8.3 for comparison.

Without a selfie available:<br>
![Without selfie](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ublock-vs-abp-memory-201409-a.png)

With a selfie available:<br>
![With selfie](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ublock-vs-abp-memory-201409-b.png)