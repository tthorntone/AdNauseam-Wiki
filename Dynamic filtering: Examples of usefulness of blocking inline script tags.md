### Example 1

URL: <http://www.wetteronline.de/wetter>

Ads embedded in the page using `data:` URIs as `background-image` CSS style on a randomly generated identifier ([source](https://adblockplus.org/forum/viewtopic.php?f=2&t=25452)). I don't see how Adblock Plus filters can take care of this one.

But disabling **inline `<script>` tags** on this site got rid of the ads, probably because the random identifier is generated using inline script tags. Other maybe useful stuff appear to have disappeared to, but a user may decide this is an acceptable side-effect.