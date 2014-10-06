Dynamic filtering, introduced in version 0.7.0.0, allows a user to filter dynamically certain classes of requests. Currently, `script` and `iframe` objects can be dynamically filtered, i.e. filtered on or off without having to create a custom filter.

Dynamic filtering is a useful feature security-wise. For example, blocking 3rd-party `<iframe>` by default would have protected users in the case of the [jQuery.com malware attack](http://www.riskiq.com/resources/blog/jquerycom-malware-attack-puts-privileged-enterprise-it-accounts-risk). Disabling inline javascript is also often useful to work around anti-blockers behavior on some sites.

Of course, blocking portion of a page may cause page breakage, sometimes benign, sometimes severe. It is up to the user to choose how to make use of this feature.

![Figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-1.png)

The "default" row above refers to the default settings to use for any web site. These default settings will take effect on the site **unless** there are specific settings for the current site, which specific settings appear in the row above.

Columns:

1. to block inline `<script>` tags, i.e. javascript code which is embedded directly in the main document.
2. to block 1st-party `<script>` tags.
3. to block 3rd-party `<script>` tags.
4. to block 1st-party `<iframe>` tags.
5. to block 3rd-party `<iframe>` tags.

![Figure 2](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-2.png)

Color scheme:

- Reddish indicates dynamic filtering in effect.
- Grayish indicates no dynamic filtering in effect.
- Darker red indicates dynamic filtering in effect, bypass default setting.
- Darker gray indicates no dynamic filtering in effect, bypass default setting.

So in the illustration above we have:

- Default settings:
    - Do not block inline `<script>` tags
    - Do not block 1st-party `<script>` tags
    - Block 3rd-party `<script>` tags
    - Do not block 1st-party `<iframe>` tags
    - Block 3rd-party `<iframe>` tags

- Site-specific settings:
    - Block inline `<script>` tags
    - Do not block 3rd-party `<script>` tags

The user interface is not terribly self-explanatory, but I really want to keep it as uncluttered as possible. Once you read the doc here, using dynamic filtering should require no further explanation.