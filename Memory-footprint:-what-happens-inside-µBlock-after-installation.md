1. µBlock will load the default selection of filter lists:
    - This causes short-term memory churning (loading/parsing/sorting/storing), which short-term memory will be garbage-collected eventually
    - All this short term memory churning causes µBlock's baseline memory footprint to grow further
1. After **five minutes**, µBlock will look whether one or more filter list need to be updated
1. If an update is needed, µBlock will flush from memory all filters and reload with the latest version
    - This will causes another round of short-term memory churning, which short-term memory will be garbage-collected eventually
    - Again, all this short term memory churning causes µBlock's baseline memory footprint to grow further
1. After **seven minutes**, assuming no change in selection of filter lists, or change in the content of selected filter lists, µBlock will snap a selfie
    - Generating the selfie also causes short-term memory churning, which short-term memory will be garbage-collected eventually
    - Again, this short term memory churning causes µBlock's baseline memory footprint to grow further
    - Any change in the selection of filter lists, or change in the content of selected filter lists will invalidate µBlock's selfie
1. Even after the growth in memory baseline, µBlock's own memory footprint is still quite smaller than that of Adblock Plus.
1. µBlock's much smaller contributed memory footprint to web pages is much smaller than that of ABP
    - Though this measure is less visible, it's where you get the biggest bang for the buck with µBlock relative to ABP.

