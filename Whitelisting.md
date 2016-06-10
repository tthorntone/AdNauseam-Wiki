### Whitelisting with AdNauseam 

You can permanently whitelist a website by clicking on the 'PAUSE ADNAUSEAM' button in the AdNauseam menu (as shown below). To whitelist only that specific page, you can click on that button with the control key (or command key on a mac) pressed. This decision will be remembered next time you visit the site.

&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![menu](https://raw.githubusercontent.com/dhowe/AdNauseam/gh-pages/img/pause-adnauseam.png)

&nbsp;


#### Detailed syntax

All whitelist directives are matched against the URL address of web pages.

The whitelist directive syntax is split into three classes:

- Plain
- Complex
- Comment

Plain syntax is when using only hostname label(s), which means only the hostname portion of a URL will be taken into account. With plain syntax, the matching is performed by comparing the right-most portion of the page hostname with the whitelist directive. Wildcards are not allowed when using plain syntax.

Complex syntax occurs if and only if at least one / appears in a whitelist directive. Optionally, the wildcard * can be used with complex directives for more flexibility.

A comment is a line prefixed with #. Comments are ignored by uBlock.

If no / appears in a whitelist directive, and if the directive contains characters which are not allowed for a plain hostname, then the whitelist directive will be commented out and ignored by uBlock. This allows you to fix your directive.


#### Plain hostname
- `example.com`: whitelist all pages from `example.com` or above (i.e. `example.com`, `www.example.com`).
- `www.example.org`: whitelist all pages from `www.example.org` or above (i.e. `www.example.org`, `forums.www.example.org`, but not `example.org`).
- `org`: whitelist all pages from TLD `org` (i.e. `example.org`, `wikipedia.org`).

#### Single web page
- `http://www.twitch.tv/letofski`: whitelist only this one page, i.e. when the URL in the address bar **matches exactly** `http://www.twitch.tv/let
ofski`.

#### Section of a web site

 - `http://www.twitch.tv/letofski*`: whitelist this one page, and everything underneath, i.e. when the URL in the address bar **starts exactly** with `http://www.twitch.tv/letofski`.

#### Specific pattern

- `*reddit.com/r/privacy/*`

Wildcards can be used at any position. However, when a wildcard is used within the hostname portion of a directive, it cannot be at the end of the hostname, and also must be at the boundary of a hostname label.

### Other details

If you re-enable AdNauseam by clicking on the 'RESUME ADNAUSEAM' button in the menu after you have whitelisted a page, your handcrafted whitelist directive will simply be commented out. This way you can bring it back to life if ever you un-whitelist by mistake.

&nbsp;

Adapted from https://github.com/gorhill/uBlock/wiki/How-to-whitelist-a-web-site