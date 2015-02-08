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

[...]

You can disengage default-deny for the current site with one click: set the local "3rd-party" cell to `noop`:

![Default-deny](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-dd-02.png)<br>
<sup>Default-deny engaged, through the default blocking of 3rd-party network requests.</sup>

This results in default-deny being disengaged for the current site (`theguardian.com` in the picture), **while** keeping engaged static filtering (_EasyList, _EasyPrivacy_, etc.)

> working on it.. topic to cover:
> 
> no need to use malware domain lists since all 3rd-parties are blocked by default = leaner uBlock
>
> ubiquitous servers blocked by default, i.e. no need to pre-emptively block facebook, google, twitter, linkdin, etc. to prevent tracking by these
>
> provide many real-life examples of how easy it is to un-break websites, including worst case scenario of simply setting the `3rd-party` cell to `noop` to completely disengage default-deny for one specific web site, if it gets too complicated
