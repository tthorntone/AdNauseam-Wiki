Reminder: the `noop` rule action means that network requests will not be filtered through dynamic filtering, but they will still be filtered through static filtering (_EasyList_, _EasyPrivacy_, etc). 

    # the default-deny rules
    * * 3p block
    * * 3p-frame block

    # Pick whatever you want, or all

    # Global

    # This one is useful if you want to keep the ability to translate
    # any web page using the contextual menu in Chromium:
    * translate.googleapis.com * noop

    # Local

    # arstechnica.com
    arstechnica.com arstechnica.net * noop

    # crowdin.com
    crowdin.com d1ztvzf22lmr1j.cloudfront.net * noop

    # deviantart.com
    deviantart.com deviantart.net * noop

    # economist.com
    www.economist.com static-economist.com * noop

    # facebook.com
    facebook.com akamaihd.net * noop
    facebook.com fbcdn.net * noop

    # foxnews.com
    foxnews.com fncstatic.com * noop

    # github.com
    github.com avatars0.githubusercontent.com * noop
    github.com avatars1.githubusercontent.com * noop
    github.com avatars2.githubusercontent.com * noop
    github.com avatars3.githubusercontent.com * noop
    github.com camo.githubusercontent.com * noop
    github.com cloud.githubusercontent.com * noop
    github.com raw.githubusercontent.com * noop
    github.com render.githubusercontent.com * noop
    # This one is needed to allow auto-upload of images through drag-n-drop
    github.com s3.amazonaws.com * noop

    # huffingtonpost.co.uk
    www.huffingtonpost.co.uk huffpost.com * noop

    # lifehacker.com
    lifehacker.com kinja-img.com * noop
    lifehacker.com kinja-static.com * noop
    lifehacker.com kinja.com * noop

    # marketwatch.com
    www.marketwatch.com mktw.net * noop
    www.marketwatch.com wsj.net * noop

    # medium.com
    medium.com d262ilb51hltx0.cloudfront.net * noop
    medium.com dnqgz544uhbo8.cloudfront.net * noop

    # mozilla.org
    mozilla.org mozilla.net * noop

    # nytimes.com
    nytimes.com nyt.com * noop

    # reddit.com
    reddit.com redditmedia.com * noop
    reddit.com redditstatic.com * noop

    # slashdot.org
    news.slashdot.org fsdn.com * noop

    # stackoverflow.com
    stackoverflow.com sstatic.net * noop

    # techcrunch.com
    techcrunch.com 5min.com * noop
    techcrunch.com wordpress.com * noop
    techcrunch.com wp.com * noop
    techcrunch.com wpcomwidgets.com * noop

    # theguardian.com
    www.theguardian.com guardianapps.co.uk * noop
    www.theguardian.com guim.co.uk * noop
    www.theguardian.com theguardian.tv * noop

    # twitch.tv
    twitch.tv jtvnw.net * noop
    twitch.tv swiftype.com * noop
    twitch.tv ttvnw.net * noop

    # twitter.com
    twitter.com twimg.com * noop

    # yahoo.com
    yahoo.com yimg.com * noop

    # ycombinator.com
    blog.ycombinator.com phaven-prod.s3.amazonaws.com * noop
    blog.ycombinator.com posthaven-assets.s3.amazonaws.com * noop

    # youtube.com
    youtube.com content.googleapis.com * noop
    youtube.com ggpht.com * noop
    youtube.com google.com * noop
    youtube.com googleusercontent.com * noop
    youtube.com googlevideo.com * noop
    youtube.com gstatic.com * noop
    youtube.com plus.googleapis.com * noop
    youtube.com youtube-nocookie.com * noop
    youtube.com ytimg.com * noop

    # wikipedia.org
    wikipedia.org wikimedia.org * noop