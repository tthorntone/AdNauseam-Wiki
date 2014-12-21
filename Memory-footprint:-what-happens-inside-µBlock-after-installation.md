1. µBlock will load the default selection of filter lists:
    - This causes short-term memory churning (loading/parsing/sorting/storing), which short-term memory will be garbage-collected eventually
    - All this short term memory churning causes µBlock's baseline memory footprint to grow further
1. After **five minutes**, µBlock will look whether one or more filter lists need to be updated
1. If an update is needed, µBlock will flush from memory all filters and reload with the latest version
    - This will causes another round of short-term memory churning, which short-term memory will be garbage-collected eventually
    - Again, all this short term memory churning causes µBlock's baseline memory footprint to grow further
1. After **seven minutes**, assuming no change in selection of filter lists, or change in the content of selected filter lists, µBlock will make a selfie
    - A selfie allows µBlock to skip the parsing/sorting of data next time it loads
    - Generating the selfie also causes short-term memory churning, which short-term memory will be garbage-collected eventually
    - Again, this short term memory churning causes µBlock's baseline memory footprint to grow further
    - Any change in the selection of filter lists, or change in the content of selected filter lists will invalidate µBlock's selfie
1. Even after the growth in memory baseline, µBlock's own memory footprint is still quite smaller than that of Adblock Plus -- once the garbage collector does its job.
1. µBlock's much smaller contributed memory footprint to web pages is much smaller than that of ABP
    - The contributed footprint to web pages is part of the memory footprint of the web pages themselves 
    - As opposed to an extension's own memory footprint, visible using Chromium's _"Task Manager"_, the contributed memory footprint to web pages cannot be easily seen by users
    - Though this measure is not readily visible, it's where you get the biggest bang for the buck with µBlock relative to ABP -- because µBlock **does not** inject thousands of CSS rules into pages and embedded frames.

Now if you have reach the point where there is a valid µBlock selfie, this is when µBlock will run the most efficiently.

The next time you launch µBlock and there is a valid selfie, the load time will be a fraction of the load time when no selfie is available, and µBlock's baseline memory footprint will be noticeably smaller then when µBlock launches without a selfie available.

So my point is that µBlock will perform best efficiency wise if you leave it time to optimize itself after installation: In subsequent launches, µBlock will perform noticeable more efficiently than what you may have observed right after you installed it.

***

Related: ["Notes on memory benchmarks, selfies"](https://github.com/gorhill/uBlock/wiki/Notes-on-memory-benchmarks,-selfies)
Be aware: ["Popup UI of extensions causes systematic memory leaks"](https://code.google.com/p/chromium/issues/detail?id=441500)