Keep in mind that this feature is to prevent leakage of your non-internet-facing IP adresses. The purpose of this feature is not to hide your current internet-facing IP address -- so be cautious to not misinterpret the results of some WebRTC-local-IP-address-leakage tests found online.

For example, if you use a VPN, your internet-facing IP address is that of the VPN, so your ISP-provided IP address should not be visible to outside world with this setting checked. However, if you are not behind any VPN or proxy, your ISP-provided IP address will be visible regardless of this setting.

Test: [Trickle ICE](https://webrtc.github.io/samples/src/content/peerconnection/trickle-ice/) (click the <kbd>Gather candidates</kbd> button at the bottom).

#### Caveats

##### Chromium-based browsers

It has been reported that Google Hangout and Facebook messenger do not work properly when this setting is enabled (issue [#757](https://github.com/gorhill/uBlock/issues/757), [#681](https://github.com/gorhill/uBlock/issues/681)).

If you are using an extension-based VPN, this setting won't [prevent your ISP IP address from leaking](https://code.google.com/p/chromium/issues/detail?id=457492#c44).

Also: ["When using a proxy, WebRTC leaks unproxied IP address even with multiple routes disabled"](https://code.google.com/p/chromium/issues/detail?id=497040).

The feature works only on version 42 and above.

##### Firefox

With Firefox, it's not possible to prevent local IP addresses leakage without completely disabling WebRTC -- this is what uBlock Origin does.

WebRTC is required for Firefox Hello to work properly. Thus Firefox Hello won't work if you enable this setting.

#### See also

- [WebRTC WG / Privacy/IPAddresses](https://www.w3.org/wiki/Privacy/IPAddresses)