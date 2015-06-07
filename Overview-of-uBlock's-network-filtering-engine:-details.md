#### Overview

[Overview of uBlock's network filtering engine](https://github.com/gorhill/uBlock/wiki/Overview-of-uBlock's-network-filtering-engine)

#### Dynamic URL filtering rules

Advantages:
- Little overhead creating/deleting dynamic URL rules.
- Precedence over both dynamic filtering rules and static filters.

Disadvantages:
- Can only match URLs which "start with".
- Can't be loaded from a filter list.

#### Dynamic filtering rules

Advantages:
- Little overhead creating/deleting dynamic rules.
- Precedence over static filters.

Disadvantages:
- Rules are broad: whole sites or class of types.
- Can't be loaded from a filter list.

#### Static filtering

Advantages:
- Flexible syntax: from very broad to very narrow targeting.
- Support cosmetic filtering (removal of DOM elements).
- Can be loaded from a filter list: facilitate community-supported filter lists.
- Compatibility: can be used in other blockers supporting ABP-compatible filter syntax.
    - Except for a few filter syntax extensions specific to uBlock not adopted by other blockers.

Disadvantages:
- High overhead creating/deleting network/cosmetic filters (high memory churn).
- In case of 3rd-party filter lists, forced to use all filters, including those which may not be wanted.