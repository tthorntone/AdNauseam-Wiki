Parsing raw filter lists is a CPU and memory intensive task. Adblock Plus-compatible filter syntax is complex, and thus parsing those filters requires a lot of CPU cycles. To add to the parsing complexity, µBlock also supports the parsing of hosts files. Though µBlock could parse filter lists at a satisfying speed, this doesn't mean trying to improve performance in that area should not be attempted.

So this is what has been done in 0.8.9.0. The idea is rather simple: create a compiled version of a filter list, so that next time it needs to be loaded in memory, all the costly parts of the parsing operation has been done already:

![Figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/setup-performance-internals.png)

The compiled version of a filter list is contains very deterministic content, such that no complicated parsing is required. This improves launch time performance (smaller is better):

![Figure 2](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/setup-performance-0.8.9.0.png)

And this also improve the performance when filter lists have to be reloaded:

![Figure 3](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/filters-load-performance-0.8.9.0.png)

A compile filter lists is made of a sequence of _atomic_ filter, i.e. a filter which is not composite. ABP-compatible filter syntax allows the creation of composite filters, i.e. filter declarations which really represents many filters. For example:

    