If you plan to manually edit rules for [per-site switches](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-site-based-switches), here is the syntax.

There are currently three per-site switches supported:

- `no-popups`: To block **all** popups.
- `no-strict-blocking`: To disable strict blocking.
- `no-cosmetic-filtering`: To disable cosmetic filtering.

When toggled through the popup UI, these switches will apply only to the current web site. However you can edit them manually using the _"My rules"_ pane in the dashboard.

The syntax is as follow:

    switch-name: hostname state

The switch name must be followed by a column `:`, a space, then the hostname on which the switch must apply. Use `*` as a hostname placeholder to indicate you want the switch to apply everywhere. Following is the state of the switch, which can be `on` or `off`.

When switches share a common hostname ancestor, the most specific wins. For example, if you have:

    no-popups: example.com on
    no-popups: www.example.com off

and you visit `www.example.com`, the "no popups" switch will be turned off (popup allowed unless blocked by a static filter).

All switches are `off` by default, meaning there is no point in creating an entry such as:

    no-popups: www.example.com off

Unless it is to override a related broader entry for which the switch is `on`.