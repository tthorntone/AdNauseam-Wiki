##### Setup (on OS X)

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

1. Open Firefox and go to ```about:config```, then set ```xpinstall.signatures.required``` to false

2. Make sure you have [jpm](https://www.npmjs.com/package/jpm) installed

3. In terminal:` $ tools/run-ff.sh`

4. (Optional) To use a [Firefox profile](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles) other than the default, pass the profile path to _run-ff.sh_:

    ````$ tools/run-ff.sh /path/to/profile```` 

5. To view console messages, select the ```Tools->Web Developer->Browser Console``` menu option
