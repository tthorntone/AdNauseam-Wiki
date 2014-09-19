Just a place for me to keep track of contributed memory to web pages over time. Using [Acid Test 3](http://acid3.acidtests.org/), a very simple web page, with embedded `iframes`. Web page was opened in a new tab for each extension (important). Each extension tested alone, with no other extension enabled.  Browser left on idle for more than 1 minute to ensure web page memory was garbage collected.

### 19 September 2014

- Chromium 37.0.2062.94 64-bit (Linux)
- µBlock v 0.6.2.1 (default filter lists)
- Adblock Plus 1.8.5 (_EasyList_, _EasyPrivacy_, _Malware Protection List_, _"Acceptable ads"_ disabled)

Summary of results:
- Reference memory usage for the web page: 22 MB
- Adblock Plus adds over 32 MB
- µBlock Plus adds over 9 MB

No extension (reference):<br>
![no extension](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-in-page-20140919-none.png)

Adblock Plus:<br>
![Adblock Plus](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-in-page-20140919-abp.png)

µBlock:<br>
![µBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-in-page-20140919-ublock.png)

Observations:

Last time I ran this benchmark [was on Chromium 34 64-bit](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-vs.-ABP:-efficiency-compared#added-memory-footprint-to-web-pages), and it does appear that Chromium 37 is causing web pages to consume more memory -- reference result went from ~17 MB to ~22 MB.