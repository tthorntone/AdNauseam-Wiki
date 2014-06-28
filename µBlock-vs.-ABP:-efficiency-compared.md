Here is a quick illustrated comparison of efficiency using various angles.

### Own memory footprint

These screenshots show the memory footprint of ABP and µBlock _after_ they have gone through this rather [demanding benchmark](https://github.com/gorhill/uBlock/wiki/Reference-benchmark). Once the benchmark was completed, I forced the browser to garbage collect the memory in each extension by clicking the trash icon a couple of times -- this is an _important step_, or else the shown memory footprint is not too reliable.

##### Adblock Plus
![ABP](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/abp-own-mem.png)

##### µBlock
![uBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ublock-own-mem.png)

Both extensions had _EasyList_, _EasyPrivacy_, _Peter Lowe's Ad Server_ list, and malware protection (there are more filters in µBlock for this last one).

####

### Added overhead to each net request

### Added memory footprint to web pages