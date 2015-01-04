### Rule syntax

A dynamic filtering rule is made of four components: a source hostname, a destination hostname, a request type, and then a keyword which tells what to do with a request which happens to match the three former components.

    source-hostname destination-hostname request-type action

Source hostname always correspond to the hostname extracted from the URL of the web page in the browser. The destination hostname correspond to the hostname extracted from the URL of a remote resource which the web page is fetching (or trying to). The type is the type of the fetched resource. A request can be blocked, allowed, or ignored.

### Type-based rules

Type-based rules are used to filter specific types of request on a web page. There currently exists five types of request which can be dynamically filtered:

- `image`: images
- `inline-script`: inline script tags, i.e. scripts embedded in the main document
- `1p-script`: 1st-party scripts, i.e. scripts which are pulled from the same domain name of the current web page
- `3p-script`: 3rd-party scripts, i.e. scripts which are pulled from a different domain name than that of the current web page
- `3p-frame`: 3rd-party frames, i.e. frames elements which are pulled from a different domain name than that of current web page

These rules can apply everywhere, or be specific to a web site. For instance blocking 3rd-party frames is a very good habit security-wise: `* * 3p-frame block`. This rule translates into "block 3rd-party frames of all origins".

Another example: `wired.com * image block`, which means "block images from all origins when visiting a web page on wired.com".

Note that with type-based rules, the destination hostname is **always** `*`, meaning "from anywhere".

### Hostname-based rules

Hostname-based rules are used to filter network resources according to their origin, i.e. according to which remote server a resource is pulled. Hostname-based rules have a higher specificity than type-based rules, and thus hostname-based rules always override type-based rules whenever a network request end up matching both a type- and a hostname-based rule.

With hostname-based rule, the type is always `*`, meaning the rule will apply to any type of request.

For example, `* disqus.com * block` means "globally block all net requests to `disqus.com`".

Just like type-based rules, a hostname-based rule can apply only when visiting a specific web site, for example: `wired.com disqus.com * noop`, which means "do not apply dynamic filtering to net requests to `disqus.com` when visiting a web page on `wired.com`. Since this last rule is more specific than the previous one, it will override the global blocking of `disqus.com` everywhere.

### Actions

A matching rule can do one of three things:

- `block`: matching net request will be blocked.
    - `block` dynamic filter rules override any existing [static exception filters](https://adblockplus.org/en/filters#whitelist).
    - Thus you can use them to block with 100% certainty (unless you set another overriding dynamic filter rule).
- `allow`: matching net request will be allowed.
    - `allow` dynamic filters rules override any existing static and dynamic block filters.
- `noop`: prevent matching net requests from being subjected to dynamic filtering.
