[Google has banned AdNauseam](https://adnauseam.io/free-adnauseam.html) from its web store and have left users with no access to their data. Follow these instructions to install it anyway.

## Back up your data

_If you're a new AdNauseam user, or don't care about your saved ads, jump to [Installation](#install-adnauseam)_

1. Click on the AdNauseam icon to open the AdNauseam menu
2. Click the ``SETTINGS`` button at the bottom of the menu
3. Scroll down to the bottom of the page and click ``EXPORT ADS``

## Install AdNauseam

### Other Operating Systems
The following instructions are for Google's Chrome and Chromium browsers ONLY. For other Chromium-based browsers simply download the latest [.CRX file](https://github.com/dhowe/AdNauseam/releases/latest), open the extension page, and drag the file into your browser window 

*NOTE: the Brave Browser no longer allows extensions from outside the Chrome webstore*

#### Manual Install in Developer Mode
1. Download the most latest adnauseam.chromium.zip file from our [releases page](https://github.com/dhowe/AdNauseam/releases/latest) (make sure to download the _chromium.zip_ file!)
2. Extract the zip file to a folder somewhere that it can remain  
**Warning: Do not delete this folder after the install; Chrome will disable AdNauseam if this folder is not in the expected location**

3. In your Chrome Browser menu, click Windows > Extensions or type chrome://extensions/ in the address bar  
4. Check the 'Developer Mode' checkbox  
5. Click the 'Load unpacked extension' button and navigate to the folder you downloaded in step 1. Make sure you select the folder with the name 'adnauseam.chromium'(without a version number). 
6. If you have previously exported your ads, you can retrieve them now  

<br>

*&nbsp;Note that each time you restart Chrome you will be prompted to ``Disable Developer Mode Extensions``. Feel free to simply hit ``Cancel`` and continue.<br/>  
![image](https://cloud.githubusercontent.com/assets/27123/21674871/5041d6c6-d338-11e6-9112-9dcebb5553e6.png)

This is indeed annoying, as Google intends, however there is a workaround for [advanced users on Windows](https://github.com/dhowe/AdNauseam/wiki/Install-AdNauseam-in-Chrome-on-Windows). Unfortunately we are thus far unaware of workarounds for other platforms.

<br>

## Retrieve your saved data

1. After you have AdNauseam up and running again, go back to the AdNauseam settings page
1. Scroll all the way down again and click ''Import Ads''
1. Choose your backup
1. You're all set

<br>

## Using AdNauseam on other browsers

If __Google has lost your trust__, as it has ours, you might want to move to a browser that is not as intrusive and controlling. You have a number of options including:

* Go back to [Firefox](https://getfirefox.com), or a derivative like [WaterFox](https://www.waterfoxproject.org/)
* Try one of the many non-Google versions of Chromium, such as:
    * [Comodo Dragon](https://www.comodo.com/home/browsers-toolbars/browser.php)
    * [Vivaldi](http://www.vivaldi.com/)
    * [Centbrowser](https://www.centbrowser.com/)

<br>

## Keep AdNauseam Updated

### For Chrome Enterprise / Edge Chromium users:

If you add the following Key's to the HKLM or HKCU, no other actions need to be taken to install AdNauseam
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Google\Chrome\ExtensionInstallForcelist]
"1"="pnjfhlmmeapfclcplcihceboadiigekg;https://rednoise.org/adnauseam/updates.xml"
```
For the Edge Beta you can set the same key in this location.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge\ExtensionInstallForcelist]
```

~~For the Brave Browser you can set the same key here:~~

Note: Brave no longer allows non-Chrome store extensions
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\BraveSoftware\Brave\ExtensionInstallForcelist]
```

### For Linux users:
Please note that by default, manually installed AdNauseam in Developer Mode won't be automatically updated. If you are familiar with Arch Linux, you can checkout [this package](https://aur.archlinux.org/packages/chromium-extension-adnauseam/), maintained by [gardenappl](https://github.com/gardenappl), to keep AdNauseam updated.
