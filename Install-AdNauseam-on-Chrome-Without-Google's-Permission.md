[Google has banned AdNauseam](https://adnauseam.io/free-adnauseam.html) from its web store and have left users with no access to their data. Follow these instructions to install it anyway.

## Back up your data

_If you're a new AdNauseam user, or don't care about your saved ads, jump to [Installation](#install-adnauseam)_

1. Click on the AdNauseam icon to open the AdNauseam menu
2. Click the ``SETTINGS`` button at the bottom of the menu
3. Scroll down to the bottom of the page and click ``EXPORT ADS``

## Install AdNauseam

_The following instructions are for Google Chrome/Chromium ONLY. For other chromium-based browsers simply download the latest [.CRX file](https://github.com/dhowe/AdNauseam/releases/latest), open the extension page and drag into your browser window._

#### Manual Install in Developer Mode
1. Download the most latest adnauseam.chromium.zip file from our [releases page](https://github.com/dhowe/AdNauseam/releases/latest) (make sure to download the _chromium.zip_ file!)
2. Extract the zip file to a folder somewhere that it can remain  
**Warning: Do not delete this folder after the install; Chrome will disable AdNauseam if this folder is not in the expected location**

3. In your Chrome Browser menu, click Windows > Extensions or type chrome://extensions/ in the address bar  
4. Check the Developer mode checkbox  
5. Click the Load unpacked extension button (see image) and navigate to the folder you downloaded in step 1  
6. If you have previously exported your ads, you can retrieve them now  

<br>

*&nbsp;Note that each time you restart Chrome you will be prompted to ``Disable Developer Mode Extensions``. Feel free to simply hit ``Cancel`` and continue.<br/>  
![image](https://cloud.githubusercontent.com/assets/27123/21674871/5041d6c6-d338-11e6-9112-9dcebb5553e6.png)

This is indeed annoying, as Google intends, however there is no workaround we are aware of at this time

<br>

#### Installing the CRX (Windows only)

Instead of installing the extension from the unpacked files, you can install the CRX and whitelist it so that you don't get the ``Disable Developer Mode Extensions`` message. This requires access to the group policy editor.

1. Download the latest chromium CRX file from our [releases page](https://github.com/dhowe/AdNauseam/releases/latest)
2. Go to chrome://extensions/
3. Enable developer mode by flipping the switch at the top right corner
4. Drag the CRX from earlier into the window. This will install the extension
5. Download the Chrome group policy templates [here](http://dl.google.com/dl/edgedl/chrome/policy/policy_templates.zip)
6. Copy [zip]\windows\admx\chrome.admx to C:\Windows\PolicyDefinitions
7. Copy [zip]\windows\admx\Your Language (for example, en-GB)\chrome.adml to C:\Windows\PolicyDefinitions\Your Language\chrome.adml
8. Go to chrome://extensions and copy the ID of Adnauseum. It should be a long string of letters. If you can't see the ID, ensure that developer mode is enabled.
9. Press Win + R to open the run window and type gpedit.msc
10. Go to User Configuration -> Administrative Templates -> Google Chrome -> Extensions
11. Open "Configure extension installation whitelist" by double clicking on it
12. Check the "Enabled" box to activate this policy
13. In the options box, click "Show..."
14. Paste the Adnauseam ID into a box and click OK
15. Apply these changes
16. Restart Chrome, Adnauseam should be enabled and working. If it isn't, ensure that it's enabled in chrome://extensions
17. If you have previously exported your ads, you can retrieve them now 

## Retrieve your saved data

1. After you have AdNauseam up and running again, go back to the AdNauseam settings page
1. Scroll all the way down again and click ''Import Ads''
1. Choose your backup
1. You're all set

<br>

## Using AdNauseam on other browsers

If __Google has lost your trust__, as it has ours, you might want to move to a browser that is not as intrusive and controlling. You have a number of options including:

* Go back to [Firefox](https://getfirefox.com), or a derivative like [WaterFox](https://www.waterfoxproject.org/)
* You've always wanted to [give Opera a chance](https://opera.com), this is a good excuse
* Try one of the many non-Google versions of Chromium, such as:
    * [Comodo Dragon](https://www.comodo.com/home/browsers-toolbars/browser.php)
    * [Vivaldi](http://www.vivaldi.com/)
    * [Centbrowser](https://www.centbrowser.com/)