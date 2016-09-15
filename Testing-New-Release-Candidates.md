### Steps to test a new build or release candidate on Firefox, Chrome, Opera:

* Check the AdNauseam and uBlock version numbers in the interface (on the settings page, and on the uBlock menu page)
* Test various options on the first-run page (click-ads, block-malware, hide-ads, DNT)

### Ad Testing
* Test a set of pages, and make sure that ads are being captured and visited   
  ** Image-ads: visit Facebook/Youtube/Amazon... and verify ads are hidden and appear in menu
  ** Text-ads: visit Google/Ask/Yahoo/Bing/Duckduckgo to search for keywords such as "credit card" or "loan"
*  Test that ads from [DNT-respecting sites](https://www.eff.org/files/effdntlist.txt) are not hidden or clicked, when each DNT setting is enabled, and that they are hidden and clicked when disabled
*  Test ad-parsing from within dynamically-created iframes [here](http://rednoise.org/adntest/dynamic_iframe.html)                       
*  Test that no ads are collected in incognito/private-browsing windows    
   * In Chrome and Opera, first go to the extension page and check "Allow in incognito"/"Allow in private mode" for AdNauseam, then hit command+shift+N to start testing.   
   *In Firefox, use command+shift+P to open the private window.
  
### Function Testing
* Check general function of Menu 
   (the popup window triggered by clicking AdNauseam logo from browser toolbar )
   - Check all the buttons and information (including ad cost)
   - Hover the ad images in the menu, check whether the zooming function works properly
* Check general function of Vault
   - Zooming in and out using mouse wheel and the buttons in the top-left corner 
   - Clicking collected images and text ads to see if the information and layout are correct   
   - Check the date filter slider at the bottom of the vault
   - Check if the AdNauseam logo in the bottom-right corner links correctly to the AdNauseam homepage  
   - Check correct calculation of ad cost
* Test import/export/clear ads functions (both in Vault and in Settings)
* Test the content, buttons, check boxes and links in Settings

### AdNauseam-advanced (in Settings)
Tools to use:   
[Live HTTP Headers in Chrome](https://chrome.google.com/webstore/detail/live-http-headers/iaiioopjkcekapmldfgbebdclcnpgnlo?hl=en)    
[Live HTTP Headers in Firefox](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers-clone/)   
[Charles: a crossplatform application for web debugging](https://www.charlesproxy.com/latest-release/download.do) 

*  Test each header-option, enabled and disabled (outgoing cookies, referer, & user-agent, and incoming cookies)
*  Test that the DNT header is being sent correctly when enabled
*  Test that no cookies are accepted from [ALLOW]ed requests   
   1.Go to Chrome:Settings and search for Cookies, Open the Cookies Setting and you will find an extension icon next to the choice "Block third-party cookies". When you Click that icon, it will tell you that this setting is controlled by AdNauseam. Click the disable button.   
   2.Then, Test in websites where AdNauseam is allowing anything that is not allowed by uBlock.(Ex:Youtube, New York Times)   
     Make sure no cookies is accepted by using any tools suggested above.


(Pending)

