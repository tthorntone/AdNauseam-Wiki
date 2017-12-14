
_First make sure that you are working with the correct commit (check the hash) or installed release, then perform each test on Firefox, Chrome and Opera

**Test set**  
[Full test set](https://github.com/dhowe/AdNauseam/wiki/Testing-New-Release-Candidates#interface)  
[Basic / Android test set](https://github.com/dhowe/AdNauseam/wiki/Testing-New-Release-Candidates#tests-for-firefox-android--basic-tests)  

## Interface

&nbsp;&nbsp;&nbsp;&nbsp;<b>First-Run</b>
- Remove and reinstall AdNauseam to trigger this page 
- Test selection of various options (click-ads, block-malware, hide-ads, DNT)
- Verify that the DNT option is visible _only_ when clicking OR hiding is enabled
- Test that toggling the DNT option changes _both_ DNT options in Settings
- Check the links on first-run page
- Check the version number at left-bottom corner

&nbsp;&nbsp;&nbsp;&nbsp;<b>Menu</b>
- Check all buttons and information (including number of Ads and $$ cost, hidden if no ads)
- Hover over Ad images and check zooming
- Check that menu is correctly updated after ad-visiting
- Check ad-visiting animation
- Check there is no text overlap in the menu for text ads
- Check AdNauseam version number(in uBlock menu)
- Menu shows "AdNauseam is paused on current pages" when AdNauseam is paused, and make sure that the layout is correct.
- Check that the Adnauseam logo links to homepage

&nbsp;&nbsp;&nbsp;&nbsp;<b>Vault</b>
- Verify loading animation, and centering/scaling of Ads on load
- Zoom in/out using mouse wheel and buttons in top-left corner 
- Check function/layout of Inspector (for both image and text ads)
- Check correct function of date-filter slider at bottom
- Check that AdNauseam logo in the bottom-right corner links correctly to homepage  
- Check correct calculation of ad cost
- Test import/export/clear functions
- Right click on an ad and delete it. Refresh the page and check that it is successfully deleted

&nbsp;&nbsp;&nbsp;&nbsp;<b>Dashboard</b>
- Check 2 version numbers in 'About' page (links.html)
- Check layout of buttons, check-boxes, and links in each tab
- Test that all (i)nfo buttons lead to correct FAQ pages in each tab
- On settings tab (options.html) check that when clicking or hiding are disabled, then all of their sub-items are also disabled
- Test import/export/clear ads functions
- Test whitelist

&nbsp;&nbsp;&nbsp;&nbsp;<b>Toolbar Icon</b>
- Check that the icon in the toolbar is in purple when AdNauseam is active
- Check that the icon in the toolbar is in grey when AdNauseam is disabled
- Check that the icon in the toolbar is in green when on DNT pages
- Icon should animate each time an Ad is clicked (>= v3.1)
- double check that the badge number is correctly updated

&nbsp;&nbsp;&nbsp;&nbsp;<b>Notifications</b>
- Check that disabling hiding, clicking, or blocking on the first-run generates a notification warning at the top of the dashboard (all tabs), menu, and vault page (after first-run is closed or 'ok' is clicked). 
- Check that disabling hiding, clicking, or blocking on the dashboard/options page generates a notification warning at the top of the dashboard(all tabs), menu, and vault page. 
- Check that disabling EasyList/AdNauseam filters on the dashboard/3p-filters page generates a notification warning at the top of the dashboard(all tabs), menu, and vault page. 
- Check that clicking 'reactivate' on a notification warning at the top of the dashboard, menu, or vault pages causes the visual state to change correctly, and the setting in question to be updated correctly. 
- Check that the vault (if open) is updated when notifications change
- Check that the dashboard (if open) is updated when notifications change
- Dashboard::settings (options.html) Check that page refreshes correctly when a notification is 'reactivated'
- Dashboard::3rd-Party (3p-filters.html) Check that page refreshes correctly when a list-notification is 'reactivated'

------------------

## Ad Hiding/Parsing
* Test a set of pages, and make sure that ads are being captured and visited   
  * ImageAds: visit Facebook/Youtube/Amazon... and verify ads are hidden and appear in menu
  * TextAds: visit Google/Ask/Yahoo/Bing/DuckDuckGo to search for keywords such as "credit card" or "loan"
*  Test Ad-parsing from within dynamically-created iFrames: hidden and collected   
  Test cases:
[Chrome](http://lab-lamp.scm.cityu.edu.hk/adntest/dynamic_iframe.html) | 
[Firefox](http://lab-lamp.scm.cityu.edu.hk/adntest/dynamic_iframe_firefox.html)
*  Test Ad-parsing from cosmetically-filtered iFrames: hidden but not collected (without cosmetic filters for any contained elements)  [here](http://lab-lamp.scm.cityu.edu.hk/adntest/iframe-cosm.html)                       
*  Test that no Ads are collected in incognito/private-browsing windows:    
   * In Chrome/Opera, go to the extension page and check "Allow in incognito" for AdNauseam, then hit command+shift+N to start testing
   * In Firefox, use command+shift+P to open a private window

------------------
## Ad clicking status (Menu and Vault)

**Visual**  
Check whether the clicking status of an ad is correctly indicated by the color of its border:

- Blue - Pending
- Purple - Clicked
- Red - Failed
- Green - DNT

**Text**

- If an ad is not visited because of the clicking frequency, the ad should be marked as "SKIPPED: Click Frequency "
- If an ad is not visited because the user has already clicked it, the ad should be marked as "SKIPPED: Clicked by user "
- When an ad is collected from a dnt site (Ex:duckduckgo), the ad should be marked as "SKIPPED: DNT Allowed" ("Allowed via Do Not Track Policy" in vault)
- When clicking is disabled, all ads that are not "visited" or "failed" should be marked as "SKIPPED: Clicking Disabled:"

------------------
## DoNotTrack (DNT)
DNT: Go to a DNT page (Ex: duckduckgo.com) and check the following items:

&nbsp;&nbsp;&nbsp;&nbsp;<b>Headers/Cookies</b>

&nbsp;&nbsp;&nbsp;&nbsp;To check ad visits headers, click on request in browser's network panel, select 'Headers'
&nbsp;&nbsp;&nbsp;&nbsp;(For a more detailed network logging, you can check Chrome Net-Internals of the [tools](#tools) listed below.)
- DNT-header is being sent correctly for ALL requests (including Ad visits) if either disableClickingForDNT and disableHidingForDNT are enabled (and vice versa) 
- DNT Cookie handling (v3.1 and later)

&nbsp;&nbsp;&nbsp;&nbsp;<b>Hiding/Clicking</b>
- Ads are visible when domain is 1st-party if disableHidingForDNT is checked
- Requests are not blocked when domain is 1st-party iff disableHidingForDNT is checked
- Requests are not blocked when domain is 3rd-party iff disableHidingForDNT is checked([here](http://lab-lamp.scm.cityu.edu.hk/adntest/effTestPage.html))
- No clicking when ad domain is on list iff disableClickingForDNT is checked (especially for 3rd-party)
- If both DNT options are disabled, then hiding, blocking, visiting occur again as usual(both first party and 3rd-party)

&nbsp;&nbsp;&nbsp;&nbsp;<b>Interface</b>
- DNT list at top of whitelist.html is checked when either DNT option is checked, otherwise unchecked
- Check that changing the two DNT settings will triggger DNT notifications with corresponding messages to the menu  
- Check the layout of each DNT notification("?" should be in the middle, 'settings' button appears on hover)  

&nbsp;&nbsp;&nbsp;&nbsp;<i>[Test Page for 3rd-party DNT](http://lab-lamp.scm.cityu.edu.hk/adntest/effTestPage.html)</i>

------------------

## Cookies 
* Test that no cookies are accepted from adn-ALLOWed requests: [Test Case](http://lab-lamp.scm.cityu.edu.hk/adntest/incomingCookies.html) 
  - Make sure ‘Activate debugging mode’ is set to true to view log info in the console   
  - Visit sites where one or more _3rd-party_ requests are adn-ALLOWed and note their domains
* Verify that no cookies are accepted from these domains: first by checking cookies before/after in the browser, then verify using one of the [tools](#tools) listed below (look for 'set-cookies' in response Header)

------------------

## Ad Visits 
To check headers for ad visits, please go to developer tools of the browser -> Network -> click on a request -> select 'Headers'. You can also click on 'XHR' type to filter the requests.
(For a more detailed network logging, you can check Chrome Net-Internals of the [tools](#tools) listed below.)

- Test that outgoing cookies are always sent
- Test that incoming cookies are not allowed from responses to Ad visits, by checking cookies before/after
(if only Channel ID cookies are allowed, it is ok for now) [TestCase](http://lab-lamp.scm.cityu.edu.hk/adntest/cookie-setting-ad.html)
- Please notice that, sometimes there is a “CAUTION: provisional headers are shown” message when you check headers in the console. If you see this message, the headers shown are not reliable. Therefore it should not be considered as a reference when checking the headers during test release/ debugging. Check other requests or use [Chrome Net-Internals](#tools) instead.
- Test different click probabilities
------------------

## Check Ad Blockers
- Install uBlock Origin
- Remove and reinstall AdNauseam to trigger the first-run page 
- check if there is a warning about other ad blockers on first-run page,menu and vault
- click 'disable' button on the warning message, it should lead to the extension page
- disable uBlock and check whether the message is gone in vault and menu.(If the page was opened, it need to be refreshed)

  _Test this for Adblock Plus/AdBlock/uBlock as well

------------------

## Check Blocking
- Check that the request from the following test page is blocked by adnauseam by using the uBlock logger 
[here](http://lab-lamp.scm.cityu.edu.hk/adntest/block.html)

------------------

## Check Element-picker Tool
- Go to some web page with a visible ad, then right-click, select 'Block element', create a rule to hide the element

------------------

## Test Update
- Test Manual Update by clicking "Update Now" in settings page
  1.  Change the local uAsset and run tools/update-ublock0.sh to generate a new checksum
  1.  Rebuild AdNauseam
  1.  Click "Update Now" in Settings Page and check 
    - All out-dated filters are updated (background.html console)
    - The total rules of adnauseam has been updated
    - The rules are functioning when test on webpage.
- Test Auto Update (This need to be tested from unpacked extension)
 Check the same thing above with a different procedure:
 1.  Go to start.js and change this line : "µb.scheduleAssetUpdater(µb.userSettings.autoUpdate ? 7 * 60 * 1000 : 0);" to "µb.scheduleAssetUpdater(µb.userSettings.autoUpdate ? 10 * 1000 : 0);"
 1.  Go to background.js and change autoUpdateAssetFetchPeriod to 1
 1.  Rebuild AdNauseam
 1.  Delete and reinstall AdNauseam
 1.  Activate debugging mode and open the background.html page to check the logging message in the console
 1.  Wait till the autoUpdate triggers and check whether there is any error message in the console
 1.  Check the same things as above
- Test "Update" button for adnauseam.txt

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
- Test selection of various options (click-ads, block-malware, hide-ads, DNT)
- Check the layout

&nbsp;&nbsp;&nbsp;&nbsp;<b>Menu</b>
- Check all buttons and information (including number of Ads and $$ cost, hidden if no ads)
- Check the layout when adnauseam is paused
- Check there is no text overlap in the menu for text ads

&nbsp;&nbsp;&nbsp;&nbsp;<b>Vault</b>
- Verify loading animation, and centering/scaling of Ads on load
- Zoom in/out using gesture and buttons in top-left corner 
- Check function/layout of Inspector (for both image and text ads)
- Check correct function of date-filter slider at bottom
- Test import/export/clear functions

&nbsp;&nbsp;&nbsp;&nbsp;<b>Dashboard</b>
- Check layout of buttons, check-boxes, and links in each tab
- Test import/export/clear ads functions

------------------

### Basic Functions
- Blocking [here](http://lab-lamp.scm.cityu.edu.hk/adntest/block.html)
- Hiding [here](http://lab-lamp.scm.cityu.edu.hk/adntest/simple.html)
- Clicking
- Check DNT headers

------------------

### Test Update
- Test Manual Update by clicking "Update Now" in settings page
  1.  Change the local uAsset and run tools/update-ublock0.sh to generate a new checksum
  1.  Rebuild AdNauseam
  1.  Click "Update Now" in Settings Page and check 
    - All out-dated filters are updated (background.html console)
    - The total rules of adnauseam has been updated
    - The rules are functioning when test on webpage.
- Test "Update" button for adnauseam.txt
