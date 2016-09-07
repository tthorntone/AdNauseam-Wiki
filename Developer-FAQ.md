## Frequently Asked Questions for Developers  (in progress)

### Getting Started
* [How to build AdNauseam from source?](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers))
* [What is the usual workflow for developers?]()
* [What is the relationship between blocking and hiding rules in uBlock and ADN?]()-pending

* [What is the difference between JS code in src/js, in src/js/adn, and in platform/chromium, or platform/firefox?]()-pending
* [How should I setup my browser profiles for developing?]()-pending
* [How can I get the first-run page to show up when developing?]()-pending

### Common Tasks
* [How do I use the logger, and what are the different types of entries I see?]() pending

* [How do I view the extensions storage entries?]() 
* [How do I debug an ad that is appearing on a page?](#how-do-i-debug-an-ad-that-is-appearing-on-a-page)
* [How do I debug a video ad that is appearing on a page?](#how-do-i-debug-a-video-ad-that-is-appearing-on-a-page)
* [How do I debug an image ad that is being hidden, but not found?](#how-do-i-debug-an-image-ad-that-is-being-hidden-but-not-found)
* [How do I debug a text ad that is being hidden, but not found?](#how-do-i-debug-a-text-ad-that-is-being-hidden-but-not-found)

### Useful References

* [Adblock Plus rule syntax](https://adblockplus.org/filter-cheatsheet)
* [What are Dynamic Filtering Rules?](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-rule-syntax)

&nbsp;     
&nbsp;    

#### What is the usual workflow for developers?

New developers should begin by reading the [FAQ](https://github.com/dhowe/AdNauseam/wiki/FAQ) and [Developer FAQ](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ) and making sure that they can [build the extension](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers) in Chrome, Firefox, or both. They should then start work on a ticket (either by selecting one, perhaps marked with the _Good Volunteer Task_ label, or by being assigned one). It is generally good practice to start a new git branch for the feature/ticket you are working on. Ask questions as you go (in the ticket itself, and/or via email), and when ready, submit a pull-request so that your branch can be merged in.

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

In this case, we need to debug the parsing code (/src/js/adn/parser.js) to figure out where it is failing. You can use the debugger to do this, but it may also be useful to turn on the vAPI.debugAdParsing flag for parsing on whichever platform you are using (either in platform/chromium/vapi-client.js OR platform/firefox/vapi-client.js).

#### How do I debug a text-ad that is being hidden, but not found?

In this case, we need to first determine whether we have a filter for this type of text-ad (these filters are in /src/js/adn/textads.js). If not, we may or may not want to add a filter, depending on how popular a site the text-ads are found on, so simply mark the ticket with this question. If we do, then we need to debug why it is not working correctly. (pending)

#### How should I setup my browser profiles for developing?

It is highly recommended to setup separate browser profiles for development (at very least you should have one for AdNauseam and one for uBlock). This enables you to compare results between AdNAuseam and uBlock, and also to prevent tests being influenced by cookies and other shared state. Remember also to modify your Firefox (development or nightly build) profiles according to [these steps](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers). In Chrome, you can simply enable developer mode.

Chrome

1. Go to chrome://settings/
1. In "People" section, click "Add Person"
1. Choose a picture and give your new profile a name. Ex: AdNauseamDev
1. Click "Add"
1. Now a new chrome window is opened with your new profile

In the same way you can add another profile for uBlock.
To switch among different profiles, right click on the right top corner of chrome browser. You will see a dropdown menu showing all the profiles you have created.

Firefox
(pending)

#### How do I view the extension's storage entries?

Go to chrome://extensions, then open the background.html page, then open the console and enter:

    chrome.storage.local.get(function(result){console.log(result)});
