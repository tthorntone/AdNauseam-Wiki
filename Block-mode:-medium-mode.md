Blocking-wise, this is one significant leap from [easy mode](https://github.com/gorhill/uBlock/wiki/Blocking-mode:-easy-mode). However, be ready to accept you will have to un-break web sites, though at a lesser rate than [hard mode](https://github.com/gorhill/uBlock/wiki/Blocking-mode:-hard-mode).

This is where you start to use [dynamic filtering](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering), a feature available only when you tell uBlock Origin that you are an [advanced user](https://github.com/gorhill/uBlock/wiki/Advanced-user-features). Be sure to read [the guide](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering) before, it is assumed that you understand well how dynamic filtering works in order to use effectively medium mode.

Using medium mode will improve significantly your browser performance, and similarly reduce significantly your privacy exposure when compared to easy mode.

##### Characteristics

- Web pages will load significantly faster compared to the [_easy mode_](https://github.com/gorhill/uBlock/wiki/Blocking-mode:-easy-mode).
- Your privacy exposure will be significantly reduced compared to easy mode.
- You no longer depends mostly on 3rd-party filter lists to dictate what is blocked or not.
    - The 3rd-party filter lists are still used to mop up whatever network requests is not blocked in this mode -- so double protection.
- High likelihood of web pages being broken: you have to be ready and willing to fix them when this happen.
    - Keep in mind though that as you build your ruleset for the sites you usually visit, you will spend less and less time fixing web pages.

##### How to enable this mode

_Settings_ pane:
- _I am an advanced user_: checked.

_3rd-party filters_ pane:
- All of uBlock origin's custom filter lists: checked
- _EasyList_: checked
- _Peter Lowe’s Ad server list_: checked
- _EasyPrivacy_: checked
- _Malware Domain List‎_: checked
- _Malware domains_: checked
- All other filter lists: unchecked

_My rules_ pane:
- Add `* * 3p-script block`
- Add `* * 3p-frame block`

##### Tips

If ever you stumble onto a broken site, and if for whatever reason you do not wish to spend time to un-break this particular site, you can easily point-and-click to toggle dynamic filtering off for that site with only one click: it's just a matter of locally _noop_'ing the _3rd-party scripts_ cell (also the _3rd-party frames_ cell if needed). This will cause the specific site to be filtered through static filtering only (i.e. _EasyList_, _EasyPrivacy_, etc.)
