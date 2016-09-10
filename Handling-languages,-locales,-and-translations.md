###How are locales and languages handled?

Locale files for each platform are generated during the build process. The final 'messages.json' file (or 'messages.properties' on Firefox) is generated when `_locales/en/messages.json` and `_locales/en/adnauseam.json` are merged (via `jq`, called from `tools/make-locales.sh`). Though automatically triggered when building, you can also run this script on its own as follows:

`$ tools/make-locales.sh [/path/to/output/files]`

###How are translations updated and integrated?

We sometimes manually update the locale file `_locales/en/adnauseam.json` in Github. When this happens we also need to update all our translations to include these edits or additions, which we do through [Crowdin](https://crowdin.com/project/adnauseam). 

_Note: the English version of 'adnauseam.json' is the ONLY locale file that should ever be edited directly in the repo!_

The English 'adnauseam.json' file can then be uploaded as the source on Crowdin for public translations (step 1 below)

Our workflow for updating translations is as follows (assumes Crowdin Manager permission):

1. Sync the English version of 'adnauseam.json' on Crowdin with the one from the repo (see image below)
2. Make and approve contributed translations on Crowdin 
3. Build the Crowdin project so that it contains only the latest approved translated strings (???)
4. Download and unpack the latest Crowdin zip archive (to ~/Downloads/adnauseam)
5. Run the following command from root of ADN to update the (non-english) locale files in our source.

  `$ tools/import-adn-crowdin.sh`

6. Check one or more translated languages (e.g., `_locales/zh_CN/adnauseam.json`) to verify that they contain the latest updates
7. At this point, building for any platform will now merge the updated 'adnauseam.json' with the existing 'messages.json' into a single file, for each language/locale, in the generated extension.

**_Screenshot for updating source `adnauseam.json`_**:
![1](https://cloud.githubusercontent.com/assets/2461812/18377999/cdc54c16-769c-11e6-89df-b432a28c1bda.PNG)



