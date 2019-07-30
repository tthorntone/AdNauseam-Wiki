_NOTE: For advanced Windows users only: improperly editing the registry can result in serious system problems_

If you see the following message: “This extension is not listed in the Chrome Web Store and may have been added without your knowledge”, follow the steps below to use AdNauseam _without enabling Developer Mode_.
 
1. Find the extension-id for AdNauseam by going to chrome://extensions/. In the .crx file for the current release, this is  `pnjfhlmmeapfclcplcihceboadiigekg`

1. Open _regedit_ (you can type that into the start menu) as an administrator

1. Navigate to Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Google\Chrome\

1. Create a new key called “ExtensionInstallWhitelist”, if it doesn’t already exist

1. Create a new string value for this key called “1” (or any number higher than what is already there) and set it to  AdNauseam's extension-id

1. Restart chrome.

<br/>

Note: you may need to update the extension-id for newer versions of AdNauseam


<br/>

<sup>Thanks to Matt Moore for this workaround!</sup>