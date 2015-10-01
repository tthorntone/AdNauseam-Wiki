There are many ways to block script tags from executing in uBlock Origin:

- Block external script resources.
- Block all inline script tags embedded in a page at once.<sup>[1]</sup>

Inline script tags are those scripts which are embedded in the main page: they can not be blocked from downloading unless the whole page itself is blocked, which is not very useful. Here is a example of HTML code with two inline script tags:

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

The big advantage of this new filter is that it can fix many of the anti-blocker workarounds web sites use at the _source_.

For example, the web site at `http://focus.de/` will resort to deface itself with ridiculous ads when the site detects that the user is using a blocker, and using _EasyList_ + _EasyList Germany_ does not work. Wholesale blocking of inline scripts does prevent the auto-defacing, but possibly at the cost of using useful functionalities. However, a script tag filter to block the specific inline script tag which contains the self-defacement javascript code allows a more targeted approach: prevent the undesirable inlibe javascript code from executing while keeping the desirable inline javascript code intact. At time of writing, this script tag filter worked for that site:

    www.focus.de##script:contains(uabInject)

#### Why is the new script tag filter a cosmetic one?

...

#### When to use a script tag filter?

...

#### How to craft a good script tag filter?

...

#### Caveats

Script tag filters do not work in all browsers, due to browser API limitations:

- Not supported in Chromium-based browser.
- Not supported on older version of Firefox.

***

- [1] Through the use of the `inline-script` static filter option (`||example.com^$inline-script`), or through the use of a dynamic filtering block rule for _inline scripts_.