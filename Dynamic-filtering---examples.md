Dynamic filtering can be used to block much more aggressively than what would normally happen when relying only on the default filter lists. With dynamic filtering, web pages are definitely more likely to break, but for many users this is acceptable, so long as the content of a web page can still be read.

Following are some examples of using dynamic filtering vs. not using dynamic filtering, with both scenarios using the default filter lists. The top row in each table shows the used bandwidth.

I didn't report below the comparative results without a blocker, that would be a lot of noise detracting from the main topic here, but I provide a summary of what would have happened without µBlock with default filter lists. (That is with click-to-play enabled for plugins -- it would be much worst without this.)

#### Example 1 -- An article on TechCrunch

URL: <http://techcrunch.com/2014/10/07/yahoo-lays-off-employees-in-india-reportedly-up-to-2000-affected/>

The article could be read all fine with dynamic filtering. For many users it's often only what matters for most sites.

Without µBlock enabled at all, 61 hostnames were hit, with the consumed bandwidth at 2,627,068 bytes.

| No dynamic filtering | Dynamic filtering<br>3rd-party `<script>` and `<iframe>` |
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
