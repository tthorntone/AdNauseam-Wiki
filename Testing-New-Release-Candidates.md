_Note: perform each test on Chrome, Firefox, and Opera_

### Interface

* First-run &nbsp; (remove and reinstall AdNauseam to trigger)
  - Test selection of various options (click-ads, block-malware, hide-ads, DNT)
  - Test that DNT is only visible when clicking OR hiding is enabled

* Menu 
   - Check all buttons and information (including number of ads and $$ cost)
   - Hover over ad images and check zooming
   - Check the uBlock version number

* Vault
   - Zoom in/out using mouse wheel and buttons in top-left corner 
   - Check inspector (for both image and text ads)
   - Check date filter slider at bottom of page
   - Check that AdNauseam logo in the bottom-right corner links correctly to homepage  
   - Check correct calculation of ad cost
   - Test import/export/clear functions

### Ad Hiding/Parsing
* Test a set of pages, and make sure that ads are being captured and visited   
  * ImageAds: visit Facebook/Youtube/Amazon... and verify ads are hidden and appear in menu
  * TextAds: visit Google/Ask/Yahoo/Bing/DuckDuckGo to search for keywords such as "credit card" or "loan"
*  Test Ad-parsing from within dynamically-created iframes [here](http://rednoise.org/adntest/dynamic_iframe.html)                       
*  Test that no Ads are collected in incognito/private-browsing windows    
   * In Chrome/Opera, go to the extension page and check "Allow in incognito" for AdNauseam, then hit command+shift+N to start testing
   * In Firefox, use command+shift+P to open a private window

### Settings
* Check version number in 'About' page
* Check layout of buttons, check-boxes, and links in each tab
* Test that all (i)nfo buttons lead to correct FAQ pages in each tab
* Test import/export/clear ads functions

### DoNotTrack (DNT)
*  Test that the DNT header is being sent correctly when enabled (and vice versa)
*  Test that ads from [DNT-respecting sites](https://www.eff.org/files/effdntlist.txt) are not hidden and/or clicked, when each of the 2 DNT settings is enabled, and that they ARE hidden and/or clicked when each setting is disabled

### Cookies 
* Test that the browser's 'no 3rd-party cookies' option is enabled after install
* Test that the browser's 'no 3rd-party cookies' can be disabled
* Test that no cookies are accepted from ALLOWed requests:  
  1. Go to cookie options in Chrome:Settings and check that "Block third-party cookies" is marked as controlled by AdNauseam. Then click the disable button.   
  1. Make sure the `logBlocks` flag in core.js is set to true to view blocking data in the   
  1. Visit sites where one ore more _3rd-party_ requests are ALLOWed and note their domains
  1. Verify that no cookies are accepted from these domains, using one of the [tools](#tools) listed below


&nbsp;

(More to come)

&nbsp;

### Tools
  * [Live HTTP Headers in Chrome](https://chrome.google.com/webstore/detail/live-http-headers/iaiioopjkcekapmldfgbebdclcnpgnlo?hl=en)    
  * [Live HTTP Headers in Firefox](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers-clone/)   
  * [Charles: a cross-platform application for web debugging](https://www.charlesproxy.com/latest-release/download.do) 