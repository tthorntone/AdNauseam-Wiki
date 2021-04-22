
First make sure that you are working with the correct commit (check the hash) or installed release, then perform each test on Firefox, Chrome, Opera and Edge. Check the console for background.html page as well as the UI pages throughout the process, report any error/warning messages.

**Test set**  
[Full test set](https://github.com/dhowe/AdNauseam/wiki/Testing-New-Release-Candidates#interface)  
[Basic / Android test set](https://github.com/dhowe/AdNauseam/wiki/Testing-New-Release-Candidates#tests-for-firefox-android--basic-tests)  

## Interface

&nbsp;&nbsp;&nbsp;&nbsp;<b>First-Run</b>

- Remove and reinstall AdNauseam to trigger this page 
- [ ]  Test selection of various options (click-ads, block-malware, hide-ads, DNT)
- [ ]  Verify that the DNT option is visible _only_ when clicking OR hiding is enabled
- [ ]  Test that toggling the DNT option changes _both_ DNT options in Settings
- [ ]  Check the links on first-run page
- [ ]  Check the version number at left-bottom corner

&nbsp;&nbsp;&nbsp;&nbsp;<b>Menu</b>
- [ ]  Check all buttons and information (including the number of Ads and $$ cost, hidden if no ads)
- [ ]  Hover over Ad images and check zooming
- [ ]  Check that menu is correctly updated after ad-visiting
- [ ]  Check ad-visiting animation
- [ ]  Check there is no text overlap in the menu for text ads
- [ ]  Go to extensions page, the menu should show "AdNauseam is paused on current pages", make sure that the layout is correct.
- [ ]  Check that the Adnauseam logo links to homepage
- [ ]  Check that the uBlock menu is properly displayed and everything is readable

&nbsp;&nbsp;&nbsp;&nbsp;<b>Vault</b>
- [ ]  Verify loading animation, and centering/scaling of Ads on load
- [ ]  Zoom in/out using mouse wheel and buttons in the top-left corner 
- [ ]  Check function/layout of Inspector (for both image and text ads)
- [ ]  Check correct function of the date-filter slider at the bottom
- [ ]  Check that AdNauseam logo in the bottom-right corner links correctly to homepage  
- [ ]  Check correct calculation of ad cost
- [ ]  Test import/export/clear functions
- [ ]  Right-click on an ad and delete it. Refresh the page and check that it is successfully deleted
- [ ]  Check the statistics panel and make sure that an ad is correctly categorized for ad types, ad networks and sites
- [ ]  Click on "My statistics", the panel should be minimized with smooth animation

&nbsp;&nbsp;&nbsp;&nbsp;<b>Dashboard</b>
- [ ]  Check layout of buttons, check-boxes, and links in each tab
- [ ]  Test that all (i)nfo buttons lead to correct FAQ pages in each tab
- [ ]  On settings tab (options.html) check that when clicking or hiding are disabled, then all of their sub-items are also disabled
- [ ]  On settings tab (options.html), change click probabilities and refresh the page, make sure that the probabilities is set to the new value after page refresh
- [ ]  Scroll to the bottom of the settings tab, test reset/backup/restore buttons
- [ ]  Click on a filter in 3p-filters and make sure that asset viewer works
- [ ]  Test all the import/export/apply buttons for "My Filters"
- [ ]  Test that import/export buttons work for "My Rules"
- [ ]  Test creating deleting and modifying the rules in "My Ryles" (make sure to test `strictBlock` which is AdNauseam-specific 
- [ ]  Test whitelist
- [ ]  Check 2 version numbers in 'About' page (links.html)

&nbsp;&nbsp;&nbsp;&nbsp;<b>Toolbar Icon</b>
- [ ]  Check that the icon in the toolbar is in purple when AdNauseam is active
- [ ]  Check that the icon in the toolbar is in grey when AdNauseam is disabled
- [ ]  Check that the icon in the toolbar is in green when on DNT pages
- [ ]  Icon should animate each time an Ad is clicked
- [ ]  Double check that the badge number is correctly updated
- [ ]  Check that the text on hover is correct for active and disabled state

&nbsp;&nbsp;&nbsp;&nbsp;<b>Notifications</b>
- [ ]  Check that disabling hiding, clicking, or blocking on the first-run generates a notification warning at the top of the dashboard (all tabs), menu, and vault page (after first-run is closed or 'ok' is clicked). 
- [ ]  Check that disabling hiding, clicking, or blocking on the dashboard/options page generates a notification warning at the top of the dashboard(all tabs), menu, and vault page. 
- [ ]  Check that disabling EasyList/AdNauseam filters on the dashboard/3p-filters page generates a notification warning at the top of the dashboard(all tabs), menu, and vault page. 
- [ ]  Check that clicking 'reactivate' on a notification warning at the top of the dashboard, menu, or vault pages causes the visual state to change correctly, and the setting in question to be updated correctly. 
- [ ]  In Firefox, choose "strict" for Enhanced Tracking Protection in `about:preferences#privacy`. Check that a notification shows up after the setting is changed. 
- [ ]  Check that the vault (if open) is updated when notifications change
- [ ]  Check that the dashboard (if open) is updated when notifications change
- [ ]  Dashboard: settings (options.html) Check that page refreshes correctly when a notification is 'reactivated'
- [ ]  Dashboard::3rd-Party (3p-filters.html) Check that page refreshes correctly when a list-notification is 'reactivated'
- [ ]  [Opera only] If "allow access to search page results" is unchecked, AdNauseam will show a corresponding notification in menu on the search result page. (Test Google search result for "credit card")

&nbsp;&nbsp;&nbsp;&nbsp;<b>Logger</b>
- [ ]  Visit a random web page then open the logger
- [ ]  Check that the logger is properly displayed and all entries are readable
- [ ]  Click on the 'i' icon on the top right corner of the screen, make sure that it links to AdNauseam's wiki page for the logger

------------------

## Ad Hiding/Parsing
- [ ]  Test a set of pages, and make sure that ads are being captured and visited   
  * TextAds: visit Google/Ask/Yahoo/Bing/DuckDuckGo to search for keywords such as "credit card" or "loan"
  * ImageAds: visit NYTimes/Youtube/Facebook(Right column only)... and verify image ads are hidden and appear in menu
- [ ]  Test Ad-parsing from within dynamically-created iFrames: hidden and collected   
  Test cases: [Dynamic_iframe](http://rednoise.org/adntest/dynamic_iframe.html) 
- [ ]  Test Ad-parsing from cosmetically-filtered iFrames: hidden but not collected (without cosmetic filters for any contained elements)  [here](http://lab-lamp.scm.cityu.edu.hk/adntest/iframe-cosm.html)                       
------------------
## Ad clicking

**Visual**  
Check whether the clicking status of an ad is correctly indicated by the color of its border:

- [ ]  Blue - Pending
- [ ]  Purple - Clicked
- [ ]  Red -  Failed
- [ ]  Green - DNT

**Ad Visits**
- [ ]  Test different click probabilities

**Text**

- [ ]  If an ad is not visited because of the clicking frequency, the ad should be marked as "SKIPPED: Click Frequency "
- [ ]  If an ad is not visited because the user has already clicked it, the ad should be marked as "SKIPPED: Clicked by user "
- [ ]  When an ad is collected from a dnt site (Ex:duckduckgo), the ad should be marked as "SKIPPED: DNT Allowed" ("Allowed via Do Not Track Policy" in vault)
- [ ]  When clicking is disabled, all ads that are not "visited" or "failed" should be marked as "SKIPPED: Clicking Disabled:"

*[Real-world test cases for ad collection and clicking](https://github.com/dhowe/AdNauseam/wiki/Real-world-test-cases-for-ad-collection-clicking)*

------------------
## DoNotTrack (DNT)
DNT: Go to a DNT page (Ex: duckduckgo.com) and check the following items:

&nbsp;&nbsp;&nbsp;&nbsp;<b>Headers/Cookies</b>

&nbsp;&nbsp;&nbsp;&nbsp;To check ad visits headers, click on request in browser's network panel, select 'Headers'
&nbsp;&nbsp;&nbsp;&nbsp;(For a more detailed network logging, you can check Chrome Net-Internals of the [tools](#tools) listed below.)
- [ ]  DNT-header is being sent correctly for ALL requests (including Ad visits) if either disableClickingForDNT and disableHidingForDNT are enabled (and vice versa) 
- [ ]  DNT Cookies are allowed (v3.1 and later)

&nbsp;&nbsp;&nbsp;&nbsp;<b>Hiding/Clicking</b>
- [ ]  Ads are visible when domain is 1st-party if disableHidingForDNT is checked
- [ ]  Requests are not blocked when domain is 1st-party iff disableHidingForDNT is checked
- [ ]  Requests are not blocked when domain is 3rd-party iff disableHidingForDNT is checked([here](http://lab-lamp.scm.cityu.edu.hk/adntest/effTestPage.html))
- [ ]  No clicking when ad domain is on list iff disableClickingForDNT is checked (especially for 3rd-party)
- [ ]  If both DNT options are disabled, then hiding, blocking, visiting occur again as usual(both first party and 3rd-party)

&nbsp;&nbsp;&nbsp;&nbsp;<b>Interface</b>
- [ ]  DNT list at top of whitelist.html is checked when either DNT option is checked, otherwise unchecked
- [ ]  Check that changing the two DNT settings will trigger DNT notifications with corresponding messages in the menu(dnt sites only)  
- [ ]  Check the layout of each DNT notification("?" should be in the middle, 'settings' button appears on hover)  

&nbsp;&nbsp;&nbsp;&nbsp;<i>[Test Page for 3rd-party DNT](http://lab-lamp.scm.cityu.edu.hk/adntest/effTestPage.html)</i>

------------------

## Cookies 
- [ ]  Test that no cookies are accepted from adn-ALLOWed requests:
  * Make sure ‘Activate debugging mode’ is set to true to view log info in the console   
  * Visit sites(nytimes for example) where one or more _3rd-party_ requests are adn-ALLOWed and note their domains
- [ ]  Test that outgoing cookies are always sent
- [ ]  Test that incoming cookies are not allowed from responses to Ad visits, by checking cookies before/after
(if only Channel ID cookies are allowed, it is ok for now) [TestCase](http://lab-lamp.scm.cityu.edu.hk/adntest/cookie-setting-ad.html)
* To check headers for ad visits, please go to developer tools of the browser -> Network -> click on a request -> select 'Headers'. You can also click on 'XHR' type to filter the requests.(For a more detailed network logging, you can check Chrome Net-Internals of the [tools](#tools) listed below.)Please notice that, sometimes there is a “CAUTION: provisional headers are shown” message when you check headers in the console. If you see this message, the headers shown are not reliable. Therefore it should not be considered as a reference when checking the headers during test release/ debugging. Check other requests or use [Chrome Net-Internals](#tools) instead.
------------------

## Check Ad Blockers
- [ ]  Install uBlock Origin
- [ ]  Remove and reinstall AdNauseam to trigger the first-run page 
- [ ]  check if there is a warning about other ad blockers on the first-run page,menu and vault
- [ ]  [chromium based only] click the 'disable' button on the warning message, it should lead to the extension page
- [ ]  [chromium based only] disable uBlock and check whether the message is gone in vault and menu. (If the page was opened, it need to be refreshed)
- [ ]  Test this for Adblock Plus/AdBlock/uBlock as well
- [ ]  Make sure that a warning message won't be triggered for uBlock Origin Extra (chromium based)
------------------

## Check Blocking
- [ ]  Check that the request from the following test page is blocked by adnauseam by using the uBlock logger 
[here](http://lab-lamp.scm.cityu.edu.hk/adntest/block.html)

------------------


## Check Redirect-rules

- [ ]  Check that the "redirect" and "redirect-rule" are properly working, comparing behaviour with uBlock Origin. Example of website with both types of rules [here](https://m.bild.de/###wt_ref=https%3A%2F%2Fwww.bild.de%2F&wt_t=1616698301531). For further information follow the discussion on this issue https://github.com/dhowe/AdNauseam/issues/1771#issuecomment-807294379

------------------

## Check New Features
### Strict Blocking   
- [ ]  Enable global strict blocking in settings, open the logger and go to sites such as nytimes. All blocking rules(including easyList) should be blocked(in red). 
- [ ]  Go to "My rules" and add `* doubleclick.net * strictBlock`; Commit the rule and make sure that nothing turns red in codeMIrror; Go to nytimes and make sure that requests from doubleclick.net are all blocked by easylist.
- [ ]  Go to "My rules" and add `nytimes.com * * strictBlock`; Commit the rule and make sure that nothing turns red in codeMIrror; Go to nytimes and make sure that blocking filters from easyList are triggered.
- [ ]  Go to "My rules" and add `nytimes.com * image strictBlock`; Commit the rule and make sure that nothing turns red in codeMIrror; Go to nytimes and make sure that blocking filters on images are triggered from easyList, but other types of requests are still allowed. 

------
## Check incognito/private browsing
   * In Chrome/Opera, go to the extension page and check "Allow in incognito" for AdNauseam, then hit command+shift+N to start testing
   * In Firefox, use command+shift+P to open a private window
- [ ]  Test that by default ads are collected in incognito/private-browsing windows:    
### Private Mode
- [ ]  [Opera Only] For Private Mode to work correctly, make sure that in opera's manifest file, "incognito" is always set to "spanning". This is the default value in chrome.
- [ ]  Enable Private Mode and open one incognito/private window
- [ ]  Close the private window
- [ ]  Open adVault. The ad content should have been removed, while an private ad place holder is rendered, leaving a count for total ads collected and the ad network in the statistics panel.
- [ ]  In a normal window, open the menu and check that the collected ad(in private mode) is not rendered now.
- [ ]  Disable Private Mode, double check that private ads are normally displayed in menu and vault.
------------------

## Check Element-picker Tool
- [ ]  Go to some web page with a visible ad, then right-click, select 'Block element', create a rule to hide the element

------------------

## Test Update
- [ ]  Test Manual Update by clicking "Update Now" in settings page
  1.  Rebuild AdNauseam
  1.  Click "Update Now" in Settings Page and check 
    - [ ]  All out-dated filters are updated (background.html console)
    - [ ]  The total number of rules of Adnauseam has been updated
    - [ ]  The rules are functioning when test on a webpage.
- [ ]  Test Auto Update
 1.  Go to "advanced-settings.html" and modify "autoUpdateAssetFetchPeriod", "autoUpdatePeriod" to 1, and "autoUpdateDelayAfterLaunch" to 0.
 1.  Open the background.html page to check the logging message in the network section
 1.  Wait till the autoUpdate triggers and check whether there is any error message in the console
- [ ]  Make sure that both buttons "Update Now" and "Purge All Caches" toggle correctly
- [ ]  Test "Update" button for adnauseam.txt on "filterlists" page
- [ ]  Test "Update" button for Eff list on "whitelists" page

After going through all the tests, check:
[How do I create a new release](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#how-do-i-create-a-new-release) and 
[After new release](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#after-new-release)
(make sure to update http://rednoise.org/adnauseam/updates.xml for chrome)

------------------
&nbsp;

## Tools 
  * [Live HTTP Headers (Firefox)](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers-clone/) 
  * Chrome Net-Internals   chrome://net-internals/#events


***


## Tests for Firefox Android / Basic Tests

### Interface
&nbsp;&nbsp;&nbsp;&nbsp;<b>First-Run</b>
- Remove and reinstall AdNauseam to trigger this page 
- [ ]  Test selection of various options (click-ads, block-malware, hide-ads, DNT)
- [ ]  Check the layout

&nbsp;&nbsp;&nbsp;&nbsp;<b>Menu</b>
- [ ]  Check all buttons and information (including number of Ads and $$ cost, hidden if no ads)
- [ ]  Check the layout when adnauseam is paused
- [ ]  Check there is no text overlap in the menu for text ads

&nbsp;&nbsp;&nbsp;&nbsp;<b>Vault</b>
- [ ]  Verify loading animation, and centering/scaling of Ads on load
- [ ]  Zoom in/out using gesture and buttons in top-left corner 
- [ ]  Check function/layout of Inspector (for both image and text ads)
- [ ]  Check correct function of date-filter slider at bottom
- [ ]  Test import/export/clear functions

&nbsp;&nbsp;&nbsp;&nbsp;<b>Dashboard</b>
- [ ]  Check layout of buttons, check-boxes, and links in each tab
- [ ]  Test backup/restore/reset settings functions

------------------

### Basic Functions
- [ ]  Blocking [here](http://lab-lamp.scm.cityu.edu.hk/adntest/block.html)
- [ ]  Hiding [here](http://lab-lamp.scm.cityu.edu.hk/adntest/simple.html)
- [ ]  Clicking
- [ ]  Check DNT headers

------------------

### Test Update
- [ ]  Test Manual Update by clicking "Update Now" in settings page
  1.  Change the local uAsset and run tools/update-ublock0.sh to generate a new checksum
  1.  Rebuild AdNauseam
  1.  Click "Update Now" in Settings Page and check 
    - All out-dated filters are updated (background.html console)
    - The total rules of adnauseam has been updated
    - The rules are functioning when test on webpage.
- [ ]  Test "Update" button for adnauseam.txt

After going through all the tests, check:
[How do I create a new release](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#how-do-i-create-a-new-release) and 
[After new release](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#after-new-release)
(make sure to update http://rednoise.org/adnauseam/updates.xml for chrome)