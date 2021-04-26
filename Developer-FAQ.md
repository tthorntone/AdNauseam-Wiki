## Welcome and thanks for visiting!

AdNauseam is a completely non-profit, volunteer-run project dedicated to protecting privacy online... and we REALLY do need your help!

There are _many ways to contribute,_  from testing, to translating, to documenting, to helping us develop and nurture our community (and of course coding!) 

If you're interested in helping, just send an email to _adnauseam-at-rednoise.org_
telling us about your interests and skills and we will help you get started!

<img alt="the AdNauseam finger" src="https://camo.githubusercontent.com/fef7dc37503e6356d2558bada3c75091785893bdc1e32d7eabf302f8bb101ddd/68747470733a2f2f7265646e6f6973652e6f72672f696d616765732f61646e61757365616d2e706e67" width="300"/>

### Getting Started
* [How to build AdNauseam from source?](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers))
* [What is the usual workflow for developers?](#what-is-the-usual-workflow-for-developers)
* [How should I setup my browser profiles for developing?](#how-should-i-setup-my-browser-profiles-for-developing)
* [How can I get the first-run page to show up when developing?](#how-can-i-get-the-first-run-page-to-show-up-when-developing)
* [How should I setup for firefox android?](#how-should-i-setup-for-firefox-android)
* [How to manually install AdNauseam in Firefox (temporarily)](#how-to-manually-install-adnauseam-in-firefox-temporarily)

### How Things Work
* [How does AdNauseam detect Ads?](#how-does-adnauseam-detect-ads)
* [What is the relationship between blocking and hiding rules in uBlock and AdNauseam?](#what-is-the-relationship-between-blocking-and-hiding-rules-in-ublock-and-adn)
* [How does AdNauseam handle visual resources that link to the same domain?](#how-does-adnauseam-handle-visual-resources-that-link-to-the-same-domain)
* [What is the difference between JS code in src and in platform?](#what-is-the-difference-between-js-code-in-src-and-in-platform)
* [What ads does AdNauseam collect?](#what-ads-does-adnauseam-collect)
* [How does the Ad-parsing mechanism work?](#how-does-ad-parsing-work)
* [How are messages passed to AdNauseam core functions?](#how-are-messages-passed-to-adnauseam-core-functions)
* [What does it mean for AdNauseam to appear as 'paused' in the menu?](#what-does-it-mean-for-adnauseam-to-appear-as-paused-in-the-menu)
* [What does it mean when 'Do Not Track (DNT)' is enabled?](#what-does-it-mean-when-do-not-track-dnt-is-enabled)
* [What is the data format for Ad imports/exports?](#what-is-the-data-format-for-ad-importsexports)
* [How does AdNauseam handle asset managements?](#how-does-adNauseam-handle-asset-managements)
* [How does AdNauseam handle incoming and outgoing cookies?](#how-does-adnauseam-handle-incoming-and-outgoing-cookies)
* [What is ‘Strict Blocking’, and when should I use it?](#what-is-strict-blocking-and-when-should-i-use-it)

### Common Tasks
* [How do I view extension messages in the console?](#How-do-I-view-extension-messages-in-the-console)
* [How do I run the browser's debugger on different parts of the extension?](#how-do-i-run-the-browsers-debugger-on-different-parts-of-the-extension)
* [How do I use the logger, and what are the different types of entries it shows?](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#how-do-i-use-the-logger-and-what-are-the-different-types-of-entries-it-shows)
* [How do I view the metadata for an ad?](#how-do-i-view-the-metadata-for-an-ad)
* [How do I view AdNauseam-specific network events in the addon console?](#how-do-i-view-adnauseam-specific-network-events-in-the-addon-console)
* [How do I view the extensions storage entries?](#how-do-i-view-the-extensions-storage-entries)
* [How are locales/languages/translations handled?](https://github.com/dhowe/AdNauseam/wiki/Handling-languages,-locales,-and-translations)
* [How do I inspect the requests/visits made by AdNauseam to collected Ads?](#how-do-i-inspect-the-requestsvisits-made-by-adnauseam-to-collected-ads)
* [How do I merge in upstream (uBlock) code?](#how-do-i-merge-in-upstream-ublock-code)
* [How do I create a new release?](#how-do-i-create-a-new-release)
* [How do I create a custom filter for a text or text-hybrid ad](#how-do-i-create-a-custom-filter-for-a-text-or-text-hybrid-ad)



### Debugging / Testing
* [How do I debug an ad that is visible on a page?](#how-do-i-debug-an-ad-that-is-appearing-on-a-page)
* [How do I debug a video ad that is visible on a page?](#how-do-i-debug-a-video-ad-that-is-appearing-on-a-page)
* [How do I debug an image ad that is being hidden, but not collected?](#how-do-i-debug-an-image-ad-that-is-being-hidden-but-not-collected)
* [How do I debug a text ad that is being hidden, but not collected?](#how-do-i-debug-a-text-ad-that-is-being-hidden-but-not-collected)
* [How do I test/verify functionality of a commit?](#how-do-i-testverify-functionality-of-a-commit)
* [How do I test a release candidate?](https://github.com/dhowe/AdNauseam/wiki/Testing-New-Release-Candidates)
* [How do I run the unit tests?](#how-do-i-run-the-unit-tests)


### Useful References
* [The git fork-and-branch workflow](http://blog.scottlowe.org/2015/01/27/using-fork-branch-git-workflow/)
* [Adblock Plus rule syntax (overview)](https://adblockplus.org/filter-cheatsheet)
* [Writing Adblock Plus filters (detailed)](https://adblockplus.org/filters)
* [What are Dynamic Filtering Rules?](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-rule-syntax)
* [What is the uDom?](#what-is-the-udom)
* [Chrome Extension Overview](https://developer.chrome.com/extensions/overview)
&nbsp;     
&nbsp;    

-----------
#### What is the usual workflow for developers?

New developers should begin by reading the [FAQ](https://github.com/dhowe/AdNauseam/wiki/FAQ) and [Developer FAQ](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ) and making sure that they can [build the extension](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers) in Chrome and Firefox. They should then start work on a ticket (either by selecting one, perhaps marked with the _Good Volunteer Task_ label, or by being assigned one). 

It is generally good practice to start a new git branch for the feature/ticket you are working on. Ask questions as you go (in the ticket itself, and/or via email), and when ready, submit a pull-request so that your branch can be merged in.

If multiple tickets are assigned to you, work on the one with highest priority, unless otherwise specified.

Sometimes you may be assigned a ticket with the label _Needs-verification_. In such cases, you should simply verify that the fix works as expected. If so, then the ticket can usually be closed. If not, document as specifically as possible how/why the fix fails.

The project uses the git fork-and-branch workflow, described nicely [here](http://blog.scottlowe.org/2015/01/27/using-fork-branch-git-workflow/).

-----------
#### How should I setup for firefox android?

1. Download `adnauseam-[VERSION].firefox.zip` file from desired AdNauseam release from the [release page](https://github.com/dhowe/AdNauseam/releases) and unzip it in your folder of choice.
2. Install [web-ext](https://extensionworkshop.com/documentation/develop/getting-started-with-web-ext/).
3. Install `adb` (Android Debug Bridge). Best solution for MacOS is using [brew](https://brew.sh/).
```
brew install android-platform-tools
```
4. Connect the Android Device with the USB to your computer.
5. Enable USB Debbuging on your Android phone.
6. Enable USB Debugging on Firefox Android in settings.  
7. Run `adb devices` on the terminal to get the id of your connected Android Device, e.g.: `cb16bcbe`. [reference link](https://stackoverflow.com/questions/17901692/set-up-adb-on-mac-os-x).
8. With the terminal go to the unziped AdNauseam release firefox folder where the `manifest.json` file is located.
9. Run the following command: (substituting `cb16bcbe` with your Android Device id)
```
web-ext run --target=firefox-android --android-device cb16bcbe --firefox-apk=org.mozilla.firefox
```
10. Adnauseam should be running now on Firefox on your Android device.

Further reference to web-ext commands [here](https://extensionworkshop.com/documentation/develop/web-ext-command-reference/) 

[Developing extensions for firefox for Android](https://extensionworkshop.com/documentation/develop/developing-extensions-for-firefox-for-android/).

-----------
#### How to manually install AdNauseam in Firefox (temporarily)

After downloading the `adnauseam-{VERSION}.firefox.zip`, open the about:debugging page, click "This Firefox" (in newer versions of Firefox), click "Load Temporary Add-on", then select any file in your extension's directory. The extension will now be installed, and will stay until you restart Firefox.

[Reference - Loading a temporary extension](https://developer.mozilla.org/en-US/docs/Tools/about:debugging#loading_a_temporary_extension)

-----------
#### How do I run the unit tests?
Make and load the extension as usual, then navigate to 'src/unit-tests.html' in your browser

#### How do I debug an ad that is appearing on a page?

Please check [Step-by-step dev documentation for fixing visible ads](https://github.com/dhowe/AdNauseam/wiki/Step-by-step-documentation-for-fixing-visible-ads)

-----------
#### How do I debug a video ad that is appearing on a page?

This process is similar to the [above](#how-do-i-debug-an-ad-that-is-appearing-on-a-page), except that because ADN is not collecting video Ads (at least for now), we need to add a block filter (for blocking), rather than a cosmetic filter (for hiding).

-----------
#### How do I debug an image-ad that is being hidden, but not collected?

First we need to check if the Ad is being correctly detected by the parser.js content-script. We can check do this by looking at the browser console for the page to see if the Ad was detected there (there will be an "IMG-AD" if so). If not, there may be warning messages that will give you a clue as to what went wrong (skip to _Case 2_ below).

_Case 1_

The Ad was correctly detected by the content-script. Here we need to look for messages in the addon console (chrome://extensions->AdNauseam->background.html->console) to see if it was rejected there (perhaps as a duplicate or because it has an internal targetURL). If the Ad is a duplicate, we just need to clear our Ads and test again. If the ad has an internal link but IS a valid ad, then we need to add the domain to 'internalLinkDomains' in core.js.

_Case 2_

The Ad was NOT detected by the content-script. Here we need to debug the parsing code (/src/js/adn/parser.js) to figure out where it is failing. You can use the debugger to do this, but it may also be useful to turn on the 'debugging' option on the settings page. For more details about how parser works, and a guideline of what the log messages mean, please check: [#how-does-parserjs-work).

_Case 3_ 

In rare cases, a dynamically-generated Ad appears to be hidden (and not collected), when in actuality the code to generate the Ad (usually JS code) was either blocked or redirected, and thus never executed. You can recognize such cases because the Ad will not be present in the DOM.  Further, in the logger you will find a JS resource being blocked or redirected. To address such cases it is generally necessary to create an exception rule (see the entry for Google's gpt.js script [here](https://github.com/dhowe/AdNauseam/blob/master/filters/adnauseam.txt#L540)) so that the JS is allowed to run. Once the rule is in effect, the logger entry should disappear and the Ad should be visible in the DOM. Then you can then evaluate whether it is being hidden and/or collected correctly, and if not, continue to debug as described above.

-----------
#### How do I create a custom filter for a text or text-hybrid ad?

To create a custom filter for text or text-hybrid ad, please make your changes in the file /src/js/adn/textads.js.


1. Create a new filter in the filters array  
A filter consists of four elements: selector, handler, name and domain. The selector should be the one used to target the ad you are going to parse. If there is more than one ad on a page, please use the selector for the outer div here, so that you can parse all the ads later in the handler later. The handler should be the name of the handler function you are going to create later for the ads; The domain is a regex expression that specify the domain that would trigger the current filter. 

2. Write a new handler  
Each handler takes the div selected by the filter and creates ads based on the information. Please go through the dom structure of each ad and try to specify the selector needed to parse the information. For a default text ad in adnauseam, you will need to find: title, text, the site and a target link. After finding all the information you can create an ad using vAPI.adParser.createAd and return an array of all the ads you found as the last step.
For details, please refer to the current handlers as a template to write your own.

-----------
#### How do I debug a text-ad that is being hidden, but not collected?

In this case, we need to first determine whether we have a filter for this type of text-ad (these filters can be found in /src/js/adn/textads.js). If not, we may or may not want to add a filter, depending on how popular a site the text Ads are found on, so simply mark the ticket with this question. If we do have a filter, then we need to debug why it is not working correctly. To see debugging messages from textads.js, activate debugging mode in Settings, then open the console for the page in question. From the debugging output, you should be able to see which text-ad handler is in use and where the parsing has failed (title, site or the detailed text of a text-ad).

-----------
#### How do I test/verify functionality of a commit?

Please always delete the addon and reinstall it whenever you are testing a commit or trying to go back to a previous version.
This can clear the stored preferences and avoid possible conflicts between the new and old version.

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
#### How does AdNauseam detect Ads?
Ads are detected via standard cosmetic, or 'hiding', filters found in whatever lists are currently enabled ([EasyList](https://easylist.to/) currently has the best rules for this, and thus the user is warned when it is disabled). Once a DOM element is detected by a cosmetic filter in one of uBlock's content-scripts, it is passed to AdNauseam's parser component where the ad's information (viewable by clicking an ad in the _vault_ to _inspect_ it) is extracted. This info includes timestamp, size, content-url, target-url, page-detected-on, etc. Text-only Ads, as often found on search engine, are a bit different as they are generally served inline along, with page content, rather than requested separately. In these cases, several additional fields are parsed (title, description, tagline) and there is no content-url linking to an external resource. To enable text-ad extraction, AdNauseam includes a custom set of CSS selectors (in textads.js) for common providers (Google, Ask, Bing, etc), which link to specific hand-written parsing routines. These run only on those domains for which such filters have been written.

-----------
#### What is the relationship between blocking and hiding rules in uBlock and ADN?

Blocking rules block the requested element from being fetched by the browser. Hiding rules (also called 'Cosmetic filters') cause the element to be downloaded and added to the DOM as usual, but then hidden via CSS. Filter lists are combinations of blocking and hiding rules. The only difference between uBlock and ADN in this regard is that ADN cannot block 3rd-party requests which are part of, or generate, visual advertising. These request must be allowed and the requested elements then hidden, which may be done via an existing hiding rule (in one of the filter-lists), or via a new hiding rule specific to ADN (generally placed in the _adnauseam.txt_ filter list).

An important point to note is that these 3rd-party requests, for which an active blocking rule exists, but which are _allowed_ by AdNauseam (because blocking would make collection of the Ad impossible), are marked and treated differently than those which are simply hidden (for example, all cookies from such requests are blocked, assuming they are not on a DNT list). These are often referred to as _adn-allowed_ requests as they would be blocked by uBlock, but are specifically allowed by AdNauseam.

Existing lists are divided into two categories, those that primarily block visual ads and those that block other requests, trackers, beacons, etc. Currently we only allow blocks for those in the latter category, as identified by the `enabledBlockLists` lists in core.js. If a list (Peter Lowe's for example) contains only blocking rules (and no hiding rules) AND this list blocks visual ads, then it is not useful for AdNauseam and is likely removed from the default list set (as is the case for Peter Lowe's list).

For completeness, there are also two other kinds of rules: exception rules, which are similar to blocking rules, except that they define which requests should be allowed even when other matching blocking rules exist; and dynamic-filtering rules, which are explained [here](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-rule-syntax).

-----------
#### What is ‘Strict Blocking’, and when should I use it?

By default AdNauseam only blocks requests that do not interfere with the collection of ads. However, when ‘Strict Blocking’ mode is enabled, AdNauseam will instead block all requests that match a blocking rule from an enabled third-party list. This means that LESS ads will be collected, placed in the vault, and later clicked, and that AdNauseam will be LESS effective in its primary function (for example, the majority of Google ads won’t be collected or clicked). 

Thus for most users ‘Strict Blocking’ mode is NOT RECOMMENDED. However, if you are primarily interested in blocking ads, you _may_ see better performance with ‘Strict Blocking’ enabled (depending on your settings and the specific sites you visit). You can read more about blocking and hiding rules in AdNauseam [here](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#what-is-the-relationship-between-blocking-and-hiding-rules-in-ublock-and-adn). Generally speaking this mode is for advanced users with specific use-cases (e.g., testing), so please be sure to understand the ramifications before enabling it. 

A BETTER OPTION is often to use ‘Strict Blocking’ in combination with dynamic filtering rules. You can follow [uBlock's dynamic filtering rule syntax](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-rule-syntax) to create your own strict blocking rules to block requests based on sites, 3rd-party domains, and request types. To compose strict-blocking rules, you will need to use the syntax `strictBlock` for the "action" component.

Here are a few examples:  
* To strict-block all the requests for facebook.com, you can use the following rule:
   `facebook.com * * strictBlock`  

* To strict-block all the requests coming from doubleclick.net for a certain site, you can use the following rule (this will stop google ads from rendering and prevent them from being collected and clicked by AdNauseam):
   `mysite.com doubleclick.net * strictBlock` 

* To strict-block all 3rd-party scripts for a certain site, you can use the following rule:
   `facebook.com * 3p-script strictBlock`

* Please note the difference between `strictBlock` and `block`. The `block` action blocks requests according to the dynamic filtering rules, while `strictBlock` only blocks a request if it triggers a blocking rule in one of the filter lists.

-----------
#### How do I use the logger, and what are the different types of entries it shows?

Open the uBlock menu by clicking on the 'µ' icon in the ADN menu, then click on the logger icon. Choose the tab you are interested in, then click the 'refresh' icon. This will refresh the tab with the logger activated, and you will see each request made by the browser (whether blocked, allowed, or hidden). For info on the different types of entries, see this [page](https://github.com/dhowe/AdNauseam/wiki/The-logger).

#### How does AdNauseam handle visual resources that link to the same domain?
Generally AdNauseam does not recognize Ads with internal target URLs. So an Ad found on xyz.com which links to a URL on xyz.com (or www.xyz.com) is ignored. However, some sites use this mechanism (generally with a redirect) for serving real Ads. These are sometimes text Ads and sometimes so-called 'native Ads'. One classic example is Google, where all Ads on search pages go first to a Google URL, and are then redirected. To accommodate these exceptions, AdNauseam maintains an array of domains called `internalLinkDomains` (see core.js). Adding a domain to this list will cause AdNauseam to no longer ignore internal Ads from that domain.

-----------
#### How do I view extension messages in the console?

This depends on the browser and the code you are interested in.

##### In Chrome
 For messages from the extension core, use the console from background.html in `chrome://extensions`. For messages from interface-pages and content-scripts use the console from the page in question. For messages from the extension menu, right-click _inspect_, then use the console in the window that appears

##### In Firefox

Unlike chrome, all the logging messages in firefox can be viewed at one place. 
Use `ctrl/command + shift + J` to open the browser console.

-----------
#### How do I view the extensions storage entries?

Go to chrome://extensions, then open the background.html page, then open the console and enter:

    chrome.storage.local.get(function(result){console.log(result)});

-----------
#### How do I inspect the requests/visits made by AdNauseam to collected Ads?

When the user has enabled the 'click-ads' preference, any Ad that is detected and parsed will then be visited. Currently this happens via an XMLHttpRequest (XHR, or in uBlock terminology, a *behind-the-scenes* request). Such requests are not initiated from the site the Ad was found on, but rather from the addon core. Such requests must ALWAYS be allowed by the browser if issued by AdNauseam itself (even, for example, when a user-level rule exists to block all XHR requests), or ad-clicking will fail.

To begin the process, AdNauseam makes a request to the URL stored in the parsed Ad's `targetUrl` property. This URL holds the 'clickable' link extracted from a DOM element during parsing (generally either the href attribute of an anchor tag, or the onclick handler target for some other tag). Such requests can be viewed in the addon console (background.html on chrome), in a line starting with `[TRYING] Ad#(img)...`. The URL logged here will be the same as displayed in the `targetUrl` property of the Ad object logged when the Ad is parsed, shown in a line starting with `[FOUND] Ad#(img)...`.

In the addon console, the actual request data can be seen (headers, response, etc.) in the 'Network' tab. Similarly, any redirects for the visit (status 302, for example) can also be viewed. In such cases, the chain of requests can be followed from the initial `targetUrl`, through some number (0 or more) of redirects until either the actual advertiser's site is reached (status 200), or a request in the chain fails (status 404, for example). The last URL to be reached successfully in this chain is stored in the Ad object as its `resolvedTargetUrl`, and the timestamp is stored as its `visitedTs`. If an error occurs, it is stored in the Ad's `errors` array, and the time stamped is logged as a negative value (timestamp * -1).

-----------

#### How do I merge in upstream (uBlock) code?

1. Fetch code and tags from upstream
  `$ git fetch --all --tags --prune`
1. Check out the tag for the release you want to merge
  `$ git checkout tags/1.10.2`
1. Create a new branch here, and verify the version number matches in manifest.json)
  `$ git checkout -b upstream1.10.2`
1. Go back to master
  `$ git checkout master`
1. Create a new branch for the merge
  `$ git checkout -b merge1.10.2`
1. Merge upstream branch to the new merge branch
  `$ git merge upstream1.10.6`
1. Resolve any merge conflicts

-----------

#### How do I create a new release?
1. Make sure [web-ext](https://github.com/mozilla/web-ext) is installed
1. Go to uAssets folder and update it by `git pull`
1. From the top-level of the AdNauseam folder, run tools/make-artifacts.sh
1. Make a new PR and add a note that a new release tag is needed on master
1. After the PR is accepted and a new release tag has been created in `dhowe/AdNauseam/master`, edit the release notes by adding information about the changes
1. Do a 'git pull' to fetch the new release tag
1. Run tools/make-artifacts.sh again and upload the five generated files to the release (note that in order to enable auto-updating, the chromium release MUST BE SIGNED with the AdNauseam key)
1. Once approved for production, submit the new release to the Opera and Firefox stores, and update the version and link on http://rednoise.org/adnauseam/updates.xml


-----------

#### After new release
1. Upload to Firefox and Opera add-on stores
2. Update the website (version number in 3 locations)
3. Make sure that the version # and link in the following page is updated: ````http://rednoise.org/adnauseam/updates.xml````
4. Install a previous version in chrome and verify that auto-update is triggered and the new version auto-installed 


-----------

#### How do I view the metadata for an ad?
- To see basic data for a single ad, simply click on the ad in the vault to inspect it.
- To view the full metadata for a single ad, click on the ad in the vault inspector,
then hit the 'd' on the keyboard to dump this data to both the addon and vault consoles.
- To view JSON data for all Ads, simply export your ad file from the settings interface.

-----------
#### How can I get the first-run page to show up when developing?

First remove the ADN extension in chrome://extensions (using the trash icon), then reload.
Note that for dev-builds (with version numbers in the form of X.Y.Z.Q, the first-run page 
is disabled.

-----------

#### What is the difference between JS code in `src` and in `platform`?

Code in 'src/js' is cross-browser code that originates in uBlock, though it may have been modified in ADN's fork. Code in 'src/js/adn' is cross-browser code specific to ADN. Code in subdirectories of 'platform/' is code specific to a browser. You should not mess with this code unless you are an expert dev, _and_ have discussed the necessity of changes with the other devs.

With that said, this code implements the vAPI interface for each browser. This interface, which has a large version for the extension core, and a minimal version for content-scripts, abstracts away all browser specific details and exposes a common API for cross-platform code to use. Therefore, no browser specific code should ever be put within 'src/js' or 'src/js/adn'. Instead, the code must be placed within a vAPI function (which means changing the interface, and should be considered a big deal) and then implemented ånd tested for each of the browser platforms.

--------------------

#### How are messages passed to AdNauseam core functions?

Messages from page-scripts (menu.js, vault.js, etc) and content-scripts (parser.js, textads.js, etc) are _automatically_ invoked on functions exported from the AdNauseam object. For example, in menu.js, a message is created and sent as follows:

`  vAPI.messaging.send('adnauseam', { what: 'adsForPage', tabId: popupData.tabId } ...);`

When this message is received in the addon core, the `adnauseam.adsForPage(request, pageStore, tabId, frameId)` function is automatically invoked with the arguments shown.

--------------------

#### What ads does AdNauseam collect?

At this stage AdNauseam only collects:

* Image Ads 
* Text Ads from search result page (google/bing/ask/yahoo/duckduckgo/aol/baidu)

What AdNauseam only blocks and doesn't collect:

* Video Ads
* Audio Ads
* Dynamically-assembled Ads [example](https://github.com/dhowe/AdNauseam/issues/765)
* Ads that are drawn to a canvas
* Background images
* Internal Ads ([exceptions](https://github.com/dhowe/AdNauseam/blob/master/src/js/adn/core.js#L45))

--------------------

#### How does Ad parsing work?

When a cosmetic rule fires for an element on the page, the element is passed to the `process()` function in [parser.js](https://github.com/dhowe/AdNauseam/blob/master/src/js/adn/parser.js). With the 'debugging' option enabled on the settings page, related messages will appear in the console in the following format: `process(tagName)...`.

There are three main cases handled by the `process()` function: images, iFrames, and other.

`1. Images —> findImageAds() —> processImage()  `

`2. IFrames  —> processIFrame —> check inside for image elements —> processImage()  `

`3. Other —> check inside for image elements —> processImage(), then check for text Ads`


**1. Images**

With the exception of text Ads, the parser's main role is to detect clickable Ad images. If all goes well after an image is matched by a cosmetic filter, then you will see a message in the page console saying 'IMG-AD' and the Ad will be viewable in both the menu and vault.

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

#### What does it mean for AdNauseam to appear as 'paused' in the menu?

If AdNauseam is paused, there could be several scenarios:
1.You are on browser pages or pages for browser extensions.
2.You have paused AdNauseam for this specific page. You can resume AdNauseam by clicking the "Resume AdNauseam" button in the menu.
3.You have paused AdNauseam for the whole site. In this case, you can delete the site entry from the whitelist page in settings.

-----------

#### What does it mean when 'Do Not Track (DNT)' is enabled?

This setting applies for [sites](https://www.eff.org/files/effdntlist.txt) that follow the [EFF](ttps://www.eff.org)'s [Do Not Track](https://www.eff.org/dnt-policy) standard. 

With either of the 'Do Not Track (DNT)' settings enabled, AdNauseam will send the DNT header and allow all requests to sites on the current DNT list (which is checked/updated like any other list), including any 3rd-parties on those pages.

Technically, the following changes occur when either (or both) of AdNauseam's DNT-exception options are disabled:

* <b>When "Don't hide non-tracking Ads" is checked </b> (hidingAds=true, disableHidingForDNT=true)

  * Ads will be collected, but NOT hidden on DNT sites (first party).

* <b>When "Don't click non-tracking Ads" is checked </b> (clickingAds=true, disableClickingForDNT=true)

  * Ads will be collected, but NOT clicked for DNT sites (both first party and third party).

* <b>When either of the above is checked</b>

  * The DNT header will be sent for ALL outgoing requests (traffic.js)
  * Incoming cookies from sites on the allowedExceptions list, which would normally be blocked, are allowed when the site is on the DNT list, unless blocked by other browser settings (core.js)

-----------

#### What is the data format for Ad imports/exports?

AdNauseam uses JSON format to store the exported ads. 
The basic structure of the file is as follows:  
* Unique hash for the page where the following ads are found  
 * Unique hash for the Ad itself
   * Ad Content  
 * Unique hash for the Ad itself
   * Ad Content  

The fields of each Ad include:
* **id**: a non-persistent sequential identifier
* **contentType**: the type of Ad, either 'img' or 'text'
* **contentData**: the 'data', src/width/height for image Ads, site/text/title for text Ads
* **title**: the title of the page the Ad leads to
* **targetUrl**: the link for the Ad (the URL loaded if the ad was to be clicked)
* **resolvedTargetUrl**: the final link for the Ad (after however many redirects)
* **pageUrl**: the url of the page the Ad was found on
* **pageTitle**: the title of the page the Ad was found on
* **foundTs**: the timestamp for when the Ad was initially found  
* **attemptedTs**:a timestamp when the last attempt to visit the Ad was made
* **visitedTs**: the timestamp for an visit in ms; either 0 (before it has been attempted), a positive-timestamp for a successful visit, or a negative timestamp on failure   
* **version**: the version of AdNauseam that created the Ad

-----------

#### How does AdNauseam handle asset managements?
##### uAssets


##### assets.js
All the information about filter lists is in file `assets.js`. For each update, adnauseam is going to update other filter lists based on the information in `assets.js`. If there is any change in the remote `assets.js` file, adnauseam will update `assets.js` first and update other list accordingly.

Each entry in assets.js looks like this:
  ```
  µBlock.assets.registerAssetSource('adnauseam.txt', {
    content: '[whatever you want]',
    contentURL: [ array of URLs of where to fetch the resource ],
    updateAfter: 2,
    submitter: 'adnauseam'
  });
  ```

`content` is just a token for what the content of the resource contains. uBO will look at this when gathering all the filter lists available -- in which case `content` will be `filters` (this makes the resource appear in the _3rd-party filters_ pane). uBO uses `internal` for resources other than filters.

`contentURL` can be a URL string or an array of URL strings. This tells the asset source manager where to get the resource. Typically I assume you will ship with a local version of `adnauseam.txt`, in which case you should list the relative URL in there, and a also provide a URL of where to fetch `adnauseam.txt` for update purpose.

`updateAfter` tells the asset updater how often (in days) it should pull the asset from its remote location(s).

The `submitter` field is needed **only** if you register the resource programmatically. This tells uBO to not remove the entry when it updates its own `assets.json` resource.

##### What happens when ‘update now’ button is clicked?  
_In 3pfilters.js_  
`SelectFilterLists()` will read the active filter lists from 3p-filters.html and return the selection. Then the selection will be passed to `ApplyFilterListSelection()`, and get saved the in local storage.
Finally, the content script will send a  `forceUpdateAssets` message to trigger the background script.

_In assets.js_  
An update will be scheduled and  `µBlock.assets.updateStart({...})` will force AdNauseam to launch an update session, i.e. lookup what is obsolete (as per `updateAfter`) and for assets in need of an update, to pull assets from their remote locations and cache them locally. If auto-update is enabled, the semantic of `µBlock.assets.get('adnauseam.txt', ...)` is to return the most recent version of the asset, keeping in mind that auto-update kicks in a few minutes after launch.

When an asset is updated, the asset manager fires a notification to observers registered through `µBlock.assets.addObserver(callback)`, and the observer call will be passed the argument `topic` and `details`, where `topic` will be `'after-asset-updated'`, and `details` is an object with the properties `assetKey`  and `content` which is the new content.

##### What happens when the ‘update’ button next to AdNauseam filters is clicked?  
A  ‘forceUpdateAdNauseam’ message will be sent to the background script and `updateAdNauseam` will grab adnauseam.txt from remote and update that single file instead of updating all the selected lists in 3rd-party filters.  

Based on gorhill's comment in [issue752](https://github.com/dhowe/AdNauseam/issues/752)

-----------

#### How does AdNauseam handle incoming and outgoing cookies?

Incoming cookies are blocked when responses comes from an ad-visit OR a domain in the allowedExceptions list, which is NOT an enabled DNT entry. Outgoing cookies are not manipulated. 

Path: vapi-background.js::handleResponseHeaders() -> traffic.js::onHeadersReceived()


-----------
#### How do I view AdNauseam-specific network events in the addon console?

To view such events (blocks, allows, cookies, headers, etc.), enable the 'debugging' option on the settings page, then open the addon console as usual (for example, by clicking on 'background.html' on the extensions page, in Chromium with developer-mode enabled)

-----------
#### How do I run the browser's debugger on different parts of the extension?

**Chrome / Opera**  
* Background-scripts: click on background.html in chrome://extensions, then go to tab 'Sources'
* Content-scripts: right click on the page in question, then choose 'inspect' and go to tab 'Sources'.

**Firefox**
1. Open the `about:debugging` page in Firefox
2. Make sure the "Enable add-on debugging" box is checked
3. Click the "Debug" button next to your add-on's entry in the page
4. Next you'll see a dialog asking you to accept an incoming connection. Click "OK", and the debugger will start in a separate window.

-----------
#### What is the uDom?
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
