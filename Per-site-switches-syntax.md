If you plan to manually edit rules for [per-site switches](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-site-based-switches), here is the syntax.

There are currently three per-site switches supported:

- `no-popups`: To block **all** popups.
- `no-strict-blocking`: To disable strict blocking.
- `no-cosmetic-filtering`: To disable cosmetic filtering.

When toggled through the popup UI, these switches will apply only to the current web site. However you can edit them manually using the _"My rules"_ pane in the dashboard.

The syntax is as follow:

    switch-name: hostname state

The switch name must be followed by a column `:`, a space, the the hostname on which the switch must apply. Use `*` to indicate you want the switch to apply everywhere. Following is the state of the switch, which can be `on` or `off`.