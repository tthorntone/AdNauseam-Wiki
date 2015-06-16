[Adblock Plus filter syntax](https://adblockplus.org/en/filters) allows for the use of [regular expression as filters](https://adblockplus.org/en/filters#regexps).

It is not recommended to use regex-based filters, hence why I chose for a long time to not support these in uBlock: to prevent users who write their own filters from acquiring the bad habit of using regular expressions to filter network requests.

However this led to the often-repeated myth that the reason uBlock was efficient memory- and CPU-wise was because it did not support regex-based filters, a completely nonsensical assertion, given that there is a grand total of only 15 such filters in all of _EasyList_ (at time of writing) out of tens of thousands.

It is because of this myth that I finally decided to support regex-based filters with version 0.8.6.0:

![regex-based filter at work](https://cloud.githubusercontent.com/assets/585534/5883114/606b7838-a31d-11e4-98e5-1e9ea47e3308.png)

Given the way uBlock works internally, the regex-based filters are implemented in a more efficient way than other big-name blockers.

An efficient regex-based filter is one which does not need to be evaluated.

So if you decide to write a regex-based filter, here is the trick to help you make your regex as efficient as possible:

**Use filter options to reduce the likelihood of a regex-based filter of being executed.**

A most-efficient regex-based filter is one which comes with all the following filter options set:

1. type: a filter which apply only to a specific request type will be executed only for request which matches the type.
    - Example: `/\.filenuke\.com/.*\/[a-zA-Z0-9]{4}/$script` will be executed only for request of type `script` (this filter is found in _EasyList_)
1. `domain=`: The regular expression won't be executed if the hostname of a request does not match the hostnames declared in the `domain` filter option
1. `third-party`: the regular expression won't be executed if the request does not fulfill the `third-party` option (or it's complement `~third-party`)

An example of a regex-based filter found in _EasyList_ which is handled very efficiently by uBlock:

    /http:.*(?:\+|\@|\=|\;|\_|\-|\!|\?|\&|\%|\#|\^|\:).*\/\//$script,third-party,domain=allenbwest.com

This filter contains all the filter options which makes it very unlikely that the regular expression will have to be executed. The regular expression will execute **only** if the request is of type `script`, originates from `allenbwest.com`, and is 3rd-party to `allenbwest.com`.

If this sounds like basic common sense, it's because it is. However I've seen other big-name blockers out there execute all regex-based filters unconditionally for every request. (**Edit:** [fixed in ABP](https://issues.adblockplus.org/ticket/2177))