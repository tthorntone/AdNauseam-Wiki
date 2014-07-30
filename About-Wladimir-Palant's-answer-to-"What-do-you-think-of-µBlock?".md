I see Wladimir Palant has again commented on µBlock [in his comment section](https://palant.de/2014/07/29/which-is-better-adblock-or-adblock-plus#c000761), in response to a someone asking "What do you think of µBlock?":

> Didn’t have a chance to look at it yet. So far the author has been posting proposals that were supposed to fix all that is wrong with Adblock Plus but always failed to consider some scenarios. These proposals also had a clear tendency to trade performance for memory use. It seems that he gave up taking to the stupid Adblock Plus developers and rolled his own.

This has been a pattern with Wladimir Palant with regard to my work. [Outright misrepresentation](https://github.com/gorhill/httpswitchboard/wiki/Adblock-Plus-memory-consumption), or criticism through vague statements while never specific enough to understand what part of the code he is referring to.

- What "proposals" is he specifically referring to?
- What specific "scenarios" is he referring to?

Conveniently for him, I just don't know how to comment specifically technical aspects in response to vague statements. How does one do that?

Also, nowhere in the code did I trade _"performance for memory use"_, both memory use and CPU use have always been of highest concern. Given that my [benchmarks](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-vs.-ABP:-efficiency-compared) show µBlock does _significantly_ better than ABP on both memory and CPU count, vaguely stating that _"clear tendency to trade performance for memory use"_ is just plain nonsense.

I [did ask him to be specific](https://bugzilla.mozilla.org/show_bug.cgi?id=988266#c43) about his statement regarding how I implemented element hiding without injecting gigantic CSS stylesheet in every page and frame, but never received a response, and it is understandable why: he was [misrepresenting the solution](https://bugzilla.mozilla.org/show_bug.cgi?id=988266#c39): nothing in my implementation was "broken", and his supposed worries about page hanging are beyond ridiculous given that's it's exactly the result of ABP's solution, which is to inject unconditionally 13,000 CSS rules in every page and every frame on a page (even more if you are using extra lists aside _EasyList_).

Despite this misrepresentation, apparently I am supposed to feel bad for "[giving] up taking" to Adblock Plus developers. The use of "gave up talking" also seems to imply that not talking to ABP developers before implementing alternative solutions to what ABP is trying to solve is somehow abnormal.