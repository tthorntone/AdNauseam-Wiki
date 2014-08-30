I've seen a couple of feedbacks in the store of people who wish it was possible to whitelist a web site, i.e. to disable µBlock on a specific web site.

The feature is already available, it is the big power button: it serves to whitelist the current web site, its state will be remembered next time you visit the web site.

![µBlock's popup](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png)

### Tips

If you press the `Ctrl` key as you click the power button, this will whitelist only the current web page, not the whole site (true since [version 0.3.2.0](https://github.com/gorhill/uBlock/releases/tag/0.3.2.0))

Also, you can whitelist a section of a web site. This can currently only be done by editing manually your whitelist. If you add an asterisk `*` at the end of a URL, all the pages which **starts** exactly with that URL will be whitelisted.