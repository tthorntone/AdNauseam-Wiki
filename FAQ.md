Collection of questions which have been asked, along with the answer I provided, or I would have provided.

#### Does it block Youtube ads?

If there are filters to block Youtube ads in EasyList, then yes, it will block Youtube ads.

#### Fails to block Google Search ads

If you have EasyList enabled, µBlock will block ads in Google Search results.

If you feed µBlock with an invalid cosmetic filter in the _"My filters"_ pane in the dashboard, this will break cosmetic filtering, and a symptom of this is that ads will not be blocked in Google Search results.

#### Is Firefox version considered stable?

Yes.

#### Is µBlock related to uTorrent?

No.

#### How often are filter lists updated?

Currently, after four days a filter list is deemed "obsolete".

#### How to show the google text ads?

You can create a whitelist directive *only* for Google Search page. For example, in my case it would be:

    www.google.ca/search*

In your case, just replace `google.ca` with whatever is your Google search domain name.

Whitelist directives are those appearing in the _Whitelist_ tab in µBlock's dashboard, and which serves to disable µBlock completely.

#### Web pages appear only as text

You probably have a bad filter entry in your _"My filters"_ pane in the dashboard. You will have to find it and remove it. For examples, filter entries which look like:

    http:
    /

Will cause that exact problem.

#### YouTube filtering options à la ABP (or, Facebook filtering options à la ABP)

These filter lists do not come with a Creative Common license, thus µBlock is not shipping with these lists. But you can add them manually as custom filter lists. You can find URLs to various external lists on this pahe: [Filter lists from around the web](https://github.com/gorhill/uBlock/wiki/Filter-lists-from-around-the-web).
