### Whitelisting sites with AdNauseam 

You can use the 'pause-adnauseam' button in the AdNauseam menu to whitelist a page or a site (as shown below). Its state will be remembered next time you visit the web site.

![menu](https://raw.githubusercontent.com/dhowe/AdNauseam/gh-pages/img/pause-adnauseam.png)

#### Detailed syntax

All whitelist directives are matched against the URL address of web pages.

The whitelist directive syntax is split into three classes:

-Plain
-Complex
-Comment

Plain syntax is when using only hostname label(s), which means only the hostname portion of a URL will be taken into account. With plain syntax, the matching is performed by comparing the right-most portion of the page hostname with the whitelist directive. Wildcards are not allowed when using plain syntax.

Complex syntax occurs if and only if at least one / appears in a whitelist directive. Optionally, the wildcard * can be used with complex directives for more flexibility.

A comment is a line prefixed with #. Comments are ignored by uBlock.

If no / appears in a whitelist directive, and if the directive contains characters which are not allowed for a plain hostname, then the whitelist directive will be commented out and ignored by uBlock. This allows you to fix your directive.

Adapted from https://github.com/gorhill/uBlock/wiki/How-to-whitelist-a-web-site