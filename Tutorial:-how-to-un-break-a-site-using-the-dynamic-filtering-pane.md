Real, concrete case: [issue #1323](https://github.com/gorhill/uBlock/issues/1323), also reported on [ABP forum](https://adblockplus.org/forum/viewtopic.php?f=2&t=43736):

>  On money.cnn.com, the comments section is being blocked by a filter 
list blocking rule.  I would appreciate it if someone could suggest an 
exception rule that works in Adblock Plus

From what I gathered, the user had _Fanboy’s Annoyance List‎_ enabled. With ABP, users are told to use the _Blockable items_ pane to un-break pages broken by one or more static filters, by disabling one or more filters.

In uBlock Origin ("uBO"), it is not possible to disable specific static filters, un-breaking pages is done in different ways: In uBO one does not _disable_ a static filter, one _overrides_ a static filter, and this can be done on a per-site basis. I will illustrate how to do it here using the dynamic filtering pane -- this is the easiest way.

The page which was reportedly broken would not properly render comments:

<img src="https://csa-discourse-uploads.s3-us-west-1.amazonaws.com/original/2X/b/bce1d6fb0cdcb91795d0bbce900d0b4fefbbe476.png" width="645" height="499">

uBO's popup panel reports that 30 network requests were blocked on the page:

<img src="https://csa-discourse-uploads.s3-us-west-1.amazonaws.com/original/2X/7/780715c19e7b97b91afddb0a4b28f86307b3c61c.png" width="645" height="499">

You can fix yourself the issue, and at the same time contribute some investigation work to help narrow the cause of why the page is broken -- the comments section in the current case.

First, enable the _"I am an advanced user"_ mode in the dashboard:

<img src="https://csa-discourse-uploads.s3-us-west-1.amazonaws.com/original/2X/1/1511e067d82d801901ddcb572c7c3776ab23709e.png" width="645" height="499">

This will give you access to the dynamic filtering pane in the popup panel. By default, there are no rules present in the dynamic filtering pane, which means it does not affect at all what is blocked/allowed:

<img src="https://csa-discourse-uploads.s3-us-west-1.amazonaws.com/original/2X/4/4a2649f2a37cea840a1010db94dde35b5f582363.png" width="645" height="499">

You can see a list of domain names, with each domain name followed by two cells: the first one is for global rules, the second one is for local rules. For the current case, we will only care about local rules. Local rules are those which apply _only_ to the current site , and we are only interested in un-breaking the current site. The cells for the local rules show whether network requests were allowed/blocked using pluses/minuses.

Now if you scroll down the list of domains, you can see a lot of network requests were blocked, and surely one of the blocked network requests is responsible to cause the comments section from not being rendered.

At this point, there is no magick trick to know beforehand which domain(s) is responsible for making the comments appear properly -- a trial and error approach must be used. Experience helps. For example in the current case, one may notice that network requests to `s3.amazonaws.com` were blocked, and an experienced user may consider this anomalous.

In such case, it's worth to try to bypass whatever static block filters blocked the network requests to `s3.amazonaws.com`:

<img src="https://csa-discourse-uploads.s3-us-west-1.amazonaws.com/original/2X/c/c6e2c53195dcd55f36a96271daea83deff8f5b2e.png" width="645" height="499"> 

The picture above shows a local `allow` rule being set for `s3.amazonaws.com`. "Local" here means the rule will apply _only_ for the current site (`http://money.cnn.com/`).

If you hover the mouse pointer over the local rule cell for `s3.amazonaws.com`, you will see that you can set one of three rules: `allow`, `noop` or `block`. Rules in the dynamic filtering pane _always_ override static filters in effect for a given domain.

Possible rules:
- `allow`: always allow network requests, disregard all block static filters (green).
- `noop`: ignore for now -- this belongs to another topic (gray).
- `block`: always block network requests, disregard all exception static filters (red).

Reloading the page with the newly created `allow` rule for `s3.amazonaws.com` will show that the comments section and other parts on the page now render properly:

<img src="https://csa-discourse-uploads.s3-us-west-1.amazonaws.com/original/2X/5/59edafb214ddcc671211aa1ee67aeb47e008ca3d.png" width="645" height="499">

This is an example of how you can un-break a site yourself using point-and-click in uBO's popup panel (and trial-error until you find the proper rule). Things to keep in mind:

All rules you set in the dynamic filtering pane are temporary by default:

- You can erase all temporary rules currently set in the pane using the eraser icon.
- You can persist the temporary rules currently set in the pane using the padlock.

The rules being temporary by default is very convenient when trying to find out which set of rules un-break a site, you can commit the proper rules once you find out what works.

Once you succeed in un-breaking a site, you can report the issue to the filter list maintainers that a site was broken -- so that the fix can benefit everybody. In such case it is useful to report:

- A specific URL where the breakage can be seen (`http://money.cnn.com/video/news/2016/01/29/fox-news-gop-debate-trump-election.cnnmoney?iid=EL`).
- A description of what is broken ("comments are not rendered").
- The filter lists in use ("EasyList, EasyPrivacy, Fanboy’s Annoyance List‎, etc.)
- How you fixed the issue ("allowing network request to `s3.amazonaws.com` fixed the issue")

It is possible to find out exactly which filter(s) in which filter list(s) was causing the breakage, but this is for another topic.