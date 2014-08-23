Just a page to collect my counterarguments when I spot something which I believe deserve countering.

#### Who care about efficiency, I have 8 GB

Doing more with less is a virtue in software. For users of µBlock, this means:

- Page loads faster
- Free to use more filter lists
    - For instance, [ABP warns against using too many filter lists](https://adblockplus.org/en/getting_started#subscription): _"It is important to note that you should not add too many filterlists to Adblock Plus"_
- Free to use a blocker on less powerful devices
    - For instance: [Reddit: _"ABP was a significant burden on my CPU"_](http://www.reddit.com/r/chromeos/comments/298jh1/just_a_tip_try_out_%C2%B5block_for_your_adblocking/)
- Free to use more extensions

Memory and CPU cycles are finite resources. A sure way for a developer to **not** be hired when being interviewed is to dismiss efficiency work because "memory is plentiful" or "CPU nowadays are fast enough".

#### µBlock is a fork of Adblock Plus code

No. Code is wholly original, it was written from scratch. There are a very few places I borrowed code from elsewhere, and this is clearly identified. For example, for the element picker, I [embedded](https://github.com/gorhill/uBlock/blob/master/js/element-picker.js#L27) [CSS.escape](http://mths.be/cssescape) from Mathias Bynens.

#### Adblock Edge is as light as µBlock

No it's not. Adblock Edge is exactly like Adblock Plus, except that it doesn't have the _"Acceptable ads"_ exception filters out of the box. See for yourself: [here](https://bitbucket.org/adstomper/adblockedge/diff/lib/filterClasses.js?diff1=f89367e6ddc7&diff2=a642b932365d9521042cf8fec56089caca496a7d&at=default) is a diff of a code change for Adblock Edge, and [here](https://github.com/adblockplus/adblockplus/commit/384cb64c6d3c2aa698b5f15c9d8aaefd22c889aa#diff-3) is the same exact diff for Adblock Plus. The timestamps shows that Adblock Edge pulled code changes from the Adblock Plus project.