<p align="center"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-6.png" /><br><sup>Inline script tags blocked for the current site only.</sup></p>

### Example 1

URL: <http://www.wetteronline.de/wetter>

Ads embedded in the page using `data:` URIs as `background-image` CSS style on a randomly generated identifier ([source](https://adblockplus.org/forum/viewtopic.php?f=2&t=25452)). I don't see how Adblock Plus filters can take care of this one.

But disabling **inline `<script>` tags** on this site got rid of the ads, probably because the random identifier is generated using inline script tags. Other maybe useful stuff appear to have disappeared to, but a user may decide this is an acceptable side-effect.

### Example 2

URL: <http://www.vox.com/>

If you are using a blocker with _EasyPrivacy_, the above site, bent of having a 3rd-party track your activity on the site, will have all its hyperlinks disabled. Click on a link and nothing happens.

Disabling inline `script` tags will restore hyperlink functionality, though at the cost of the site layout being somewhat untidy. To some users, this workaround is more acceptable than having to completely disable µBlock.