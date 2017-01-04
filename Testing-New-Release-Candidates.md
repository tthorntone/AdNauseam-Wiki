
_First make sure that you are working with the correct commit (check the hash) or installed release, then perform each test on Chrome, Firefox, and Opera_

## Interface

### First-Run &nbsp;
- Remove and reinstall AdNauseam to trigger this page 
- Test selection of various options (click-ads, block-malware, hide-ads, DNT)
- Verify that the DNT option is visible _only_ when clicking OR hiding is enabled
- Test that toggling the DNT option changes _both_ DNT options in Settings
- Check the links on first-run page
- Check the version number at left-bottom corner

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
To check headers for ad visits, please go to developer tools of the browser -> Network -> click on a request -> select 'Headers'. Or you can try Live HTTP Headers in [tools](#tools) below.

- DNT-header is being sent correctly for ALL requests (including Ad visits) if either disableClickingForDNT and disableHidingForDNT are enabled (and vice versa) 
- That DNT list at top of whitelist.html is checked when either DNT option is checked
- That DNT domains appear in whitelist.html entries when either DNT option is checked
- That DNT domains are removed from whitelist entries when when neither DNT option is checked 
 

&nbsp;

- Ads are visible when domain is 1st-party iff disableHidingForDNT is checked
- Requests are not blocked when domain is 1st-party iff disableHidingForDNT is checked
- Requests are not blocked when domain is 3rd-party iff disableHidingForDNT is checked

&nbsp;

- No clicking when ad domain is on list iff disableClickingForDNT is checked (especially for 3rd-party)
- Enabling/disabling of DNT firewall on all permutations of first-run page options 
- If both DNT options are disabled, then hiding, blocking, visiting occur again as usual
- DNT Cookie handling (v3.1 and later)

------------------

## Cookies 
* Test that no cookies are accepted from ALLOWed requests:  
  - Make sure ‘Activate debugging mode’ is set to true to view log info in the console   
  - Visit sites where one or more _3rd-party_ requests are ALLOWed and note their domains
  - Verify that no cookies are accepted from these domains: first by checking cookies before/after in the browser, then verify using one of the [tools](#tools) listed below('set-cookies' in response Header)

------------------

## Ad Visits 
To check headers for ad visits, please go to developer tools of the browser -> Network -> click on a request -> select 'Headers'. You can also click on 'XHR' type to filter the requests.
- Test that the correct 'referer' header is sent on Ad visits depending on the setting (ad.pageUrl when disabled, or none when enabled) 
- Test that the correct 'user-agent' header is sent on Ad visits depending on the setting (the usual user-agent when disabled, or default when enabled)  
- Test that outgoing cookies are sent on Ad visits depending on the setting (the usual cookies when disabled, or none when enabled)  
- Test that incoming cookies are never allowed from responses to Ad visits, by checking cookies before/after
(Currently if only Channel ID cookies are allowed, it is ok)
------------------

## Check Ad Blockers
- Install uBlock
- Remove and reinstall AdNauseam to trigger the first-run page 
- check if there is a warning about other ad blockers on first-run page,menu and vault
- click 'disable' button on the warning message, it should lead to the extension page
- disable uBlock and check whether the message is gone in vault and menu.(If the page was opened, it need to be refreshed)

Test this for only Ad Block Plus installed, uBlock/uBlock Origin and Ad Block Plus both installed.
------------------
&nbsp;

## Tools 
  * [Live HTTP Headers (Firefox)](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers-clone/)   