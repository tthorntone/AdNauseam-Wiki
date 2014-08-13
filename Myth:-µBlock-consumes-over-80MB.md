I've seen a couple of instances of people claiming µBlock is not as memory efficient as claimed. Examples:

- ["I just installed it, and it uses 117MB - that's not even close"](http://www.reddit.com/r/chrome/comments/2cpogs/fast_and_light_ad_blocker_for_chrome_%C2%B5block/cjhutwz)
- ["Simply tried, did not see where the province of memory" (Google translate...)](http://bbs.kafan.cn/thread-1762885-1-1.html#pid32323303)

When µBlock launches, it loads all selected filter lists, parse the content, eliminate duplicates, than instantiates the filters using efficient internal representation. This parsing of the filter lists requires a good amount of temporary memory.

So if you look at the task manager **right after** µBlock has loaded and parsed the filters, you will still see µBlock's memory footprint as a result of loading all the filter lists. Still, at the this point all this temporary has been relinquished to the browser, but the browser hasn't yet claimed the freed memory to make it available for reuse.

If the browser is idle enough, before one minute has elapsed, the browser should be able to [garbage collect](http://en.wikipedia.org/wiki/Garbage_collection_(computer_science)) the temporary memory which was freed by µBlock after it finished loading and parsing the filter lists:

![µBlock's memory footprint](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/mem-footprint-at-launch-time.png)

The top image shows the memory footprint of µBlock right after launch. The image at the bottom shows the memory footprint of µBlock before one minute has elapsed while the browser is idle.

Note that once µBlock's baseline memory footprint won't change that much afterward. It will likely settles a few MB above the memory footprint reached after garbage collection has occurred.