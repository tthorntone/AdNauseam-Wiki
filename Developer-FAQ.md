## Frequently Asked Questions for Developers  (in progress)


### Getting Started
* [How to build AdNauseam from source?](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers))
* [What is the usual workflow for developers?](#what-is-the-usual-workflow-for-developers)
* [How should I setup my browser profiles for developing?](#how-should-i-setup-my-browser-profiles-for-developing)
* [How can I get the first-run page to show up when developing?](#how-can-i-get-the-first-run-page-to-show-up-when-developing)


### How Things Work
* [How does AdNauseam detect ads?](#how-does-adnauseam-detect-ads)
* [What is the relationship between blocking and hiding rules in uBlock and AdNauseam?](#what-is-the-relationship-between-blocking-and-hiding-rules-in-ublock-and-adn)
* [How does AdNauseam handle visual resources that link to the same domain?](#how-does-adnauseam-handle-visual-resources-that-link-to-the-same-domain)
* [What is the difference between JS code in src and in platform?](#what-is-the-difference-between-js-code-in-src-and-in-platform)
* [How does Ad parsing work?](#how-does-ad-parsing-work)

### Common Tasks
* [How do I view extension messages in the console?](#How-do-I-view-extension-messages-in-the-console)
* [How do I run the browser's debugger on different parts of the extension?](#how-do-i-run-the-browsers-debugger-on-different-parts-of-the-extension)
* [How do I use the logger, and what are the different types of entries it shows?](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#how-do-i-use-the-logger-and-what-are-the-different-types-of-entries-it-shows)
* [How do I view the metadata for an ad?](#how-do-i-view-the-metadata-for-an-ad)
* [How do I view AdNauseam-specific network events in the addon console?](#how-do-i-view-adnauseam-specific-network-events-in-the-addon-console)
* [How do I view the extensions storage entries?](#how-do-i-view-the-extensions-storage-entries)
* [How are locales/languages/translations handled?](https://github.com/dhowe/AdNauseam/wiki/Handling-languages,-locales,-and-translations)
* [How do I inspect the requests/visits made by AdNauseam to collected Ads?](#how-do-i-inspect-the-requestsvisits-made-by-adnauseam-to-collected-ads)

### Debugging / Testing
* [How do I debug an ad that is visible on a page?](#how-do-i-debug-an-ad-that-is-appearing-on-a-page)
* [How do I debug a video ad that is visible on a page?](#how-do-i-debug-a-video-ad-that-is-appearing-on-a-page)
* [How do I debug an image ad that is being hidden, but not collected?](#how-do-i-debug-an-image-ad-that-is-being-hidden-but-not-found)
* [How do I debug a text ad that is being hidden, but not collected?](#how-do-i-debug-a-text-ad-that-is-being-hidden-but-not-found)
* [How do I test functionality of a commit or release?](https://github.com/dhowe/AdNauseam/wiki/Testing-New-Release-Candidates)


### Useful References
* [The git fork-and-branch workflow](http://blog.scottlowe.org/2015/01/27/using-fork-branch-git-workflow/)
* [Adblock Plus rule syntax (overview)](https://adblockplus.org/filter-cheatsheet) | [Writing Adblock Plus filters (detailed)](https://adblockplus.org/filters)
* [What are Dynamic Filtering Rules?](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-rule-syntax)
* [What is the uDom?](#what-is-the-udom)
* [Chrome Extension Overview](https://developer.chrome.com/extensions/overview) 
&nbsp;     
&nbsp;    

-----------
#### What is the usual workflow for developers?

New developers should begin by reading the [FAQ](https://github.com/dhowe/AdNauseam/wiki/FAQ) and [Developer FAQ](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ) and making sure that they can [build the extension](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers) in Chrome, Firefox, or both. They should then start work on a ticket (either by selecting one, perhaps marked with the _Good Volunteer Task_ label, or by being assigned one). It is generally good practice to start a new git branch for the feature/ticket you are working on. Ask questions as you go (in the ticket itself, and/or via email), and when ready, submit a pull-request so that your branch can be merged in.

If multiple tickets are assigned to you, work on the one with highest priority, unless otherwise specified.

Sometimes you may be assigned a ticket with the label _Needs-verification_. In such cases, you should simply verify that the fix works as expected. If so, then the ticket can usually be closed. If not, document as specifically as possible how/why the fix fails.

The project uses the git fork-and-branch workflow, described nicely [here](http://blog.scottlowe.org/2015/01/27/using-fork-branch-git-workflow/).

-----------
#### How do I debug an ad that is appearing on a page?

First check whether the ad is appearing in uBlock. If it is, then this is not an ADN-specific problem (though we may want to fix it anyway). If the ad _does_ not show in uBlock, then it is likely the case that it is being blocked in uBlock, but not in ADN (remember that we don't want to block ads, only hide them). So then we need to add a cosmetic filter (in AdNauseam filters) to replace the blocking filter that uBlock uses. All devs should learn how to do this (either by using the browser inspector, or the [block-element tool](https://github.com/gorhill/ublock/wiki/element-picker)):

1.  Select/create the cosmetic rule you want to use to block the ad
1.  Test it by adding it to Options->Dashboard->My Filters->Apply-changes
1.  If its OK, add the rule to the text-file: /AdNauseam/assets/ublock/adnauseam.txt
1.  Remove the rule from Options->Dashboard->My Filters, then click Apply-changes
1.  Rebuild/reload the extension, then click Options->Dashboard->3rd-Party-Filters->Purge-all-caches, then click Apply-changes
1.  You should now see the # of 'AdNauseam filters' increase to include your new rule
1.  Test by visiting the page in question to verify the ad is now hidden

-----------
#### How do I debug a video ad that is appearing on a page?

This process is similar to the [above](#how-do-i-debug-an-ad-that-is-appearing-on-a-page), except that because ADN is not collecting video ads (at least for now), we need to add a block filter (for blocking), rather than a cosmetic filter (for hiding).

-----------
#### How do I debug an image-ad that is being hidden, but not found?

First we need to check if the Ad is being correctly detected by the parser.js content-script. We can check do this by looking at the browser console for the page to see if the Ad was detected there (there will be an "IMG-AD" if so). If not, there may be warning messages that will give you a clue as to what went wrong (skip to _Case 2_ below). 

_Case 1_

The Ad was correctly detected by the content-script. Here we need to look for messages in the addon console (chrome://extensions->AdNauseam->background.html->console) to see if it was rejected there (perhaps as a duplicate or because it has an internal targetURL). If the Ad is a duplicate, we just need to clear our ads and test again. If the ad has an internal link but IS a valid ad, then we need to add the domain to 'internalLinkDomains' in core.js.

_Case 2_

The Ad was NOT detected by the content-script. Here we need to debug the parsing code (/src/js/adn/parser.js) to figure out where it is failing. You can use the debugger to do this, but it may also be useful to turn on the 'netLogging' flag in core.js. For more details about how parser works, and a guideline of what the log messages mean, please check: [#how-does-parserjs-work).

-----------
#### How do I debug a text-ad that is being hidden, but not found?

In this case, we need to first determine whether we have a filter for this type of text-ad (these filters are in /src/js/adn/textads.js). If not, we may or may not want to add a filter, depending on how popular a site the text-ads are found on, so simply mark the ticket with this question. If we do, then we need to debug why it is not working correctly. (pending)

-----------
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

-----------
#### How does AdNauseam detect ads?
Ads are detected via standard cosmetic, or 'hiding', filters found in whatever lists are currently enabled ([EasyList](https://easylist.to/) currently has the best rules for this, and thus the user is warned when it is disabled). Once a DOM element is detected by a cosmetic filter in one of uBlock's content-scripts, it is passed to AdNauseam's parser component where the ad's information (viewable by clicking an ad in the _vault_ to _inspect_ it) is extracted. This info includes timestamp, size, content-url, target-url, page-detected-on, etc. Text-only ads, as often found on search engine, are a bit different as they are generally served inline along, with page content, rather than requested separately. In thesecases, several additional fields are parsed (title, description, tagline) and there is no content-url linking to an external resource. To enable text-ad extraction, AdNauseam includes a custom set of CSS selectors (in textads.js) for common providers (Google, Ask, Bing, etc), which link to specific hand-written parsing routines. These run only on those domains for which such filters have been written.

-----------
#### What is the relationship between blocking and hiding rules in uBlock and ADN?

Blocking rules block the requested element, no matter its type, from being fetched by the browser. Hiding rules (also called 'Cosmetic filters') cause the element to be downloaded and added to the DOM as usual, but then hidden via CSS. Filter lists are combinations of blocking and hiding rules. The only difference between uBlock and ADN in this regard is that ADN cannot block elements which are part of, or generate, visual advertising. These elements must instead be hidden, which may be done via an existing hiding rule (in one of the filter-lists), or via a new hiding rule specific to ADN (generally placed in the adnauseam.txt filter list).

For completeness, there are also two other kinds of rules: exception rules, which are similar to blocking rules, except that they define which requests should be allowed even when other matching blocking rules exist; and dynamic-filtering rules, available only in AdNauseam or iBlock's 'advanced mode' which are explained [here](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-rule-syntax).

-----------
#### How do I use the logger, and what are the different types of entries it shows?

Open the uBlock menu by clicking on the 'µ' icon in the ADN menu, then click on the logger icon. Choose the tab you are interested in, then click the refresh icon. This will refresh the tab with the logger activated, and you will see each request made by the browser (whether blocked, allowed, or hidden). For info on the different types of entries, see this [page](https://github.com/gorhill/uBlock/wiki/The-logger).

####How does AdNauseam handle visual resources that link to the same domain?
Generally AdNauseam do not allow ads with internal target URLs. So an ad found on xyz.com which links to a URL on xyz.com (or www.xyz.com) is ignored. However, some sites use this mechanism (generally with a redirect) for serving real ads. These are sometimes text ads and sometimes so-called 'native ads'. One classic example is Google where all ads on search pages go first to a Google URL, and are then redirected. To accommodate these exceptions, AdNauseam maintains an array of domains  called `internalLinkDomains` (see core.js). Adding a domain to this list will cause AdNauseam to no longer reject internal ads from that domain.

-----------
#### How do I view extension messages in the console?

This depends on the browser and the code you are interested in.

##### In Chrome
 For messages from the extension core, use the console from background.html in `chrome://extensions`. For messages from interface-pages and content-scripts use the console from the page in question. For messages from the extension menu, right-click _inspect_, then use the console in the window that appears

##### In Firefox

Menu->Tools->Web Developer->Browser Console  (pending)

-----------
#### How do I view the extensions storage entries?

Go to chrome://extensions, then open the background.html page, then open the console and enter:

    chrome.storage.local.get(function(result){console.log(result)});

-----------
#### How do I inspect the requests/visits made by AdNauseam to collected Ads?

When the user has enabled the 'click-ads' preference, any Ad that is detected and parsed will then be visited. Currently this happens via an XMLHttpRequest (XHR, or in uBlock terminology, a *behind-the-scenes* request). Such requests are not initiated from the site the Ad was found on, but rather from the addon core. Such requests must ALWAYS be allowed by the browser if issued by AdNauseam itself (even, for example, when a user-level rule exists to block all XHR requests).

To begin the process, AdNauseam makes a request to the URL stored in the parsed Ad `targetUrl` property. This URL holds the 'clickable' link extracted from a DOM element during parsing (generally either the href attribute of an anchor tag, or the onclick handler target for some other tag). Such requests can be viewed in the addon console (background.html on chrome), in a line starting with `[TRYING] Ad#(img)...`. The URL logged here will be the same as displayed in the `targetUrl` property of the Ad object logged when the Ad is parsed, shown in a line starting with `[FOUND] Ad#(img)...`.

In the addon console, the actual request data can be seen (headers, response, etc.) in the 'Network' tab. Similarly, any redirects for the visit (status 302, for example) can also be viewed. In such cases, the chain of requests can be followed from the initial `targetUrl`, through some number (0 or more) of redirects until either the actual advertiser's site is reached (status 200), or a request in the chain fails (status 404, for example). The last URL to be reached successfully in this chain is stored in the Ad object as its `resolvedTargetUrl`, and the timestamp is stored as its `visitedTs`. If an error occurs, it is stored in the Ad's `errors` array, and the time stamped is logged as a negative value (timestamp * -1).

-----------

#### How do I view the metadata for an ad?
- To see basic data for a single ad, simply click on the ad in the vault to inspect it.
- To view the full metadata for a single ad, click on the ad in the vault inspector,
then hit the 'd' on the keyboard to dump this data to both the addon and vault consoles.
- To view JSON data for all ads, simply export your ad file from the settings interface.

-----------
#### How can I get the first-run page to show up when developing?

First remove the ADN extension in chrome://extensions (using the trash icon), then reload

-----------

#### What is the difference between JS code in src and in platform?

Code in 'src/js' is cross-browser code that originates in uBlock, though it may have been modified in ADN's fork. Code in 'src/js/adn' is cross-browser code specific to ADN. Code in subdirectories of 'platform/' is code specific to a browser. You should not mess with this code unless you are an expert dev, _and_ have discussed the necessity of changes with the other devs.

With that said, this code implements the vAPI interface for each browser. This interface, which has a large version for the extension core, and a minimal version for content-scripts, abstracts away all browser specific details and exposes a common API for cross-platform code to use. Therefore, no browser specific code should ever be put within 'src/js' or 'src/js/adn'. Instead, the code must be placed within a vAPI function (which means changing the interface, and should be considered a big deal) and then implemented ånd tested for each of the browser platforms.

--------------------

####How does Ad parsing work?

When a cosmetic rule fires for an element on the page, the element is passed to the `process()` function in [parser.js](https://github.com/dhowe/AdNauseam/blob/master/src/js/adn/parser.js). With the 'netLogging' flag enabled on core.js, related messages will appear in the console in the following format: `process(tagName)...`.

There are three main cases handled by the `process()` function: images, iFrames, and other.

`1. Images —> findImageAds() —> processImage()  `

`2. IFrames  —> processIFrame —> check inside for image elements —> processImage()  `

`3. Other —> check inside for image elements —> processImage(), then check for text-ads`


**1. Images**

With the exception of text-ads, the parser's main role is to detect clickable Ad images. If all goes well after an image is matched by a cosmetic filter, then you will see a message in the page console saying 'IMG-AD' and the Ad will be viewable in both the menu and vault. 

If this message shows in the page console, but the Ad does not appear in the menu or vault, then the Ad was rejected by the addon core. This generally happens because the detected ad is a duplicate ([EXISTS] will show in the addon console), or, because its target (where it leads when clicked) is internal (in the same domain as the page on which it was found). In this case, [INTERN] will show in the addon console and the Ad will be rejected, unless it is listed in `internalLinkDomains` in [core.js](https://github.com/dhowe/AdNauseam/blob/master/src/js/adn/core.js).

If no IMG-AD message appears in the console, then one of several things may have happened:

1. No valid src attribute could be found for the image (a "No ImgSrc" message will show in the page console)
2. No clickable parent could be found for the image (a "No clickable parent" message will show in the page console)
3. Some other error occurred (some other message will show in the page console)

**2. IFrames**

If an iFrame matches a cosmetic selector and has a valid 'src' attribute, `processIFrame()` is called. If the iFrame's 'src' and parent page have the same origin, `processIFrame()` selects all images within the iFrame and handles them as above. If the iFrame is cross-domain, however, we will not be able to access its contents due to "Same Origin" security restrictions. In this case, we may need to manually create a new cosmetic filter for the element of interest _inside_ the  the iFrame (and add it to adnauseam.txt).
 
If, on Chromium-based browsers, an iFrame is dynamically-generated, the `primeLocalIFrame()` function attempts to inject the usual contentscripts into the iFrame (this will happen automatically on Firefox).  If the injection is successful, a console message in the addon console will read as follows:
  
`[INJECT] Dynamic-iFrame...`

You may inspect the [pageStore object](https://github.com/dhowe/AdNauseam/blob/master/src/js/pagestore.js) to find more information about the iFrame.

**3. Other**

If an element matches a cosmetic filter but is NOT an image or IFrame, `process()` will search inside it for elements of type image. If any images are found, they will be processed in the usual manner. After all these steps have completed, `process()` will finally check whether the element matches any text-ad filters

**Text-ad parsing**

`textAdParser.process() —> checkFilters() —> corresponding handler function`

All actions related to text-ad parsing occur within [textads.js](https://github.com/dhowe/AdNauseam/blob/master/src/js/adn/textads.js). If domain of the current page matches the AdNauseam's domain list (including Google, Ask, AOL, Yahoo, Bing, Baidu, etc.), `checkFilters()` will invoke the corresponding handler function (e.g., `googleText()`) to process the text-ad. In each handler function, information including title, text and site of the Ad is collected according to specific selectors. Finally, if all is successful, an Ad is created and passed to the addon core. If anything fails during the process, an error message should appear in the page console.

-----------
####How do I view AdNauseam-specific network events in the addon console?

To view such events (blocks, allows, cookies, headers, etc.), enable the `netLogging` flag in core.js, then open the addon console as usual

-----------
####How do I run the browser's debugger on different parts of the extension?

(pending)

-----------
####What is the uDom?
The uDom library, written by Raymond Hill for uBlock, is a minimalist DOM framework that provides the core functionality of something like jQuery, without the size. Thus you should not mix jQuery with uDom, as they provide the same basic functionality. In fact, you should not use jQuery at all in AdNauseam. The one (temporary) exception to this is the vault, pending its rewrite. A list of commonly used uDom functions follows below (in progress), or you may consult the [source](https://github.com/dhowe/AdNauseam/blob/master/src/js/udom.js).

- on()
- attr()
- css()
- val()
- html()
- text()
- onLoad()
- nodeFromId()
- nodeFromSelector()
- appendTo()
- addClass()
- removeClass()
- toggleClass()


&nbsp;

 