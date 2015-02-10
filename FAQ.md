Collection of question which has been asked, along with the answer I provided.

#### How often are filter lists updated?

Currently, after four days a filter lists is deemed "obsolete".

#### YouTube filtering options à la ABP (or, Facebook filtering options à la ABP)

These filter lists do not come with a Creative Common license, thus µBlock is not shipping with these lists. But you can add them manually as custom filter lists. Here are the URLs:

- <https://easylist-downloads.adblockplus.org/fb_annoyances_full.txt>
- <https://easylist-downloads.adblockplus.org/fb_annoyances_sidebar.txt>
- <https://easylist-downloads.adblockplus.org/fb_annoyances_newsfeed.txt>
- <https://easylist-downloads.adblockplus.org/yt_annoyances_full.txt>
- <https://easylist-downloads.adblockplus.org/yt_annoyances_comments.txt>
- <https://easylist-downloads.adblockplus.org/yt_annoyances_suggestions.txt>
- <https://easylist-downloads.adblockplus.org/yt_annoyances_other.txt>

#### How to show the google text ads?

You can create a whitelist directive *only* for Google search page. For example, in my case it would be:

    www.google.ca/search*

In your case, just replace `google.ca` with whatever is your Google search domain name.

Whitelist directives are those appearing in the _Whitelist_ tab in µBlock's dashboard, and which serves to disable µBlock completely.