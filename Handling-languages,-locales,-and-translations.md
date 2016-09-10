###How are locales and languages handled?

Locale files for each platform are generated during the build process. The baseline English file is generated when `_locales/en/messages.json` and `_locales/en/adnauseam.json` are merged (via `jq`, called from tools/make-locales.sh). Though automatically triggered when building, you can also run this script on its own as follows:

`$ tools/make-locales.sh [/path/to/output/files]`

###How are translations updated and integrated?

We sometimes make first hand changes to the locale file `_locales/en/adnauseam.json` in Github. When this happens we also need to update all our translations to include these edits or additions, which we do through [Crowdin](https://crowdin.com/project/adnauseam).

The English version of the 'adnauseam.json' file is the source on Crowdin for public translations.

Our workflow for updating translations is as follows (assumes Crowdin Manager permission):

1. Sync the English version of 'adnauseam.json' on Crowdin with the one on Github (see image below)
2. Make and approve contributed translations on Crowdin 
3. Build the Crowdin project so that it contains only the latest approved translated strings
4. Download and unpack the latest Crowdin zip archive (to ~/Downloads/adnauseam)
5. Run the following command from root of the ADN source tree to update the (non-english) locale files in our source.

  `$ tools/import-adn-crowdin.sh`

6. Check a translated language (e.g., `_locales/zh_CN/adnauseam.json`) to verify that it contains the latest updates
7. Building for any platform will now trigger the merging of 'adnauseam.json' and 'messages.json' into a single file, for each language/locale, in the generated extension.

**_Screenshot for updating source `adnauseam.json`_**:
![1](https://cloud.githubusercontent.com/assets/2461812/18377999/cdc54c16-769c-11e6-89df-b432a28c1bda.PNG)



