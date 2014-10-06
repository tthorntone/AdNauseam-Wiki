Dynamic filtering, introduced in version 0.7.0.0, allows a user to filter dynamically certain classes of requests. Currently, `script` and `iframe` objects can be dynamically filtered, i.e. filtered on or off without having to create a custom filter.

Dynamic filtering is a useful feature security-wise. For example, blocking 3rd-party `<iframe>` by default would have protected users in the case of the [jQuery.com malware attack](http://www.riskiq.com/resources/blog/jquerycom-malware-attack-puts-privileged-enterprise-it-accounts-risk).

Of course, blocking portion of a page may cause page breakage, sometimes benign, sometimes severe. It is up to the user to choose how to make use of this feature.

![Figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-1.png)

1. to block inline `<script>` tags, i.e. javascript code which is embedded directly in the main document.
2. to block 1st-party `<script>` tags.
3. to block 3rd-party `<script>` tags.
4. to block 1st-party `<iframe>` tags.
5. to block 3rd-party `<iframe>` tags.