Back to [Static filter syntax](https://github.com/gorhill/uBlock/wiki/Static-filter-syntax).

***

- [Caveats](#caveats)
- [Overview](#overview)
- [Compatibility with Adblock Plus](#compatibility-with-adblock-plus)
- [Concrete examples of usefulness](#concrete-examples-of-usefulness)
- [Why is the new inline script tag filter a cosmetic one?](#why-is-the-new-inline-script-tag-filter-a-cosmetic-one)

***

#### Caveats

Script tag filters do not work in all browsers, due to browser API limitations:

- Not supported in Chromium-based browser.
    - Starring the [related Chromium issue](https://code.google.com/p/chromium/issues/detail?id=168175) may help motivate Chromium devs to implement support.
- Not supported on older versions of Firefox.

***

#### Overview

There are many ways to block script tags from executing in uBlock Origin:

- Block external script resources: these are taken care by network filtering.
- Block all inline script tags embedded in a page at once.<sup>[1]</sup>

Inline script tags are those blocks of javascript code which are embedded in the main page: they can not be blocked from downloading unless the whole page itself is blocked, which is not very useful. Here is a example of a web page's HTML code with two inline script tags:

```html
<html>
<head>
<meta name="referrer" content="origin">
<link rel="stylesheet" href="main.css" />
<script type="text/javascript">
    function usefulCode() {
        ...
    }
    ...
</script>
<title>lorem ipsum</title>
</head>
<body>
<h1>lorem ipsum</h1>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
<script type="text/javascript">
    function nuisanceCode() {
        ...
    }
    ...
</script>
</body>
```

In this example, blocking inline script tags wholesale would not be a good solution because both script tags would be blocked and we would lose the `usefulCode` function as well.

uBlock Origin 1.2.0 introduces a new way to block **specific** inline script tag in a web page through the script tag cosmetic filter:

    example.com##script:contains(...)

Where the value inside the parenthesis in `contains(...)` can be a plain string or a literal javascript regular expression (`/.../`). A script tag cosmetic filter will prevent the execution of whatever javascript inside a **specific** script tag when there is a match, i.e. when the plain text or the regular expression is found inside the script tag.

So we can use script tag filtering for our above example to specifically disable one of the script tag (assuming the page's URL is `https://foo.example/bar.html`):

    foo.example##script:contains(nuisanceCode)

This filter means: for any web pages from the `foo.example` web site, disable all inline script tags which contains the string `nuisanceCode`.

In the cat and mouse game between web sites and blockers, the new script tag filter is a welcomed new tool on the user side, to foil attempt by site to work around blockers.

The big advantage of this new filter is that it can fix _at the source_ many of the anti-blocker workarounds used by some web sites.

For example, the web site at `http://focus.de/` will resort to deface itself with ridiculous ads when the site detects that the user is using a blocker, and using _EasyList_ + _EasyList Germany_ does not work, as the images pulled by the page are randomly named, defeating pattern-based network filters and cosmetic filters as well.

Wholesale blocking of inline script tags does prevent the self-defacing, but possibly at the cost of disabling other possible useful functionalities on the page. However, a script tag filter to block the specific inline script tag which contains the self-defacement javascript code allows a more targeted approach: prevent the undesirable inline javascript code from executing while keeping the desirable inline javascript code intact. At time of writing, this script tag filter worked for the site:

    www.focus.de##script:contains(uabInject)

#### Compatibility with Adblock Plus

It appears inline script tag cosmetic filters can be used in filter lists which are also meant to be used for Adblock Plus ("ABP") -- ABP will ignore the `[...]##script:contains([...])` filters. This makes it possible for maintainers of filter lists to make use of this new filter syntax for the benefit of uBlock Origin users while not causing problem for users of ABP.

The compatibility was verified for the Firefox version of ABP however, I did not check for the Chromium version of ABP. This will need confirmation for whether using the new filter on a Chromium version of ABP has no negative consequences.

#### Concrete examples of usefulness

Try without, then with the respective inline script tag filter:

- <http://dayt.se/forum/activity.php>: `dayt.se##script:contains(adBlockDetected)` (see ["Blocking FuckAdblock"](https://adblockplus.org/forum/viewtopic.php?f=2&t=40895))
- <http://explosm.net/comics/1525/>: `explosm.net##script:contains(/^__durl=/)`
- <http://www.focus.de/>: `focus.de.de##script:contains(uabInject)`
- <http://www.rp-online.de/>: `rp-online.de##script:contains(uabInject)`
- <http://arstechnica.com/>: `arstechnica.com##script:contains(ars.READY.push)`

#### Why is the new inline script tag filter a cosmetic one?

Because blocking inline script tags is conceptually closer to cosmetic filtering than network filtering: inline script tags are embedded in a web page, so if the web page is downloaded, the inline script tags are downloaded -- there is no way around this.

Whatever can't be blocked using a network request filter can be taken care by a cosmetic filter, which is the removal of DOM elements from a web page. Hence inline script tag filtering is implemented using the cosmetic filter syntax -- the only difference is that when blocked, inline script tags are not removed from view (they are already invisible) but instead the execution of the javascript code inside the script tag is blocked.

#### When to use a script tag filter?

...

#### How to craft a good script tag filter?

...

- [1] Through the use of the `inline-script` static filter option (`||example.com^$inline-script`), or through the use of a dynamic filtering block rule for _inline scripts_.