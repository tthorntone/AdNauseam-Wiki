uBlock Origin does not collect any data of any kind.

- uBlock Origin has no home server.
- uBlock Origin doesn't embed any kind of analytic hooks in its code.

uBlock Origin will download the resource at `https://raw.githubusercontent.com/uBlockOrigin/uAssets/master/checksums/ublock0.txt?_=[unix time stamp in ms]`

- when you visit the _3rd-party filters_ pane in the dashboard;
- once in a while if you have _Auto-update filter lists_ checked;

... to find out whether some assets used by uBlock Origin need to be updated.

The purpose of the "unix time stamp in ms" portion of the URL is to be sure the browser cache is bypassed.

The servers behind `githubusercontent.com` are owned by GitHub, Inc., and thus are unrelated to uBlock Origin, so even if I was interested in analytics (which I am not), I have no access to whatever data is logged by `githubusercontent.com`.

That is all.