## Testing builds and releases on Firefox, Chrome, Opera:
  
### Interface

* FirstRun (remove and reinstall adn)
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
* Test advanced settings:
  * For advanced setting, use the following tools:
    * [Live HTTP Headers in Chrome](https://chrome.google.com/webstore/detail/live-http-headers/iaiioopjkcekapmldfgbebdclcnpgnlo?hl=en)    
    * [Live HTTP Headers in Firefox](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers-clone/)   
    * [Charles: a cross-platform application for web debugging](https://www.charlesproxy.com/latest-release/download.do) 
  *  Test each header-option, enabled and disabled (outgoing cookies, referer, & user-agent, and incoming cookies)
  *  Test that the DNT header is being sent correctly when enabled
  *  Test that no cookies are accepted from [ALLOW]ed requests   
   1. Go to Chrome:Settings and search for Cookies, Open the Cookies Setting and you will find an extension icon next to the choice "Block third-party cookies". When you Click that icon, it will tell you that this setting is controlled by AdNauseam. Click the disable button.   
   2. Then, Test in websites where AdNauseam is allowing anything that is not allowed by uBlock.(Ex:Youtube, New York Times)   
     Make sure no cookies is accepted by using any tools suggested above.

### DoNotTrack (DNT)
*  Test that ads from [DNT-respecting sites](https://www.eff.org/files/effdntlist.txt) are not hidden or clicked, when each of the 2 DNT settings is enabled, and that they ARE hidden and clicked when each setting is disabled

### Cookies 
* Test that the browser's 'no 3rd-party cookies' option is enabled after install
* Test that the browser's 'no 3rd-party cookies' can be disabled

(Pending)

