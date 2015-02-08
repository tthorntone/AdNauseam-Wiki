Default-deny is an awesome blocking mode for whoever is ready for the task of having to un-break web sites during the first visit, and agrees that in general most 3rd-party resources from web pages:

- are not really _all_ required
- increase privacy exposure

![Default-deny](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-dd-01.png)<br>
<sup>Default-deny engaged, through the default blocking of 3rd-party network requests.</sup>

The benefits of using default-deny are plenty:

- Faster page load
- Reduction of bandwidth consumption
- Reduction of privacy exposure
- Increase browser security
- Easier on your browser's memory and CPU footprint

The advantages do not come for free. Often, default-deny will require a bit of work the first time you visit a web site. Using [The Guardian](http://www.theguardian.com/) as our current example:

![Default-deny](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-dd-03.png)

As seen in the picture above, a few 3rd-party domains related to `theguardian.com` had to be un-blocked for the page to display and behave properly. Notice that `noop` rules (dark gray) were used to un-block the domains.

A `noop` rule is different than an `allow` rule (green): an `allow` rule will cause all block filters from static filtering to be bypassed, while a `noop` rule will just disengage dynamic filtering and keep static filtering engaged.

Keep in mind that all rules are permanent as soon as they are set (or unset).

You can disengage default-deny for the current site with one click: set the "3rd-party" local setting to `noop` if you prefer to work this way:

![Default-deny](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-dd-02.png)<br>
<sup>Default-deny cancelled locally. Notice that the blocking of 3rd-party frames is still in effect: cells with higher precedence won't have their rules overriden by cell with lower precedence.</sup>

This results in default-deny being disengaged for the current site (`theguardian.com` in the picture), **while** keeping engaged static filtering (_EasyList, _EasyPrivacy_, etc.)

> working on it.. topic to cover:
> 
> no need to use malware domain lists since all 3rd-parties are blocked by default = leaner uBlock
>
> ubiquitous servers blocked by default, i.e. no need to pre-emptively block facebook, google, twitter, linkdin, etc. to prevent tracking by these
>
> provide many real-life examples of how easy it is to un-break websites