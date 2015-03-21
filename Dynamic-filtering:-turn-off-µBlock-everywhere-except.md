[Back to "Dynamic-filtering"](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)

***

How to achieve "blacklist mode", these are the steps:

- global allow `all` cell
    - "global" = 1st column
    - "allow" = green

![c](https://cloud.githubusercontent.com/assets/585534/6042159/8a1df142-ac50-11e4-8129-6edbb664d801.png)

Nothing will be blocked, static filtering is completely bypassed: "green" means "allow unconditionally".

To "blacklist" a specific site:

- local noop `all` cell
    - "local" = 2nd column
    - "noop" = dark gray

This will cause the current site to become subjected to static filtering (EasyList, EasyPrivacy etc, i.e. whatever filter lists is in effect).

![a](https://cloud.githubusercontent.com/assets/585534/6042165/8f6bd6d2-ac50-11e4-8551-c2a17c05d917.png)

Dynamic filtering disengaged for current site: "gray" means disengage dynamic filtering, but apply static filtering.

In the screenshots above, 3rd-party frames are blocked to remind this is a good habit in general, and to illustrate that narrower dynamic rules prevails over more generic ones.