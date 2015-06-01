Collection of questions which have been asked, along with the answer I provided, or I would have provided.

Chinese translation of this Wiki: <sup>[中文](https://github.com/fang5566/uBlock/wiki/FAQ)</sup>

#### Does it block Youtube ads?

Because there are are filters to block YouTube ads in EasyList, yes, it will block YouTube ads.

#### Is [_other blocker placeholder_] still needed with uBlock?

It all depends of the filter lists you use, and whether you use dynamic filtering in uBlock. I run benchmarks regarding blocking efficiency, this may help you decide whether you should keep another blocker to complement uBlock, or whether you should drop it and further configure uBlock to block more: [uBlock and others: Blocking ads, trackers, malwares](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares). The [resulting diffs](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares#data-diffs) are particularly useful in making a decision.



#### Fails to block Google Search ads

If you have EasyList enabled, uBlock will block ads in Google Search results.

If you feed uBlock with an invalid cosmetic filter in the _"My filters"_ pane in the dashboard, this will break cosmetic filtering, and a symptom of this is that ads will not be blocked in Google Search results.

#### Is Firefox version considered stable?

Yes.

#### How often are filter lists updated?

Currently, after four days a filter list is deemed "obsolete".

#### How to show the Google text ads?

You can create a whitelist directive *only* for Google Search page. For example, in my case it would be:

    www.google.ca/search*

In your case, just replace `google.ca` with whatever is your Google search domain name.

Whitelist directives are those appearing in the _Whitelist_ tab in uBlock's dashboard, and which serves to disable uBlock completely.

#### Web pages appear only as text

You probably have a bad filter entry in your _"My filters"_ pane in the dashboard. You will have to find it and remove it. For examples, filter entries which look like:

    http:

Will cause that exact problem.

#### The badge count is very high, doesn't this slow down uBlock?

- Open a new document in a plain text editor
- Type "1"
- Notice the text editor's responsiveness
- Replace "1" with "1,000,000"
- Notice the text editor's responsiveness

Sounds absurd? It is. So is the claim that a high badge count slows down uBlock. It's just a _counter_ for the number of blocked network requests.

#### I am worried about stability, should I wait for v1.0?

uBlock is considered stable. The version number is just a convenience to differentiate one release from another one. It doesn't have any more meaning than this.

#### YouTube filtering options à la ABP (or, Facebook filtering options à la ABP)

These filter lists do not come with a Creative Common license, thus uBlock is not shipping with these lists. But you can add them manually as custom filter lists. You can find URLs to various external lists on this page: [Filter lists from around the web](https://github.com/gorhill/uBlock/wiki/Filter-lists-from-around-the-web).

#### Are you paid to develop uBlock?

No.

I like to code, and the reward is to see the resulting work useful to others, sometimes [in unexpected ways](https://www.youtube.com/watch?v=90NsjKvz9Ns).

#### Why not Firefox first instead of Chromium?

In as few words as possible, with as little private matters disclosed:

- Fall 2013
- I am Firefox/NoScript user
- Other user is Chromium/ABP
- Worried about Chromium user not being protected against `iframe` loading freely (as opposed to Firefox/NoScript)
- Looked into Chrome API to just quickly [hack together](https://news.ycombinator.com/item?id=6871331) a homespun `iframe` blocker
