[![Vim test](https://raw.githubusercontent.com/gorhill/uBlock/52ed1871b01cfb5edc0ba704cec8418463d648ad/doc/benchmarks/vim-test-abp-vs-ublock.png)](https://raw.githubusercontent.com/gorhill/uBlock/52ed1871b01cfb5edc0ba704cec8418463d648ad/doc/benchmarks/vim-test-abp-vs-ublock.png)<br><sup>Infamous VIM test: ABP 1,900 MB vs. uBlock 392 MB. Firefox 35 64-bit. ABP systematically adds around 3.5 MB per page **and per-frame** on a page, when using only _EasyList_.</sup>

#### Setup

1. Ensure the blocker is the only active extension (to avoid results to be polluted by other extensions)
1. Ensure click-to-play (or whatever equivalent) is enabled before launching the benchmark
1. Select the following filter lists in the benchmarked blockers:
    - EasyList
    - Peter Lowe's Ad server list
    - EasyPrivacy
    - Fanboy's Social Blocking List
    - Malware domain lists
    - ABP-specifics: _"Acceptable ads"_ disabled
    - uBlock-specifics: uBlock's filters enabled (+80 filters), extra malware domains (+1,459 filters)

#### Steps

1. Have the benchmarked blocker enabled and properly setup
1. Have only the "new tab" opened
1. Quit Firefox
1. Launch Firefox
1. Paste <http://news.yahoo.com/> in address bar, wait for page to finish loading
1. Open new tab, paste <http://news.google.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.huffingtonpost.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.cnn.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.nytimes.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.foxnews.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.nbcnews.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.dailymail.co.uk/>, wait for page to finish loading
1. Open new tab, paste <http://www.washingtonpost.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.theguardian.com/>, wait for page to finish loading
1. Open new tab, paste <https://news.ycombinator.com/>, wait for page to finish loading
1. Leave the browser idle for two minutes
1. Open new tab, paste `about:memory`, wait for page to finish loading
1. Firefox: Click _"Minimize memory usage"_ button in _"Free memory"_ section
1. Firefox: Click _Measure_ button in _"Show memory reports"_ section
1. Firefox: Write down _"Explicit Allocations"_ value (see notes below) / Chromium: Write down _??_ value

So I did the **exact** above steps for no blocker, ABP, uBlock.

#### Results

- **Firefox**
    - No blocker: **613.55 MB** (reference memory usage)
    - **Adblock Plus** 2.6.6: **625.05 MB** (reference _plus_ 11.5 MB)
    - **??Block** 0.8.2.0: **426.85 MB** (reference _minus_ 186.7 MB, ABP _minus_ 198.2 MB)
- **Chromium**
    - No blocker: **1,169.35 MB** (reference memory usage)
    - **Adblock Plus** 1.8.8: **1,509.05 MB** (reference _plus_ 339.7 MB)
    - **??Block** 0.8.2.0: **1,042.94 MB** (reference _minus_ 126.41 MB, ABP _minus_ 466.11 MB)

**Important:** You can't compare directly the figures between the browsers -- they are taken using different methodology from one browser to the other. The benchmarks are more to compare the figures for various blockers within the same browser.

#### Notes

Tested on Firefox 34 64-bit and Chromium 39 64-bit on Linux Mint. No other extensions were present.

For Firefox, I chose the _"Explicit Allocations"_  figure because as per Firefox, it is "the single best number to focus on" with regard to memory usage.

Without going into details, hardware is i5 quadcore + 8 GB

If other users feel like repeating the tests, it would be nice just to confirm I got everything right.

#### Raw data

<https://github.com/gorhill/uBlock/blob/master/doc/benchmarks/mem-usage-overall-20141224.ods>