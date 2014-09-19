Just a place for me to keep track of contributed memory to web pages over time. Using Acid Test 3, a very simple web page, wih embedded `iframes`. Each extension tested alone, with no other extension enabled. Browser left on idle for more than 1 minute to ensure web page memory was garbage collected.

### 19 September 2014

- Chromium 37.0.2062.94 64-bit (Linux)
- µBlock v 0.6.2.1
- AdBlock 2.7.13

No extension (reference):<br>
![no extension](https://https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-in-page-20140919-none.png)

Adblock Plus:<br>
![Adblock Plus](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-in-page-20140919-abp.png)

µBlock:<br>
![µBlock](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-in-page-20140919-ublock.png)

Observations:

Last time I ran this benchmark [was on Chromium 34 64-bit](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-vs.-ABP:-efficiency-compared#added-memory-footprint-to-web-pages), and it does appear that Chromium 37 is causing web pages to consume more memory.