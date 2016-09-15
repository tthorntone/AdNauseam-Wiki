Steps to test a new release candidate on Firefox, Chrome, Opera:


* Check the AdNauseam and uBlock version numbers   
  To check the AdNauseam version number, please refer to AdNauseam/manifest.json   
  To check the uBlock version number, please refer to AdNauseam/platform/chromium/manifest.json
* Test various options on the first-run page (click-ads, block-malware, hide-ads, DNT)

###Ads Testing
* Test a set of pages, and make sure that ads are being captured and visited   
  Image-ads
  - Go to Facebook/Youtube/Amazon... to test image-ads
  Text-ads
  - Go to Google/Ask/Yahoo/Bing/Duckduckgo to search for keyword such as "credit card" or "loan"
*  Test that ads from DNT-respecting sites (https://www.eff.org/files/effdntlist.txt) are not hidden or clicked
*  Test ad parsing from within dynamically-created iframes (New York Times, Pirate Bay)                       
*  Test that no ads are collected in incognito/private-browsing windows
  

###Functions Testing
* Check general function of menu and vault  
   Menu(the popup window triggered by clicking AdNauseam logo from browser toolbar )
   - Check all the buttons and information
   - Hover the ad images in the menu, check whether the zooming function works properly
   Vault  
   -Zooming in and out using mouse wheel and the buttons in the top-left corner 
   -Clicking collected images and text ads to see if the information and layout are correct   
   -Check the date filter slider at the bottom of the vault
   -Check if the AdNauseam logo in the bottom-right corner links correctly to the AdNauseam homepage  
* Test import/export/clear ads functions(Both in Vault and in Settings)
* Test the content, buttons, check boxes and links in Settings

### AdNauseam-advanced
*  test the header-options (cookies, referer, user-agent )
*  test that the DNT header is being sent correctly when enabled
*  test that no cookies are accepted from [ALLOW]ed requests

(Pending)


