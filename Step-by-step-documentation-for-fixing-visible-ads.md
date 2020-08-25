1. Is the ad a video ad? 
- If yes, go to step 2
- If no, go to step 5

2. **Video ad** 
- Is it visible when using ublock? 
- If no, continue to step 3.
- If yes, then this is not an ADN-specific problem (though we may want to fix it anyway), continue to step 4.

3. Block Adn-allowed requests
- Open the logger and look for an blue-color entry(adnauseam-allowed)
- Continue to step 5

4. Block general requests
- Open the logger and look for entries without background colors.
- Follow step 5 and try to block requests that seem suspicious to you(they are most likely script or xhr requests).

5. **_Hide with blocking rules_**
- Try to block one request at a time using [dynamic URL filtering rules](https://github.com/gorhill/uBlock/wiki/The-logger#dynamic-url-filtering-rules), then refresh the page by hitting the refresh button.
- If it works, use [static network filters dialog box](https://github.com/gorhill/uBlock/wiki/The-logger#static-network-filters) to assist you to write a static blocking rule. Once you are done, unblock the request from dynamic filtering and test your static blocking rule. If you can verify that the static rule works as well, add it to adnauseam.txt.

----------

6. Is it an image ad?
- Some ads might look like image ad but they are not. You can double check whether an ad is a true image ad by right click on it and check it with "inspect element". If you can find an image file either in html or css(background image), go to step 7 **[Image Ad]**. If there is no image to be collected, or if it is composed of multiple small images, go to step 8 **[Dynamic Ad]**

7. **Image Ad**
-  Try to first hide an image ad with cosmetic filters, continue to step 9
-  If the ad is hidden but not collected, please refer to [this page](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#how-do-i-debug-an-image-ad-that-is-being-hidden-but-not-collected) for more guidance on ad collection
- If under very rare cases, the annoying image ad can't be hidden using cosmetic filters no matter how hard you try, you still have the option to block it by following step 3.

8. **Text ads or Dynamic Ad**
-  These ads can't be collected with cosmetic filters and you can either hide them by creating cosmetic filters(see step 9), or try to block it by following step 3.
-  Most of the time, we don't collect ads under this category other than common search engine text ads(see [textads.js](https://github.com/dhowe/AdNauseam/blob/master/src/js/adn/textads.js)). But if it's visible on popular websites or if it's a very common ad type that appears across multiple sites, please refer to this [FAQ](https://github.com/dhowe/AdNauseam/wiki/Developer-FAQ#how-do-i-create-a-custom-filter-for-a-text-or-text-hybrid-ad) if you want to create custom filters for text or hybrid ad.

9. **_Hide with cosmetic rules_**
- Cosmetic rules are similar to element selectors in javascript or jquery. For example, if there is an ad image inside an element with the class attribute 'adImage'. Adding a rule like `##.adImage` will hide such an element. Typically we want to add cosmetic rules that are specific to the site we are working on `example.com##.adImage`. In principle, this is better  because a general cosmetic filters (one applied to every site) might hide non-ad content on other websites and this is very difficult to properly test.
- There are a number of tools you can use to help create cosmetic filters. If you're new to this, start with uBlock Origin's [element picker](https://github.com/gorhill/ublock/wiki/element-picker)(right click/block element), or you can always use the browser inspector. Sometimes uBlock's [DOM inspector](https://github.com/gorhill/uBlock/wiki/DOM-inspector) could also be helpful to identify the all the elements where cosmetic filters are triggered.
- Once you have identified a rule using one of the tools above, you should test it by adding it to "Dashboard/My filters" in AdNauseam's settings and then click the button "Apply changes".
- Refresh the web page you are testing and check whether the ad has been successfully hidden.
- If it is not hidden, then you may need to adjust your cosmetic filter rule. Double-check the syntax or try to write an alternative rule using other class names, ids, or attributes. If none of these work, you might consider going to step 5 and checking whether there are "adn-allowed" javascript requests that make these ads difficult to hide with a cosmetic filter. Please keep in mind that we prioritize ad hiding over ad blocking, as long as we can collect the ad. But if ad collection is somehow not possible for certain ad types, we will then consider blocking it when cosmetic filters are not working.
- Once the new rule is working as expected, you can then submit it for inclusion in AdNauseam itself. Do this by adding it the [AdNauseam filter list](https://github.com/dhowe/AdNauseam/blob/master/filters/adnauseam.txt) and then making a 'Pull Request' on github (or if you don't know how to do this, simply send the rule, with a brief description, to adnauseam-at-rednoise.org).
- More information on how to write your own cosmetic filters can be found [here](https://help.eyeo.com/en/adblockplus/how-to-write-filters#elemhide_basic)
- In addition to basic cosmetic filters, as described above, you can also hide elements with _procedural cosmetic filters_.  Procedural cosmetic filters are useful when there is no obvious id/class to target, but rather CSS attributes or more advanced selectors that relies on certain hierarchy of the Dom structure. It can be used on top of a plain CSS selector and supports more advanced element selection. It allows you to select a parent based on its child `subject:has(arg)`, the textual content`subject:has-text(needle)`, or even the CSS attribute `subject:matches-css(arg)`. The syntax for this type of filter can be found [here](https://github.com/gorhill/uBlock/wiki/Procedural-cosmetic-filters). 


----
### Element Selection Principles
a. The element should contain both the target URL (usually an `<a>` tag) and the image (the ad content).
b. Try to collapse the ad (also hide extra wrapper with height)  
c. The selectors should be specific to the site

 ```
 <div class="adWrapper banner">
   <div>
     <a href="#">
       <img class="adImage">
     </a>
   </div>
 </div>
 ```

Consider the DOM structure above as an example. We generally don't want to try and hide the image only, as AdNauseam (specifically the ad-clicking function) also need the ad's target URL. So in this case, the `<a>` tag would be the minimal DOM element with which we could hide the image _and_ provide enough information for AdNauseam to collect and later click the ad.  (Principle a.)

However, online ads are often hidden within layers and layers of wrappers. And sometimes these wrappers include CSS styles that set a fixed height. In these cases, we need to target the outermost wrapper, so that any extra blank space can be removed from the page. Another reason we generally target the wrapper instead of the `<a>` tag is that wrappers usually come with specific classes or ids, while it's less common for `<a>` tags to have those. (Principle b.)

Once we have decided the element we want to hide, we will need to choose the best selectors to write the cosmetic rule. In our example, the ad wrapper can be targeted by `.banner` and `.adWrapper`. Because `.banner` class is very common and we don't want to hide other banner images that are not advertisements, it's safer to write the following cosmetic rule `example.com##.adWrapper`. (Principle c.)

---
****IFrames****
```
<div class="adContainer">
  <iframe>
    <iframe>
      <div class="adWrapper banner">
        <div>
          <a href="#" id="adLink">
            <img class="adImage">
          </a>
        </div>
      </div>
    </iframe>
  <iframe>
</div>
```
Iframes are _very_ common for online ads and in general they can be hidden following the principles described above. But there are extra factors you should take into consideration when writing cosmetic rules for ads in iframes:

d. The scope for Content Scripts
[Content Scripts](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Content_scripts) are injected into each page as it loads. However, an iframe is not considered to be a part of the parent page. So any Content Scripts for the page needs to be re-injected into each iframe on each page. 

In the example above, you will need to identify the innermost iframe and focus on ".adWrapper.banner" for our cosmetic filter in order to have access to the ad-content. A cosmetic rule targeting ".adContainer" might still be necessary, in order to eliminate blank space, but that rule alone is not enough for AdNauseam to properly collect the ad.


