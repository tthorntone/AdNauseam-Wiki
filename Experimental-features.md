[under construction]

### Privacy exposure reduction

One way users increase their privacy exposure is through [content delivery networks](http://en.wikipedia.org/wiki/Content_delivery_network) ("CDN") and likes. Good examples of CDN are `ajax.googleapis.com`, `cdnjs.cloudflare.com`, `googletagservices.com`, etc. These servers are used to serve resources to countless web sites.

When a resources is pulled from one of these CDNs, typically the [referrer header](http://en.wikipedia.org/wiki/HTTP_referer) is set in the HTTP request, which allows ubiquitous CDNs to collect data about your browsing habits. Not good for privacy.

In the spirit of reducing privacy exposure, local mirroring is introduced as an experimental feature in µBlock. Local mirroring allows µBlock to cache locally resources pulled from known ubiquitous CDN, and future requests for the same resource will be served locally rather than pulling it from the CDN: not pulling a resource from a CDN prevents that CDN from collecting data about your browsing habit.

Where _x_ / _y_ = 3rd party / all.

Before: <br>
URLs visited: 60 <br>
Domains: **415** / 475 <br>
Hosts: 621 / 842 <br>
Scripts: 857 / 1264 <br>
Outbound cookies: 0 / 130 <br>
Net requests: 3,304 / 6,264 <br>

After: <br>
URLs visited: 60 <br>
Domains: **337** / 397 <br>
Hosts: 541 / 759 <br>
Scripts: 793 / 1214 <br>
Outbound cookies: 0 / 132 <br>
Net requests: 3,174 / 6,156 <br>
