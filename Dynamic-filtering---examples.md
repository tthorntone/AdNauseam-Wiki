Dynamic filtering can be used to block much more aggressively than what would normally happen when relying only on the default filter lists. With dynamic filtering, web pages are definitely more likely to break, but for many users this is acceptable, so long as the content of a web page can still be read.

Following are some examples of using dynamic filtering vs. not using dynamic filtering (i.e. relying solely on the static filter lists), with both scenarios using the default filter lists. The top row in each table shows the used bandwidth.

I didn't report below the comparative results without a blocker, that would be a lot of noise detracting from the main topic here, but I provide a summary of what would have happened without µBlock with default filter lists. (That is with click-to-play enabled for plugins -- it would be much worst without this.)

I used my [HAR parser](http://raymondhill.net/httpsb/har-parser.html) tool to extract the results.

### Example 1 -- An article on TechCrunch

URL: <http://techcrunch.com/2014/10/07/yahoo-lays-off-employees-in-india-reportedly-up-to-2000-affected/>

The article could be read all fine with dynamic filtering. For many users it's often only what matters for most sites.

Without µBlock enabled at all, 61 different hostnames were hit, with the consumed bandwidth at 2,627,068 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 1,144,039 | 418,578 |
| 0.gravatar.com | | 
| b.grvcdn.com | |
| i.api.grvcdn.com | |
| o.aolcdn.com | |
| pthumbnails.5min.com | |
| r-login.wordpress.com | |
| rma-api.gravity.com | |
| s0.wp.com | s0.wp.com |
| s2.wp.com | s2.wp.com |
| s.aolcdn.com | |
| tctechcrunch2011.files.<br>wordpress.com | tctechcrunch2011.files.<br>wordpress.com |
| techcrunch.com | techcrunch.com |
| zor.livefyre.com | |

### Example 2 -- An article on The New Yorker

URL: <http://www.newyorker.com/magazine/2013/03/11/up-all-night-2?currentPage=all>

The article could be read all fine with dynamic filtering.

Without µBlock enabled at all, 24 different hostnames were hit.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 1,346,535 | 487,095 |
| assets.adobedtm.com | |
| subscribe.condenet.com | subscribe.condenet.com |
| ajax.googleapis.com | |
| www.googletagservices.com | |
| plugin.mediavoice.com | |
| www.newyorker.com | www.newyorker.com |
| api.parsely.com | |
| dff7tx5c2qbxc.cloudfront.net | |
| use.typekit.net | |

### Example 3 -- An article on Bloomberg

URL: <http://www.bloomberg.com/news/2014-10-03/yahoo-said-close-to-investing-in-snapchat-at-10b-value.html>

The article could be read all fine with dynamic filtering, though an interactive widget to display a graph of Yahoo's stock price over time didn't display at all.

Without µBlock enabled at all, 48 different hostnames were hit, with bandwidth consumption at 2,095,142 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 1,615,283 | 141,590 |
| location.bloomberg.com | |
| login.bloomberg.com | |
| personalization.bloomberg.com | |
| q.bloomberg.com | |
| www.bloomberg.com | www.bloomberg.com |
| disqus.com | |
| bloomberg.disqus.com | |
| a.disquscdn.com | |
| cdn.taboola.com | |
| images.taboola.com | |
| netstorage.taboola.com | |
| trc.taboola.com | |
| cdn.gotraffic.net | cdn.gotraffic.net |
| fonts.gotraffic.net | |
