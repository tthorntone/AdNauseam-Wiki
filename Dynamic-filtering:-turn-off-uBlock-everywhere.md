[Back to "Dynamic-filtering"](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)

***

The ability to turned off uBlock everywhere has been requested many times: [#40](https://github.com/gorhill/uBlock/issues/40), [#403](https://github.com/gorhill/uBlock/issues/403).

I wasn't really planning to provide this functionality as I fail to see why it should be implemented in uBlock when the browsers themselves offer this ability through the disabling of extensions.

In any case, the ability to "disable" uBlock everywhere is now available, as a side effect of the ability to create a global `allow` rule for all network requests:

![Allow everything everwhere](https://cloud.githubusercontent.com/assets/585534/6097114/04368716-af7e-11e4-8ca8-49ffdaa49fa6.png)

Though it's more _"allow everything from everywhere"_, it's as good as _"globally turn off uBlock"_.