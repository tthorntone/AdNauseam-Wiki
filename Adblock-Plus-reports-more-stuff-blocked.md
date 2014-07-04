For both Adblock Plus and µBlock, the badge on the icon reports the number of net requests blocked by the extension.

Sometimes, for the same page, one extension can report more stuff blocked than the other, while the reality could be the opposite.

The less a blocker blocks, the more there are net requests. The more there are net requests, the more likely some of them will need to be blocked. So sometimes you end up with more request blocked as shown by the badge, while internally more requests were allowed on the web page.

Ultimately, for me it's the [benchmarks I run](/gorhill/uBlock/wiki/%C2%B5Block-vs.-others:-Blocking-ads,-trackers,-malwares) to report blocking power which tells the real story. The badge is really not a good way to assess blocking power of an extension, you could well endup concluding the opposite of what is really happening.

If you don't want to run a benchmark, I have this [little online tool](http://raymondhill.net/httpsb/har-parser.html) with which you can find out the requests which were **not** prevented from leaving your browser. To use it, open the dev console for the page for which you want a report, and go to the _Network_ tab.

Clear the browser cache by right-clicking somewhere in the _Network_ tab console. Force a reload of the web page, then right-click in the _Network_ tab console, and select _"Copy all as HAR"_. Then paste the result in the text area of this online tool, and click _Parse_. You will be shown the hostnames which were hit by the browser for the particular page you loaded.