If Adnauseam is automatically disabled on Chrome by Google for not being in the webstore. It will have the following message “This extension is not listed in the Chrome Web Store and may have been added without your knowledge.”
 
1. Find the extension ID by going to chrome://extensions/, which should be `pnjfhlmmeapfclcplcihceboadiigekg` if you installed it from CRX file

1. Open regedit (type that in start menu) as an administrator

1. Navigate to Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Google\Chrome\

1. Make a new key called “ExtensionInstallWhitelist” if it doesn’t already exist

1. In that key make a new string value called “1” or one number higher than what is already there.

1. Set the value of that to the Adnauseam extension ID

1. Restart chrome.

1. Should the extension update, you may need to correct the extension ID to fit the new version.