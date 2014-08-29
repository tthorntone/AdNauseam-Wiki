I consider version 0.4.0.0 to be an important milestone for µBlock, hence the jump from 0.3.2.3 to 0.4.0.0.

Contrary to Adblock Plus, µBlock does **not** inject **all** the generic cosmetic filters into each page and each embedded frames on a page, and this is why pages load faster with µBlock, and this is why the memory footprint of the web pages themselves is significantly smaller with µBlock than with Adblock Plus.

To be able to inject only the cosmetic filters which are relevant to a web page (rather than all of them), µBlock waits for the primary DOM to be available, then survey and collect information on the page to find out which cosmetic filters need to be injected in the page.

The result is significant gain in memory and page load efficiency. This gain in memory and CPU efficiency translates directly in more freedom for the user to enable more filter lists without severely crippling the browser speed, and without causing less powerful devices to become unusable (example: ["Acer C720 running slow"](http://www.reddit.com/r/chromeos/comments/2d60ed/acer_c720_running_slow/cjmkbgy)).

However the inconvenience is that the HTML elements which need to be hidden from view through cosmetic filtering may appear briefly before disappearing, because the generic cosmetic filters which have been picked as a result of the survey may take effect after the page displays.

One solution to mitigate this was to introduce a while ago the concept of entity-based cosmetic filters. This new class of cosmetic filters allows µBlock to inject such cosmetic filters without having to wait for the primary DOM to be available, hence the HTML elements which are targeted will be hidden early enough, before the page displays.

So far only the generic filters which purpose is to hide ads on Google search page have benefited from that new class of cosmetic filters. This was a best-case scenario for such cosmetic filters, because ads for the Google search page must be hidden on `google.com`, `google.ca`, `google.com.br`, etc. For example, there exist entity-based filters for `google.*`, which means they will be injected in any of the Google domain. Not being able to use a wildcard as suffix for hostnames in cosmetic filters is why Adblock Plus is forced to use generic cosmetic filters for those filters which purpose is to remove ads from Google search web page.

Still, entity-based filters are not a solution for the vast majority of generic cosmetic filters (14,000+ generic cosmetic filters just in _EasyList_).

Version 0.4.0.0 introduces a cache mechanism for cosmetic filters. All generic filters which are picked as relevant will be remembered the first time they are encountered, and injected early in subsequent visits of pages with the same hostname. This brings µBlock much closer to ABP by the way web page behaves, while preserving the highly efficient approach of injecting only a handful of generic cosmetic filters on a web page.

Benchmarking heavy sites (such as `si.com` which I use as a reference benchmark for development purpose to find performance hot spots in the cosmetic filtering code) ~~suggests~~ I confirm that with version 0.4.0.0, web page will load even more efficiently than before ([changes in version 0.3.2.2](https://github.com/gorhill/uBlock/releases/tag/0.3.2.2) also probably contribute to this), despite the added overhead of caching. This caching mechanism will increase the memory footprint of µBlock, but only marginally from what I've seen.

This is the result of profiling `www.si.com` -- page loaded 10 times, hence timing values must be divided by ten to obtain per-page timings:

##### µBlock 0.3.0.0:

![µBlock 0.3.0.0](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/profiling-cosmetic-filters-v0.3.png)

##### µBlock 0.4.0.0:

![µBlock 0.4.0.0](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/profiling-cosmetic-filters-v0.4.png)

While at it, I decided to make use of this caching mechanism to also take care of hiding HTML elements linked to blocked net requests, such that elements which are destined to have their net request blocked will be hidden even before their net request is fired in the browser.