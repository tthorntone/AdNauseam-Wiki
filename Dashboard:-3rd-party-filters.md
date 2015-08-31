[Back to Wiki home](https://github.com/gorhill/uBlock/wiki)

***

The _3rd-party filters_ pane is where you subscribe to filter lists. The filter lists to which you subscribe will feed the static filtering engine.

![3rd-party filter pane](https://cloud.githubusercontent.com/assets/585534/9589096/0b6cc212-4ffa-11e5-82f1-d276b71fef91.png)

***

##### Auto-update filter lists

If you check this option, uBlock Origin will update automatically the currently selected filter lists at regular interval. This option is checked by default (recommended).

##### Update now

This button is available for use if and only if there is at least one filter list which is deemed outdated. If this condition is fulfilled, you can force an update of all filter lists which are deemed out of date.

##### Purge all caches

This will remove all locally cached copies of filter the filter lists. Essentially, this will cause all filter lists to become out of date. This can be used to force an update of all filter lists.

##### Parse and enforce cosmetic filters

Un-check this option if you do not want cosmetic filters to be parsed and enforced. This option is mostly of interest for those who want to further reduce uBlock Origin's memory and CPU footprint. Cosmetic filtering has no value privacy-wise, its only purpose is to [hide elements](https://adblockplus.org/filters#elemhide) on a web page which can't be blocked otherwise. An example of this are the ads served with some Google Search results.

Note that disabling this option will also cause your own custom cosmetic filters (if any) to be ignored.

##### Stock filter lists

This is a collection of various filter lists, grouped by purpose. To use a specific filter list, just select it through its checkbox. Any change in the selection of filter lists must be committed by using the _Apply change_ button, which will appear if and only if the current selection of filter lists differs from the previous selection of filter lists.

> ***
> **Important:** The more filter lists are selected, the higher the likelihood of web site breakage. The quality of the selected filter lists also affects the likelihood of web site breakage. The _EasyList_-related filter lists are high quality filter lists, as they are actively maintained.
> ***

##### Custom filter lists

You can import custom 3rd-party filter lists: just paste in the text area the URL of where a filter lists can be fetched. These custom filter lists will be also automatically updated on a regular basis.