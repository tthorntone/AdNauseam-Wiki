_Note: perform each test on Chrome, Firefox, and Opera_

### Interface

#### First-Run &nbsp;
- Remove and reinstall AdNauseam to trigger this page 
- Test selection of various options (click-ads, block-malware, hide-ads, DNT)
- Verify that the DNT option is visible _only_ when clicking OR hiding is enabled
- Test that toggling the DNT option changes _both_ DNT options in Settings

#### Menu 
- Check all buttons and information (including number of Ads and $$ cost)
- Hover over Ad images and check zooming
- Check the uBlock version number

#### Vault
- Verify loading animation, and centering/scaling of Ads on load
- Zoom in/out using mouse wheel and buttons in top-left corner 
- Check function/layout of inspector (for both image and text ads)
- Check correct function date filter slider at bottom of page
- Check that AdNauseam logo in the bottom-right corner links correctly to homepage  
   - Check correct calculation of ad cost (and updates according to date-filter)
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
  - Go to cookie options in Chrome:Settings and check that "Block third-party cookies" is marked as controlled by AdNauseam. Then click the disable button.   
  - Make sure the `logBlocks` flag in core.js is set to true to view blocking data in the   
  - Visit sites where one ore more _3rd-party_ requests are ALLOWed and note their domains
  - Verify that no cookies are accepted from these domains, using one of the [tools](#tools) listed below


&nbsp;

(More to come)

&nbsp;

### Tools
  * [Live HTTP Headers in Chrome](https://chrome.google.com/webstore/detail/live-http-headers/iaiioopjkcekapmldfgbebdclcnpgnlo?hl=en)    
  * [Live HTTP Headers in Firefox](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers-clone/)   
  * [Charles: a cross-platform application for web debugging](https://www.charlesproxy.com/latest-release/download.do) 