uBlock supports most of [Adblock Plus filter syntax](https://adblockplus.org/en/filter-cheatsheet). However uBlock does not support some very specific case, and also added its own extensions to ABP filter syntax.

### Not supported		

`document`:

Not supported. The purpose of the `document` option is to disable uBlock completely. The reason it is not supported is to be sure that users explicitly disable uBlock themselves if they wish (through [whitelisting](https://github.com/gorhill/uBlock/wiki/How-to-whitelist-a-web-site)), not having some external filter list decide for them.

### Extended syntax

uBlock extends Adblock Plus filter syntax.

#### Network filters

`important`:

The filter option `important` means to ignore all _exception_ filters (those prefixed with `@@`).

It applies only to net _block_ filters. The `important` option will allow you to block with 100% certainty specific net requests.

Example: `||google-analytics.com^$important,third-party` will block all net requests to `google-analytics.com`, disregarding any existing network _exception_ filters. Another example: `||twitter.com^$important,third-party`. Etc.

`inline-script`:

To specifically disable inline script tags in a main page: `||example.com^$inline-script`.

`first-party`:

This is equivalent to `~third-party`. Provided strictly for convenience (0.9.9.0).

#### Cosmetic filters

**Entity-based cosmetic filters:** Filters which are to be applied to a specific _entity_.

An _entity_ is defined as follow: a formal domain name with the Public Suffix part replaced by a wildcard.

Examples: `google.*`  will apply to all similar Google domain names: `google.com`, `google.com.br`, `google.ca`, `google.co.uk`, etc. Another example: `facebook.*` will apply to all similar Facebook domain names: `facebook.com`, `facebook.net`.


Since the base domain name is used to derive the "entity", `google.evil.biz` would **not** match `google.*`.