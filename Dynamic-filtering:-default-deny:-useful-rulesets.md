Reminder: the `noop` rule action means that network requests will not be filtered through dynamic filtering, but they will still be filtered through static filtering (_EasyList_, _EasyPrivacy_, etc). 

##### the default-deny rules

    * * 3p block
    * * 3p-frame block

##### arstechnica.com

    arstechnica.com arstechnica.net * noop

##### crowdin.com

    crowdin.com d1ztvzf22lmr1j.cloudfront.net * noop

##### economist.com

    www.economist.com static-economist.com * noop

##### github.com

    github.com avatars0.githubusercontent.com * noop
    github.com avatars1.githubusercontent.com * noop
    github.com avatars2.githubusercontent.com * noop
    github.com avatars3.githubusercontent.com * noop
    github.com camo.githubusercontent.com * noop
    github.com raw.githubusercontent.com * noop
    github.com render.githubusercontent.com * noop

##### mozilla.org

    mozilla.org mozilla.net * noop

##### reddit.com

    reddit.com redditmedia.com * noop
    reddit.com redditstatic.com * noop

##### stackoverflow.com

    stackoverflow.com sstatic.net * noop

##### twitch.tv

    twitch.tv jtvnw.net * noop
    twitch.tv swiftype.com * noop
    twitch.tv ttvnw.net * noop

##### twitter.com

    twitter.com twimg.com * noop

##### youtube.com

    youtube.com content.googleapis.com * noop
    youtube.com ggpht.com * noop
    youtube.com google.com * noop
    youtube.com googleusercontent.com * noop
    youtube.com googlevideo.com * noop
    youtube.com gstatic.com * noop
    youtube.com plus.googleapis.com * noop
    youtube.com youtube-nocookie.com * noop
    youtube.com ytimg.com * noop

##### wikipedia.org

    wikipedia.org wikimedia.org * noop
