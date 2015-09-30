The ability to filter specific inline script tag started with uBlock Origin 1.2.0.

There are many ways to block script tags from executing in uBlock Origin:

- Block external script resources.
- Block all inline script tags<sup>[1]</sup> at once

***

- [1] Inline script tags are those which are embedded in the main web page. Example using an excerpt from the front page of Hacker News:<br>
  ```<html op="news"><head>
      <meta name="referrer" content="origin">
          <link rel="stylesheet" type="text/css" href="news.css?YL5ocwvpNdWX9tuUw2kw">
          <link rel="shortcut icon" href="favicon.ico">
          <link rel="alternate" type="application/rss+xml" title="RSS" href="rss">
    <script type="text/javascript">
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