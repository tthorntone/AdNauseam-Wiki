Support for cloud storage started with uBlock Origin 1.1.0.0.

Cloud storage is also often referred to as _sync_, as in [_Firefox Sync_](https://support.mozilla.org/1/firefox/43.0a1/Linux/en-US/prefs-weave) feature, or [Chrome browser's sync setting through a Google account](https://support.google.com/chrome/answer/165139), i.e. the ability to synchronize browser and extensions settings across multiple devices.

In uBlock Origin, cloud storage support must be explicitly enabled by the user, from the _Settings_ pane in the dashboard: check the _"Enable cloud storage support"_ checkbox.

Once you enable cloud storage support, a new UI widget will be available in the dashboard for panes which support the export/import of settings to/from cloud storage:

![screenshot](https://cloud.githubusercontent.com/assets/585534/9213128/5f29f5f2-405d-11e5-92a9-b2d9e8db3d42.png)

Your uBlock Origin settings are precious, and in order to prevent any automated browser's syncing task to cause precious local data (or cloud data) to be mistakenly overwritten, the chosen solution in uBlock Origin is to _never_ ever export to/import from cloud storage without **the user expressly asking uBlock Origin to do so**.

So essentially, the sync feature in uBlock is implemented as a global clipboard (through cloud storage) to where settings are copied to/pasted from, and only you decide when to export/import.

The granularity of uBlock settings regarding cloud storage support is straightforward: one dashboard pane = one dedicated cloud storage entry. This way it is possible for a user to use cloud storage for specific panes, and not for others. Given that cloud storage is limited by browser vendors, one can choose to not persist one specific pane to the cloud.

The import/export of cloud storage data in a pane works strictly at the UI level, i.e. when you import cloud storage data, it will fill in the pane's UI as if you entered the data yourself: depending on the pane, you will still have to validate/commit the imported data.

If ever an export operation causes the cloud storage capacity limit to be reached, typically the cloud storage providers will refuse the operation, and the data on the cloud storage will be left unchanged. This is what I have observed with Chromium-based browsers.

If you do not have a syncing account with your browser vendor, I have observed that the cloud storage can still be used as a local clipboard to save a pane settings. Might be convenient sometimes, but please do not use cloud storage as a replacement for uBlock origin's backup feature. It is recommended you back up your settings regularly, this is especially true for those who have extensive custom static filters, custom rules, whitelist directives.

#### Caveats

Cloud storage services offered by specific browser vendors have their own limitations and quirks -- and this is out of control of uBlock.

##### Chromium-based browsers

- Various size limits: for example, on Chrome storage space limit is 102,400 bytes.
- Various limits on the number of operations per unit of time.
- See [`chrome.storage` API](https://developer.chrome.com/extensions/storage#property-sync) for more technical details.

##### Firefox browsers

- I have observed that too large amount of data will cause a warning in the browser console (> 8K).
- A new installation of uBlock Origin will cause cloud storage data to be blanked.
    - See: <https://discourse.mozilla-community.org/t/how-to-sync-preferences-of-a-bootstrapped-extension-via-sync/3024>.
- There is not much doc about this for Firefox, so there might be undocumented limitations yet to be found.
- Other Firefox-related platform:
    - I have no clue whether this new feature will work for other browser vendors.