
_First make sure that you are working with the correct commit (check the hash) or installed release, then perform each test on Chrome, Firefox, and Opera_

## Interface

### First-Run &nbsp;
- Remove and reinstall AdNauseam to trigger this page 
- Test selection of various options (click-ads, block-malware, hide-ads, DNT)
- Verify that the DNT option is visible _only_ when clicking OR hiding is enabled
- Test that toggling the DNT option changes _both_ DNT options in Settings

### Menu 
- Check all buttons and information (including number of Ads and $$ cost)
- Hover over Ad images and check zooming
- Check the uBlock version number(in uBlock menu)

### Vault
- Verify loading animation, and centering/scaling of Ads on load
- Zoom in/out using mouse wheel and buttons in top-left corner 
- Check function/layout of inspector (for both image and text ads)
- Check correct function date filter slider at bottom of page
- Check that AdNauseam logo in the bottom-right corner links correctly to homepage  
- Check correct calculation of ad cost (and updates according to date-filter)
- Test import/export/clear functions

### Notifications
- Check that disabling hiding, clicking, or blocking on the first-run generates a notification warning at the top of the dashboard (all tabs), menu, and vault page (after first-run is closed or 'ok' is clicked). 
- Check that disabling hiding, clicking, or blocking on the dashboard/options page generates a notification warning at the top of the dashboard(all tabs), menu, and vault page. 
- Check that disabling EasyList on the dashboard/3p-filters page generates a notification warning at the top of the dashboard(all tabs), menu, and vault page. 
- Check that clicking 'reactivate' on a notification warning at the top of the dashboard, menu, or vault pages causes the visual state to change correctly, and the setting in question to be updated correctly. 
- Check that the vault (if open) is updated when notifications change
- Check that the dashboard (if open) is updated when notifications change
- Dashboard::settings (options.html) Check that page refreshes correctly when a notification is 'reactivated'
- Dashboard::3rd-Party (3p-filters.html) Check that page refreshes correctly when a list-notification is 'reactivated'

&nbsp;

------------------

## Ad Hiding/Parsing
* Test a set of pages, and make sure that ads are being captured and visited   
  * ImageAds: visit Facebook/Youtube/Amazon... and verify ads are hidden and appear in menu
  * TextAds: visit Google/Ask/Yahoo/Bing/DuckDuckGo to search for keywords such as "credit card" or "loan"
*  Test Ad-parsing from within dynamically-created iframes [here](http://rednoise.org/adntest/dynamic_iframe.html)
*  Test Ad-parsing from cosmetically filtered iframes (without cosmetic filters for any contained elements)  [here](http://rednoise.org/adntest/iframe-cosm.html)                       
*  Test that no Ads are collected in incognito/private-browsing windows    
   * In Chrome/Opera, go to the extension page and check "Allow in incognito" for AdNauseam, then hit command+shift+N to start testing
   * In Firefox, use command+shift+P to open a private window

------------------

## Dashboard
- Check 2 version numbers in 'About' page (links.html)
- Check layout of buttons, check-boxes, and links in each tab
- Test that all (i)nfo buttons lead to correct FAQ pages in each tab
- On settings tab (options.html) check that when clicking or hiding are disabled, then all of their sub-items are also disabled
- Test import/export/clear ads functions

------------------

## DoNotTrack (DNT)
-  Test that the EFF's DNT list on settings/whitelist.html is disabled whenever both disableClickingForDNT and disableHidingForDNT are disabled, and is otherwise enabled
-  Test that the DNT header is being sent correctly for all requests (including Ad visits) if either disableClickingForDNT and disableHidingForDNT are enabled (and vice versa)
-  Test that ads from [DNT-respecting sites](https://www.eff.org/files/effdntlist.txt) are not hidden and/or clicked, when each of the 2 DNT settings is enabled, and that they ARE hidden and/or clicked when each setting is disabled

------------------

## Cookies 
* Test that the browser's 'no 3rd-party cookies' option is enabled after install
* Test that the browser's 'no 3rd-party cookies' can be disabled
* Test that no cookies are accepted from ALLOWed requests:  
  - Go to cookie options in Chrome:Settings and check that "Block third-party cookies" is marked as controlled by AdNauseam. Then click the disable button.   
  - Make sure the `netLogging` flag in core.js is set to true to view log info in the console   
  - Visit sites where one or more _3rd-party_ requests are ALLOWed and note their domains
  - Verify that no cookies are accepted from these domains, using one of the [tools](#tools) listed below, or by checking cookies before/after

------------------

## Ad Visits 
- Test that the correct 'referer' header is sent on Ad visits depending on the setting (ad.pageUrl when disabled, or none when enabled) 
- Test that the correct 'user-agent' header is sent on Ad visits depending on the setting (the usual user-agent when disabled, or none when enabled)  
- Test that outgoing cookies are sent on Ad visits depending on the setting (the usual cookies when disabled, or none when enabled)  
- Test that incoming cookies are never allowed from responses to Ad visits, using one of the [tools](#tools) listed below, or by checking cookies before/after

------------------

&nbsp;

(More to come)

--------------------

&nbsp;

## Tools
  * [Live HTTP Headers (Chrome)](https://chrome.google.com/webstore/detail/live-http-headers/iaiioopjkcekapmldfgbebdclcnpgnlo?hl=en)    
  * [Live HTTP Headers (Firefox)](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers-clone/)   
  * [Charles (cross-platform)](https://www.charlesproxy.com/latest-release/download.do) 