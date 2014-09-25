µBlock supports most of [Adblock Plus filter syntax](https://adblockplus.org/en/filter-cheatsheet). However µBlock does not support some very specific case, and also added its own extensions to ABP filter syntax.

### Not supported

**Regular expression-based filters:** may add according to demand, but if ever I add support for regex-based filters, I will support only for regexes which can be tokenized, or which are specific to a hostname, i.e. regexes which can be implemented in an efficient way.

### Extended syntax

µBlock extends Adblock Plus filter syntax.

#### Network filters
**The `important` network filter option:** The important filter option, `important`, means to ignore all _exception_ filters (those prefixed with `@@`). It applies only to net _block_ filters. The `important` option will allow you to block with 100% certainty specific net requests. Example: `||google-analytics.com^$important,third-party` will block all net requests to `google-analytics.com`, disregarding any existing network _exception_ filters. Another example: `||twitter.com^$important,third-party`. Etc.

**The `inline-script` network filter option:** To specifically disable inline script tags in a main 
page: `||example.com^$inline-script`.

#### Cosmetic filters

**Entity-based cosmetic filters:** Filters which are to be applied to a specific _entity_. An _entity_ is defined as follow: a formal domain name with the Public Suffix part replaced by a wildcard. Examples: `google.*`  will apply to all similar Google domain names: `google.com`, `google.com.br`, `google.ca`, `google.co.uk`, etc. Another example: `facebook.*` will apply to all similar Facebook domain names: `facebook.com`, `facebook.net`.
