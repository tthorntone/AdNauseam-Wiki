##### Setup (OS X), 

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

##### For Firefox:

1. Open Firefox and go to ```about:config```, then set ```xpinstall.signatures.required``` to false
2. Make sure you have [jpm](https://www.npmjs.com/package/jpm) installed
3. In terminal:` $ tools/run-ff.sh`
4. (Optional) To use a Firefox profile other than default, pass the profile path to run-ff.sh:
````$ tools/run-ff.sh path/to/profile```` 
