Dynamic URL filtering became available in uBlock Origin version 0.9.8.0.

The primary purpose of dynamic URL filtering ("URL filtering") is as a diagnosis/mitigation tool to fix web page breakage caused by dynamic filtering or static filtering. Secondary purpose of URL filtering is to offer higher granularity than what dynamic filtering can support.

URL filtering has precedence over dynamic filtering and static filtering. See ["Overview of uBlock's network filtering engine"](https://github.com/gorhill/uBlock/wiki/Overview-of-uBlock's-network-filtering-engine) to see where URL filtering fits and to better understand its purpose.

URL filtering is accessible from the logger, i.e. you will create and manage dynamic URL rules through the logger UI.

URL filtering uses _rules_, which resemble dynamic filtering rules, except that the destination hostname is replaced by a URL.

A resource matches a URL filtering rule if the URL of the resource starts exactly with a given URL filtering rule.

