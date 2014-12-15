I've seen a couple of feedbacks in the store of people who wish it was possible to whitelist a web site, i.e. to disable µBlock on a specific web site.

The feature is already available, it is the big power button: it serves to whitelist the current web site, its state will be remembered next time you visit the web site.

![µBlock's popup](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png)

### Detailed syntax

All whitelist directives are matched against the URL address of web pages.

As of version 0.8.2.0, the whitelist directive syntax is split into three classes:
- Plain
- Complex
- Comment

Plain syntax is when using only hostname label(s), which means only the hostname portion of a URL will be taken into account. With plain syntax, the matching is performed by comparing the right-most portion of the page hostname with the whitelist directive. Wildcards are not allowed when using plain syntax.

Complex syntax occurs if and only if at least one `/` appears in a whitelist directive. Optionally, wildcard `*` can be used with complex directives for more flexibility.

A comment is a line prefixed with `#`. Comments are ignored by µBlock.

If no `/` appears in a whitelist directive, and if the directive contains characters which are not allowed for plain hostname, then the whitelist directive will be commented out and ignored by µBlock. This allows you to fix your directive.

#### Plain hostname

- `example.com`: whitelist all pages from `example.com` or above (i.e. `example.com`, `www.example.com`).
- `www.example.org`: whitelist all pages from `www.example.org` or above (i.e. `www.example.org`, `forums.www.example.org`, but not `example.org`).
- `org`: whitelist all pages from TLD `org` (i.e. `example.org`, `wikipedia.org`).

#### Single web page

- `http://www.twitch.tv/letofski`: whitelist only this one page, i.e. when the URL in the address bar **matches exactly** `http://www.twitch.tv/letofski`.

#### Section of a web site

 - `http://www.twitch.tv/letofski*`: whitelist this one page, and everything underneath, i.e. when the URL in the address bar **starts exactly** `http://www.twitch.tv/letofski`.

#### Specific pattern

- `*reddit.com/r/privacy/*`
- `*youtube.com/*&user=jacksfilms*` (assuming you are using [the user script posted here](https://greasyfork.org/en/scripts/4168-youtube-whitelist-channels-in-adblock-plus)).

Wildcards can be used at any position.

### Other details

If you click the whitelist button in µBlock's popup while a whitelist directive you handcrafted is in effect, your handcrafted whitelist directive will simply be commented out, so that you can bring it back to life if ever you un-whitelisted by mistake.