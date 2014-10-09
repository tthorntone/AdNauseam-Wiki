Dynamic filtering can be used to block much more aggressively than what would normally happen when relying only on the default filter lists. With dynamic filtering, web pages are definitely more likely to break, but for many users this is acceptable, so long as the content of a web page can still be read.

Following are some examples of using dynamic filtering vs. not using dynamic filtering (i.e. relying solely on the static filter lists), with both scenarios using the default filter lists. The top row in each table shows the used bandwidth.

<p align="center"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-4.png" /><br><sup>3rd-party scripts and 3rd-party frames blocked by default on all sites.</sup></p>

I didn't report below the comparative results without a blocker, that would be a lot of noise detracting from the main topic here, but I provide a summary of what would have happened without µBlock with default filter lists. (That is with click-to-play enabled for plugins -- it would be much worst without this.)

I used my [HAR parser](http://raymondhill.net/httpsb/har-parser.html) tool to extract the results.

- [An article on TechCrunch](#example-1----an-article-on-techcrunch)
- [An article on The New Yorker](#example-2----an-article-on-the-new-yorker)
- [An article on Bloomberg](#example-3----an-article-on-bloomberg)
- [An article on Live Mint](#example-4----an-article-on-live-mint)
- [An article on SecureList](#example-5----an-article-on-securelist)
- [An article on Wired](#example-6----an-article-on-wired)
- [An article on CNN](#example-7----an-article-on-cnn)
- [An article on VICE](#example-8----an-article-on-vice)
- [An article on Nautilus](#example-9----an-article-on-nautilus)

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
| ajax.googleapis.com | |
| api.parsely.com | |
| assets.adobedtm.com | |
| dff7tx5c2qbxc.cloudfront.net | |
| plugin.mediavoice.com | |
| subscribe.condenet.com | subscribe.condenet.com |
| use.typekit.net | |
| www.googletagservices.com | |
| www.newyorker.com | www.newyorker.com |

### Example 3 -- An article on Bloomberg

URL: <http://www.bloomberg.com/news/2014-10-03/yahoo-said-close-to-investing-in-snapchat-at-10b-value.html>

The article could be read all fine with dynamic filtering, though an interactive widget to display a graph of Yahoo's stock price over time didn't display at all.

Without µBlock enabled at all, 48 different hostnames were hit, with bandwidth consumption at 2,095,142 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 1,615,283 | 141,590 |
| a.disquscdn.com | |
| bloomberg.disqus.com | |
| cdn.gotraffic.net | cdn.gotraffic.net |
| cdn.taboola.com | |
| disqus.com | |
| fonts.gotraffic.net | |
| images.taboola.com | |
| location.bloomberg.com | |
| login.bloomberg.com | |
| netstorage.taboola.com | |
| personalization.bloomberg.com | |
| q.bloomberg.com | |
| trc.taboola.com | |
| www.bloomberg.com | www.bloomberg.com |

### Example 4 -- An article on Live Mint

URL: <http://www.livemint.com/Industry/TM8tDvrv3OfeYjeXkEPXZI/Flipkart-hits-100-million-sales-target-in-10-hours.html>

The article could be read all fine with dynamic filtering, though commenting through Disqus was not possible. Of course, if ever you care commenting, turning off whatever dynamic filters for a specific site is as simple as point-and-click.

Without µBlock enabled at all, 25 different hostnames were hit, with bandwidth consumption at 1,276,894 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 736,197 | 281,111 |
| a.disquscdn.com | |
| cdn.taboola.com | |
| disqus.com | |
| h.ppjol.com | |
| images.taboola.com | |
| livemint07.disqus.com | |
| netstorage.taboola.com | |
| s.ppjol.net | |
| trc.taboola.com | |
| www.livemint.com | www.livemint.com |

### Example 5 -- An article on SecureList

URL: <http://securelist.com/blog/research/66988/tyupkin-manipulating-atm-machines-with-malware/>

The article could be read all fine with dynamic filtering. An embedded Youtube video was reduced to an hyperlink (which is a good thing IMO).

Without µBlock enabled at all, 18 different hostnames were hit, with bandwidth consumption at 1,969,789 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 1,657,834 | 1,131,906 |
| 25zbkz3k00wn2tp5092n6di7b5k.<br>wpengine.netdna-cdn.com | 25zbkz3k00wn2tp5092n6di7b5k.<br>wpengine.netdna-cdn.com |
| i.ytimg.com | |
| kasperskycontenthub.com | |
| s0.wp.com | |
| securelist.com | securelist.com |
| s.ytimg.com | |
| www.google.com | |
| www.youtube.com | |

### Example 6 -- An article on Wired

URL: <http://www.wired.com/2014/10/feds-silk-road-hack-legal/>

The article could be read all fine with dynamic filtering. The Disqus comments were not loaded though -- a nice side-effect IMO.

Without µBlock enabled at all, 46 different hostnames were hit, with bandwidth consumption at 3,459,474 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 2,643,977 | 1,520,884 |
| a.disquscdn.com | |
| disqus.com | |
| fonts.condenast.com | |
| html1-f.scribdassets.com | |
| html2-f.scribdassets.com | |
| images.outbrain.com | |
| odb.outbrain.com | |
| plugin.mediavoice.com | |
| s1-f.scribdassets.com | |
| s2-f.scribdassets.com | |
| widgets.outbrain.com | |
| wired.disqus.com | |
| www.scribd.com | |
| www.wired.com | www.wired.com |

### Example 7 -- An article on CNN

URL: <http://www.cnn.com/2014/10/07/opinion/maynard-assisted-suicide-cancer-dignity/index.html?hpt=hp_c2>

The article could be read all fine with dynamic filtering. Disqus comments were not loaded. I noticed the CPU churning and network activity after the page loaded with µBlock disabled. This is not uncommon with bloated pages ridden with tracking et al. javascript code. After I re-enabled µBlock with dynamic filtering turned on and forced a reload of the page, the CPU went to rest.

Without µBlock enabled at all, 57 different hostnames were hit, with bandwidth consumption at 2,216,736 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 1,466,984 | 613,012 |
| a.disquscdn.com | |
| cache-02.cleanprint.net | |
| cdn.flipboard.com | |
| cnn.disqus.com | |
| d2jsycj2ly2vqh.cloudfront.net | |
| disqus.com | disqus.com |
| flipboard.com | |
| i2.cdn.turner.com | i2.cdn.turner.com |
| i.cdn.turner.com | i.cdn.turner.com |
| images.outbrain.com | |
| mediacdn.disqus.com | mediacdn.disqus.com |
| odb.outbrain.com | |
| s.flipboard.com | |
| svcs.cnn.com | svcs.cnn.com |
| trends.cnn.com | |
| widgets.outbrain.com | widgets.outbrain.com |
| www.cnn.com | www.cnn.com |
| z.cdn.turner.com | z.cdn.turner.com |

### Example 8 -- An article on VICE

URL: <http://www.vice.com/read/research-drugs-and-the-grey-market>

The article could be read all fine with dynamic filtering.

Without µBlock enabled at all, 38 different hostnames were hit, with bandwidth consumption at 2,046,372 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 1,509,663 | 1,267,643 |
| assets.vice.com | assets.vice.com |
| clients1.google.com | |
| player.ooyala.com | |
| www.google.com | |
| www.vice.com | www.vice.com |

### Example 9 -- An article on Nautilus

URL: <http://nautil.us/issue/18/genius/shakespeares-genius-is-nonsense>

The article could be read all fine with dynamic filtering of 3rd-party scripts and frames. Disqus comment section did not load (fine by me).

Without µBlock enabled at all, 22 different hostnames were hit with bandwidth consumption at 4,780,294 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>`<br>3rd-party `<iframe>` |
|---------------------:|------------------------------------------------------:|
| 4,629,924 | 4,185,531 |
| a.disquscdn.com | |
| connect.facebook.net | |
| disqus.com | |
| nautil.us | nautil.us |
| nautilusmag.disqus.com | |
| nautilus-prod.s3.<br>amazonaws.com | nautilus-prod.s3.<br>amazonaws.com |
| static.nautil.us | static.nautil.us |
| use.typekit.net | |