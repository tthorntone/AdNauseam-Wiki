uBlock Origin ("uBO") supports Adblock Plus ("ABP") filter syntax, so you can refer to [existing filter syntax documentation from Adblock Plus web site](https://adblockplus.org/en/filter-cheatsheet).

However uBO does not support some very specific cases, and also adds its own extensions to ABP filter syntax (which at time of writing are not recognized by ABP).

### Not supported		

`document` for _exception_ filters (those prefixed with `@@`):

Not supported. The purpose of the `document` option when used with an exception filter is to disable uBO completely. The purpose of the `document` option in static exception filters is mostly for the sake of "acceptable ads" support, which uBO does not support.

The reason it is not supported is to be sure that users explicitly disable uBO themselves if they wish (through [whitelisting](https://github.com/gorhill/uBlock/wiki/How-to-whitelist-a-web-site)), not having some external filter list decide for them.

### Extended syntax

uBO extends Adblock Plus filter syntax.

#### Network filters

##### HOSTS files

uBO can also parse HOSTS file-like resources. However, this creates an ambiguity with ABP filter syntax, which is pattern-based. For exemple, consider the following filter entry:

    example.com

ABP filter syntax dictates that this is interpreted as "block network requests which URL contains `example.com` at any position". However if the entry comes from a HOSTS file, the interpretation must be "block network requests to the site `example.com`".

So in uBO, any entry which can be read as a valid hostname, will be assumed to be a HOSTS file entry. If ever you want such filter to be parsed as an ABP filter, just add a wildcard at the end:

    example.com*

##### "All URLs"

The wildcard character `*` can be used to apply a filter to **all** URLs. This is not recommended though, unless you further narrow the filter using filter options. Examples:

- `*$third-party`: block all 3rd-party network requests.
- `*$script,domain=example.com`: block all network requests to fetch script resources from `example.com`.

Usually, it is far more convenient to use [dynamic filtering rules](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering) in lieu of such generic static filters.

##### Network filters options

`document` for _block_ filters:

This will cause web pages which match the filter to be subjected to [strict blocking](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#no-strict-blocking).

`first-party`:

This is equivalent to `~third-party`. Provided strictly for convenience (0.9.9.0).

`important`:

The filter option `important` means to ignore all _exception_ filters (those prefixed with `@@`).

It applies only to network _block_ filters. The `important` option will allow you to block with 100% certainty specific network requests.

Example: `||google-analytics.com^$important,third-party` will block all network requests to `google-analytics.com`, disregarding any existing network _exception_ filters. Another example: `||twitter.com^$important,third-party`. Etc.

`inline-script`:

To specifically disable inline script tags in a main page: `||example.com^$inline-script`.

`popunder`:

To block "popunders" windows/tabs. To be used in the same manner as the `popup` filter option, except that it will block popunders.

`redirect`:

To cause a blocked network request to be redirect to a local "neutered" version of the resource. (more documentation will eventually be made.)

#### Cosmetic filters

**Entity-based cosmetic filters:** Filters which are to be applied to a specific _entity_:

    google.*###tads.c

An _entity_ is defined as follow: a formal domain name with the Public Suffix part replaced by a wildcard.

Examples: `google.*`  will apply to all similar Google domain names: `google.com`, `google.com.br`, `google.ca`, `google.co.uk`, etc. Another example: `facebook.*` will apply to all similar Facebook domain names: `facebook.com`, `facebook.net`.

Since the base domain name is used to derive the name of the "entity", `google.evil.biz` would **not** match `google.*`.

##### Special cosmetic filters

`script:contains(...)`:

uBO supports a special cosmetic filter which purpose is to prevent the execution of specific inline script tags in a main HTML document. See [_"Inline script tag filtering"_](https://github.com/gorhill/uBlock/wiki/Inline-script-tag-filtering) for further documentation.

`script:inject(...)`:

This allows the injection of specific javascript code into pages. The `...` part is a token identifying a javascript resource from the [resource library](https://github.com/gorhill/uBlock/blob/master/assets/ublock/resources.txt). Keep in mind the resource library is completely under control of the uBO project, hence only javascript code vouched by uBO can be inserted into web pages, through the use of a valid resource token.

Generic `script:inject` filters are ignored: those filters **must** be specific, i.e. they must apply to specific hostnames, e.g. `example.com##script:inject(yavli-defuser.js)`.