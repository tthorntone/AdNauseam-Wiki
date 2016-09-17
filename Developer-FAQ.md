## Frequently Asked Questions for Developers  (in progress)

### Getting Started
* [How to build AdNauseam from source?](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers))
* [What is the usual workflow for developers?](#what-is-the-usual-workflow-for-developers)
* [What is the relationship between blocking and hiding rules in uBlock and ADN?](#what-is-the-relationship-between-blocking-and-hiding-rules-in-ublock-and-adn)
* [What is the difference between JS code in src and in platform?](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#what-is-the-difference-between-js-code-in-src-and-in-platform)
* [How should I setup my browser profiles for developing?](#how-should-i-setup-my-browser-profiles-for-developing)
* [How can I get the first-run page to show up when developing?](#how-can-i-get-the-first-run-page-to-show-up-when-developing)

### Common Tasks
* [How do I view extension messages in the console?](#How-do-I-view-extension-messages-in-the-console)
* [How do I run the browser's debugger on different parts of the extension?](#)
* [How do I use the logger, and what are the different types of entries it shows?](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#how-do-i-use-the-logger-and-what-are-the-different-types-of-entries-it-shows)
* [How do I debug an ad that is appearing on a page?](#how-do-i-debug-an-ad-that-is-appearing-on-a-page)
* [How do I debug a video ad that is appearing on a page?](#how-do-i-debug-a-video-ad-that-is-appearing-on-a-page)
* [How do I debug an image ad that is being hidden, but not found?](#how-do-i-debug-an-image-ad-that-is-being-hidden-but-not-found)
* [How do I debug a text ad that is being hidden, but not found?](#how-do-i-debug-a-text-ad-that-is-being-hidden-but-not-found)
* [How do I view the extensions storage entries?](#how-do-i-view-the-extensions-storage-entries)
* [How are locales/languages/translations handled?](https://github.com/dhowe/AdNauseam/wiki/Handling-languages,-locales,-and-translations)

### Useful References

* [The git fork-and-branch workflow](http://blog.scottlowe.org/2015/01/27/using-fork-branch-git-workflow/)
* [Adblock Plus rule syntax](https://adblockplus.org/filter-cheatsheet)
* [What are Dynamic Filtering Rules?](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-rule-syntax)
* [What is uDom?](#what-is-udom)

&nbsp;     
&nbsp;    

#### What is the usual workflow for developers?

New developers should begin by reading the [FAQ](https://github.com/dhowe/AdNauseam/wiki/FAQ) and [Developer FAQ](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ) and making sure that they can [build the extension](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers) in Chrome, Firefox, or both. They should then start work on a ticket (either by selecting one, perhaps marked with the _Good Volunteer Task_ label, or by being assigned one). It is generally good practice to start a new git branch for the feature/ticket you are working on. Ask questions as you go (in the ticket itself, and/or via email), and when ready, submit a pull-request so that your branch can be merged in.

If multiple tickets are assigned to you, work on the one with highest priority, unless otherwise specified.

Sometimes you may be assigned a ticket with the label _Needs-verification_. In such cases, you should simply verify that the fix works as expected. If so, then the ticket can usually be closed. If not, document as specifically as possible how/why the fix fails.

The project uses the git fork-and-branch workflow, described nicely [here](http://blog.scottlowe.org/2015/01/27/using-fork-branch-git-workflow/).

#### How do I debug an ad that is appearing on a page?

First check whether the ad is appearing in uBlock. If it is, then this is not an ADN-specific problem (though we may want to fix it anyway). If the ad _does_ not show in uBlock, then it is likely the case that it is being blocked in uBlock, but not in ADN (remember that we don't want to block ads, only hide them). So then we need to add a cosmetic filter (in AdNauseam filters) to replace the blocking filter that uBlock uses. All devs should learn how to do this (either by using the browser inspector, or the [block-element tool](https://github.com/gorhill/ublock/wiki/element-picker)):

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

First we need to check if the Ad is being correctly detected by the parser.js content-script. We can check do this by looking at the browser console for the page to see if the Ad was detected there (there will be an "IMG-AD" if so). If not, there may be warning messages that will give you a clue as to what went wrong (skip to Case 2 below). 

Case 1: the Ad was correctly detected by the content-script. Here we need to look for messages in the addon console (chrome://extensions->AdNauseam->background.html->console) to see if it was rejected there (perhaps as a duplicate or because it has an internal targetURL). If the Ad is a duplicate, we just need to clear our ads and test again. If the ad has an internal link but IS a valid ad, then we need to add the domain to 'internalLinkDomains' in core.js.

Case 2: the Ad was NOT detected by the content-script. Here we need to debug the parsing code (/src/js/adn/parser.js) to figure out where it is failing. You can use the debugger to do this, but it may also be useful to turn on the vAPI.debugAdParsing flag on whichever platform you are using (either in platform/chromium/vapi-client.js OR platform/firefox/vapi-client.js).

#### How do I debug a text-ad that is being hidden, but not found?

In this case, we need to first determine whether we have a filter for this type of text-ad (these filters are in /src/js/adn/textads.js). If not, we may or may not want to add a filter, depending on how popular a site the text-ads are found on, so simply mark the ticket with this question. If we do, then we need to debug why it is not working correctly. (pending)

#### How should I setup my browser profiles for developing?

It is highly recommended to setup separate browser profiles for development (at very least you should have one for AdNauseam and one for uBlock). This enables you to compare results between AdNAuseam and uBlock, and also to prevent tests being influenced by cookies and other shared state. Remember also to modify your Firefox (development or nightly build) profiles according to [these steps](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers). In Chrome, you can simply enable developer mode.

##### In Chrome

1. Go to chrome://settings/
1. In "People" section, click "Add Person"
1. Choose a picture and give your new profile a name. Ex: AdNauseamDev
1. Click "Add"
1. Now a new chrome window is opened with your new profile

In the same way you can add another profile for uBlock.
To switch among different profiles, right click on the right top corner of chrome browser. You will see a dropdown menu showing all the profiles you have created.

##### In Firefox

Please see the following mozilla support page for detailed explanation and steps:
https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles

You can also use the profile switcher [add-on](https://addons.mozilla.org/en-US/firefox/addon/profileswitcher/) to switch among profiles.

#### What is the relationship between blocking and hiding rules in uBlock and ADN?

Blocking rules block the requested element, no matter its type, from being fetched by the browser. Hiding rules (also called 'Cosmetic filters') cause the element to be downloaded and added to the DOM as usual, but then hidden via CSS. Filter lists are combinations of blocking and hiding rules. The only difference between uBlock and ADN in this regard is that ADN cannot block elements which are part of, or generate, visual advertising. These elements must instead be hidden, which may be done by an existing hiding rule (in one of the filter-lists), or via a new hiding rule specific to ADN (generally placed in the built-in adnauseam.txt filter list).

For completeness, there are also 2 other kinds of rules: exception rules, which are similar to blocking rules, except that they define which requests should be allowed even if other matching blocking rules exist; and Dynamic-filtering rules, available only in iBlock's 'advanced mode', which are explained [here](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-rule-syntax).

#### How do I use the logger, and what are the different types of entries it shows?

Open the uBlock menu by clicking on the 'µ' icon in the ADN menu, then click on the logger icon. Choose the tab you are interested in, then click the refresh icon. This will refresh the tab with the logger activated, and you will see each request made by the browser (whether blocked, allowed, or hidden). For info on the different types of entries, see this [page](https://github.com/gorhill/uBlock/wiki/The-logger).


#### How do I view extension messages in the console?

This depends on the browser and the code you are interested in.

##### In Chrome
 For messages from the extension core, use the console from background.html in chrome://extensions. For messages from interface-pages and content-scripts use the console from the page in question. For messages from the extension menu, right-click _inspect_, then use the console in the window that appears

##### In Firefox

Menu->Tools->Web Developer->Browser Console  (pending)

#### How do I view the extensions storage entries?

Go to chrome://extensions, then open the background.html page, then open the console and enter:

    chrome.storage.local.get(function(result){console.log(result)});

#### How can I get the first-run page to show up when developing?

First remove the ADN extension in chrome://extensions (using the trash icon), then reload

#### What is the difference between JS code in src and in platform?

Code in 'src/js' is cross-browser code that originates in uBlock, though it may have been modified in ADN's fork. Code in 'src/js/adn' is cross-browser code specific to ADN. Code in subdirectories of 'platform/' is code specific to a browser. You should not mess with this code unless you are an expert dev, _and_ have discussed the necessity of changes with the other devs.

With that said, this code implements the vAPI interface for each browser. This interface, which has a large version for the extension core, and a minimal version for content-scripts, abstracts away all browser specific details and exposes a common API for cross-platform code to use. Therefore, no browser specific code should ever be put within 'src/js' or 'src/js/adn'. Instead, the code must be placed within a vAPI function (which means changing the interface, and should be considered a big deal) and then implemented ånd tested for each of the browser platforms.


####What is uDom?
uDom, written by Raymond Hill for uBlock, is a minimalist DOM framework that provides the core functionality of something like jQuery, without the size. Thus you should not mix jQuery with uDom, as they provide the same basic functionality. In fact, you should not use jQuery at all in AdNauseam. The one (temporary) exception to this is the vault, pending its rewrite. A list of uDom functions follows below (in progress).

- on()
- attr()
- prop()
- css()
- val()
- html()
- text()
- onLoad()
- nodeFromId()
- nodeFromSelector()
- appendTo()
- addClass
- removeClass
- toggleClass

####How do I run the browser's debugger on different parts of the extension?



(pending)

