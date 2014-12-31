### Type-based rules

Type-based rules are used to filter specific types of request on a web page. There currently exists five types of request which can be dynamically filtered:

- images
- inline scripts
- 1st-party scripts: scripts which are pulled from the same domain name of the current web page
- 3rd-party scripts: scripts which are pulled from a different domain name than that of the current web page
- 3rd-party frames: frames elements which are pulled from a different domain name than that of current web page

These rules can apply everywhere, or be specific to a web site. For instance blocking 3rd-party frames is a very good habit security-wise: `* * 3p-frame block`. This rule translates into "block 3rd-party embedded frames everywhere".

Another example: `wired.com * image block`, which means "block all images when visiting a web page on wired.com".

### Hostname-based rules