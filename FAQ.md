Collection of questions which have been asked, along with the answer I provided, or I would have provided.

#### Does it block Youtube ads?

If there are filters to block Youtube ads in EasyList, then yes, it will block Youtube ads.

#### Is [_other blocker placeholder_] still needed with µBlock?

It all depends of the filter lists you use, and whether you use dynamic filtering in µBlock. I run benchmarks regarding blocking efficiency, this may help you decide whether you should keep another blocker to complement µBlock, or whether you should drop it and further configure µBlock to block more: [µBlock and others: Blocking ads, trackers, malwares](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares). The [resulting diffs](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares#data-diffs) are particularly useful in making a decision.



#### Fails to block Google Search ads

If you have EasyList enabled, µBlock will block ads in Google Search results.

If you feed µBlock with an invalid cosmetic filter in the _"My filters"_ pane in the dashboard, this will break cosmetic filtering, and a symptom of this is that ads will not be blocked in Google Search results.

#### Is Firefox version considered stable?

Yes.

#### Is µBlock related to µTorrent?

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

Will cause that exact problem.

#### I am worried about stability, should I wait for v1.0?

µBlock is considered stable. The version number is just a convenience to differentiate one release from another one. It doesn't have any more meaning than this.

#### YouTube filtering options à la ABP (or, Facebook filtering options à la ABP)

These filter lists do not come with a Creative Common license, thus µBlock is not shipping with these lists. But you can add them manually as custom filter lists. You can find URLs to various external lists on this page: [Filter lists from around the web](https://github.com/gorhill/uBlock/wiki/Filter-lists-from-around-the-web).

#### Are you paid to develop µBlock?

No.

I like to code, and the reward is to see the resulting work useful to others, sometimes [in unexpected ways](https://www.youtube.com/watch?v=90NsjKvz9Ns).