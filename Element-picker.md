The element picker's purpose is to assist the user in the creation of network or cosmetic filters.

If there is an element on a web page you wish to remove forever, open the extension's popup menu, and click the small ["eye-slash" icon](http://fontawesome.io/icon/eye-slash/). You will enter the interactive element picker-mode.

![Element picker](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ss-element-picker.png)

Once in element-picker mode, you have to point and click on the element you wish to remove.

Once you click on the element, you will be presented with a modal dialog box which allows you to select, and optionally edit and create a filter for the element you wish to remove from the web page.

If possible, a network filter will be offered, and a list of cosmetic filters, aka CSS selectors which have been derived from the element you clicked. These CSS selectors are to be used as cosmetic filters. The top most CSS selector is the most specific which could be derived from the element you clicked. The bottom-most is the farthest, the least specific.

When you click on one of the pre-computed CSS selector, you will be shown what effect it will have on the page. You may want to ensure a CSS selector will not also get rid of useful items on the page. If you hold `ctrl` while clicking on an entry in the list, only the selector of the entry itself will be used, rather than the full path of selectors.

You may manually edit the selector. However the result needs to be a valid filter, otherwise you won't be allowed to create a filter out of it. A valid filter in the context of the element picker is one which matches at least one element on the web page.

You may quit the interactive element picker by clicking the _Quit_ button. You may close the modal dialog and go pick an element again by clicking the _Pick_ button.

The _Create_ button will be enabled only if a proper filter can be created from the content of the text area. Once you click the _Create_ button, the element picker will add the necessary tokens to ensure the filter apply **only** to the current web site, will add it to your custom list of filters and save it.