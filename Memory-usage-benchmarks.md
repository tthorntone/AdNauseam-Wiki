Just a place for me o keep track of comparative memory usage over time. Screenshot before/after reference benchmark. Great care taken to ensure memory was garbage collected before screenshots taken. To force memory garbage collection, browser left on idle for more than 1 minute, then dev console of each extension opened, _Timeline_ tab, then clicked twice on the trash can icon.

### 18 September 2014

- Chromium 37.0.2062.94 64-bit (Linux)
- µBlock v 0.6.2.1
- AdBlock 2.7.13
- Adblock Plus 1.8.5
- Ghostery 5.4.0
- Disconnect 5.18.15

Before:<br>
![before](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-20140918-before.png)

After:<br>
![after](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-20140918-after.png)

Observations during benchmark:
- AdBlock is *very* CPU intensive. Adblock Plus also, although to a lesser degree compared to AdBlock.

Settings:
- **µBlock v 0.6.2.1**: _EasyList_, _EasyPrivacy_, _Peter Lowe's_, _ Fanboy’s Social Blocking List‎_, all malware lists (3).
- **AdBlock 2.7.13**: _AdBlock custom filters_, _EasyList_, _EasyPrivacy_, _ Fanboy’s Social Blocking List‎_, _Malware protection_.
- **Adblock Plus 1.8.5**: _EasyList_, _EasyPrivacy_, _ Fanboy’s Social Blocking List‎_, Malware Domains_. _Acceptable ads_ not selected.
- **Ghostery 5.4.0**: _Blocking all trackers_. Ghostrank not selected. _Alert bubble_ disabled.
- **Disconnect 5.18.15**: Default settings.

Notes:

I chose to not benchmark AdGuard, because of the privacy issues when enabling _Malware/phishing protection_.