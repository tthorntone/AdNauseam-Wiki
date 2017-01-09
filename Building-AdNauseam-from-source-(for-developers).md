##### Setup (on OS X  only, linux instructions pending)

* First, install [jq](https://stedolan.github.io/jq/) if you don't have it 
* Then do the following from the terminal:
```
$ git clone https://github.com/dhowe/AdNauseam.git
$ git clone https://github.com/dhowe/uAssets.git
$ cd AdNauseam
```

##### For Chromium / Opera:

1. Build the extension (via the terminal)
```$ tools/make-chromium.sh```
or 
```$ tools/make-opera.sh```

2. Open the browser and go to settings, with URL ```chrome://extensions/```

3. Enable Developer mode in the settings page and load extension from ```/bin/build/adnauseam.chromium``` or ```/bin/build/adnauseam.opera```

4. To view console messages, go to ```chrome://extensions/```, and select 'background.html' under the AdNauseam entry

##### For Firefox:

  _Note: [Developer](https://www.mozilla.org/en-US/firefox/developer/) builds are now required for development_

1. Open Firefox with the profile you intend to use, then go to ```about:config```, then set ```xpinstall.signatures.required``` to false     
(Make sure that you open the profile manually rather than open it through $ tools/run-ff.sh. Nothing is saved in profiles opened through jpm)

2. Make sure you have [jpm](https://www.npmjs.com/package/jpm) installed

3. In terminal:` $ tools/run-ff.sh`

  _Note: If your Firefox dev version is not in the usual location, you will need to change FIREFOX_BIN in 'tools/run-ff.sh'_

4. (Optional) To use a [Firefox profile](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles) other than the default, pass the profile path to _run-ff.sh_:

    ````$ tools/run-ff.sh /path/to/profile```` 

5. To view console messages, select the ```Tools->Web Developer->Browser Console``` menu option


##### Next

- Visit the [The Developer FAQ](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ)


