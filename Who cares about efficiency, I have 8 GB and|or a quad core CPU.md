Doing more with less is a virtue in software. For users of µBlock, this means:

- Less CPU churn when loading a web page, which may translate into noticeable faster page load.
- Higher memory consumption correlates with higher CPU-cycle consumption: whatever extra memory is used is memory which has to be allocated/written to/read from (at least once)/garbage collected.
- Free to use [more filter lists](https://github.com/gorhill/uBlock/wiki/Filter-lists:-gorhill):
    - For instance, [ABP warns against using too many filter lists](https://adblockplus.org/en/getting_started#subscription): _"It is important to note that you should not add too many filterlists to Adblock Plus"_
- Longer battery life: each time unit, however small, in which the CPU is idle rather than churning translates into extended battery life.
- Free to use a blocker on less powerful devices
    - For instance: [Reddit: _"ABP was a significant burden on my CPU"_](http://www.reddit.com/r/chromeos/comments/298jh1/just_a_tip_try_out_%C2%B5block_for_your_adblocking/)
- Free to use more extensions

Memory and CPU cycles are finite resources. A sure way for a developer to **not** be hired when being interviewed is to dismiss efficiency work because "memory is plentiful" or "CPU nowadays are fast enough".

Not convinced yet? Ok, just try this not very complicated web page: http://watchseries.ag/#.

First with Adblock Plus. Refresh many times. Notice the result. Then try with µBlock. Refresh many times. **Do you see the difference?**