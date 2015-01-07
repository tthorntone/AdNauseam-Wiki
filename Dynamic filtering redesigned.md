In µBlock version 0.9.0.0, dynamic filtering has been completely revamped. For a fresh new install of µBlock, this is how the popup UI looks:

![figure 1](https://raw.githubusercontent.com/gorhill/uBlock/fix-433/doc/img/df-tut-01.png)

This is the "novice user" interface, which is the default when installing for the first time. Notice the difference with the previous version:

- The dynamic filtering widgets are not accessible
    - This is to prevent novice users from tampering with dynamic filters without really understandng what it is all about
- The network request logger (the _eye_ icon) is now always available
    - There is no more setting to enable/disable the network request logger, it will be turned on/off automatically when opening/closing the logger page

To access dynamic filtering, you need to indicate to µBlock that you are an advanced user (mind the ["Required reading"](https://github.com/gorhill/uBlock/wiki/Advanced-user-features) link):

![figure 2](https://raw.githubusercontent.com/gorhill/uBlock/fix-433/doc/img/df-tut-02.png)

By the way, notice that the _Statistics_ tab (the network request log) is now gone from the dashboard.

For advanced users, µBlock's popup UI will show a little `+` widget aside the prompt "requests blocked":

![figure 3](https://raw.githubusercontent.com/gorhill/uBlock/fix-433/doc/img/df-tut-03.png)

This little widget allows to expand/collapse the new re-designed dynamic filtering pane. As seen below, just as with previous versions you can still dynamically filter:

- inline scripts
- 1st-party scripts
- 3rd-party scripts
- 3rd-party frames

![figure 4](https://raw.githubusercontent.com/gorhill/uBlock/fix-433/doc/img/df-tut-04.png)

However, as per [issue #282](https://github.com/gorhill/uBlock/issues/282), you can't no longer dynamically filter 1st-party frames -- that was pointless.

Also, I threw in the ability to dynamically filters images (regardless of origin), as I saw this sort of feature requested a couple of places. It's useful for users who wish to save bandwidth, and/or memory resources.

The dynamic filtering consists mainly of three columns. From left to right, they are:

- The name of what is to be dynamically filtered: can be a type of request, or a specific hostname.
- The global rule
- The local rule

Rules color scheme:

- Pale gray: no rule
- Dark red: block rule
    - The requests will be blocked, regardless of whether static exception filters exist
- Dark green: allow rule
    - The requests will be allowed, regardless of whether static block filters exist
- Dark gray: no-op rule
    - To cancel any dynamic filtering, the requests will still be subject to static filtering

![figure 5](https://raw.githubusercontent.com/gorhill/uBlock/fix-433/doc/img/df-tut-05.png)

![figure 6](https://raw.githubusercontent.com/gorhill/uBlock/fix-433/doc/img/df-tut-06.png)