&nbsp;   

## Frequently Asked Questions for Developers    

* [How do I debug an ad that is appearing on a page?](#how-do-i-debug-an-ad-that-is-appearing-on-a-page)
* [How do I debug a video ad that is appearing on a page?](#how-do-i-debug-a-video-ad-that-is-appearing-on-a-page)
* [How do I debug an image ad that is being hidden, but not found?](#how-do-i-debug-an-image-ad-that-is-being-hidden-but-not-found)
* [How do I debug a text ad that is being hidden, but not found?](#how-do-i-debug-a-text-ad-that-is-being-hidden-but-not-found)
* [What is the difference between JS code in src/js, in src/js/adn, and in platform/chromium, or platform/firefox?]()

&nbsp;     
&nbsp;    

#### How do I debug an ad that is appearing on a page?

First check whether the ad is appearing in uBlock. If it is, then this is not an ADN-specific problem (though we may want to fix it anyway). If the ad _does_ not show in uBlock, then it is likely the case that it is being blocked in uBlock, but not in ADN (remember that we don't want to block ads, only hide them). So then we need to add a cosmetic filter (in AdNauseam filters) to replace the blocking filter that uBlock uses. All devs should learn how to do this (either by using the inspector, or the 'block-element' content-menu):

1.  Select/create the cosmetic rule you want to use to block the ad
1.  Test it by adding it to Options->Dashboard->My Filters->Apply-changes
1.  If its OK, add the rule to the text-file: /AdNauseam/assets/ublock/adnauseam.txt
1.  Remove the rule from Options->Dashboard->My Filters, then click Apply-changes
1.  Rebuild/reload the extension, then click Options->Dashboard->3rd-Party-Filters->Purge-all-caches, then click Apply-changes 
1.  You should now see the # of 'AdNauseam filters' increase to include your new rule
1.  Test by visiting the page in question to verify the ad is now hidden

#### How do I debug a video ad that is appearing on a page?

This process is similar to the [above](#how-do-i-debug-an-ad-that-is-appearing-on-a-page), except that because ADN is not collecting video ads (at least for now), we need to add a block filter (for blocking), rather than a cosmetic filter (for hiding).

#### How do I debug an image-ad that is being hidden, but not found?

In this case, we need to debug the parsing code (/src/js/adn/parser.js) to figure out where it is failing. (pending)

#### How do I debug a text-ad that is being hidden, but not found?

In this case, we need to first determine whether we have a filter for this type of text-ad (these filters are in /src/js/adn/textads.js). If not, we may or may not want to add a filter, depending on how popular a site the text-ads are found on, so simply mark the ticket with this question. If we do, then we need to debug why it is not working correctly. (pending)

