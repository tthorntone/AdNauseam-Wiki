Steps to test a new release candidate on Firefox, Chrome, Opera:

General

* check the AdNauseam and uBlock version numbers
  To check the AdNauseam version number, please refer to AdNauseam/manifest.json
  To check the uBlock version number, please refer to AdNauseam/platform/chromium/manifest.json

Functions Testing
* test various options on the first-run page (click-ads, block-malware, hide-ads, DNT)
* test import/export/clear functions(Both in Settings and in Vault)
* check general function of menu and vault
 
* test a set of pages, and make sure that ads are being captured and visited:(image-ads and text-ads)
*  test that no ads are collected in incognito/private-browsing windows
*  test that ads from DNT-respecting sites (from EFF list) are not hidden or clicked         https://www.eff.org/files/effdntlist.txt
*  test ad parsing from within dynamically-created iframes  


*  test the header-options (cookies, referer, user-agent )
*  test that the DNT header is being sent correctly when enabled
*  test that no cookies are accepted from [ALLOW]ed requests

(Pending)


