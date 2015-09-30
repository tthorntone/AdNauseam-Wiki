There are many ways to block script tags from executing in uBlock Origin:

- Block external script resources.
- Block all inline script tags<sup>[1]</sup> at once.

uBlock Origin 1.2.0 introduces a new way to block **specific** inline script tag in a web page through a new script tag cosmetic filter:

    example.com##script:contains(...)

Where the value inside the parenthesis in `contains(...)` can be a plain string or a literal javascript regular expression (`/.../`). A script tag cosmetic filter will prevent the execution of whatever javascript inside a **specific** script tag when there is a match, i.e. when the plain text or the regular expression is found inside the script tag.

***

- [1] Inline script tags are those which are embedded in the main web page. An example using an excerpt from the front page of Hacker News:<br>
  ```<html op="news"><head><meta name="referrer" content="origin"><link rel="stylesheet" type="text/css" href="news.css?YL5ocwvpNdWX9tuUw2kw"><link rel="shortcut icon" href="favicon.ico"><link rel="alternate" type="application/rss+xml" title="RSS" href="rss"><script type="text/javascript">
        function hide(id) {
            var el = document.getElementById(id);
            if (el) { el.style.visibility = 'hidden'; }
        }
        function vote(node) {
            var v = node.id.split(/_/);
            var item = v[1];
            hide('up_'   + item);
            hide('down_' + item);
            var ping = new Image();
            ping.src = node.href;
            return false;
          }
    </script>
    <title>Hacker News</title>
    </head>
    <body>...
  ```