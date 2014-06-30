µBlock can parse and enforce hosts files. For instance, out-of-the-box, µBlock supports [Peter Lowe’s Ad server](http://pgl.yoyo.org/) list which contains over 2,400 ad servers.

But there is an interesting hosts file available which is not enabled by default out-of-the-box: [hpHosts ad/tracking servers](http://hosts-file.net/) list. This list contains over 20,000 hostnames linked to ad servers.

I have been using this list since days now, and I really do not see many issues, i.e. numerous unexpected web site "breakage".

I cannot select this list by default for new install, since I have no idea yet how much risks "breaking" web page. But you may want to give it a try, adding an extra 20,000 ad servers to the filtering engine surely is of help (I may run a benchmark eventually to compare the locking power relative to plain out-of-the-box settings).

Eventually, if more users try the hpHosts ad/tracking servers list, and report any and all issues with it, we can create the appropriate exception filters to prevent these breakage, and then it might become feasible to enable it out of the box.

For instance, the recent [hacking of Reuters through the Taboola content delivery network](http://www.ibtimes.co.uk/reuters-hacked-by-syrian-electronic-army-via-taboola-ad-1453717) would have left you unaffected, as hpHosts ad/tracking servers does contain the hostname `cdn.taboola.com`, which is from where the compromised javascript file was downloaded.

So if you wish to help in making it possible to enable this list out of the box, try it, and report any breakage (which doesn't happen without this list enabled) in [issue #17](https://github.com/gorhill/uBlock/issues/17)