Activity Web Specification
==========================

A specification for a __personal publishing__ and __distributed social platform__ where __you own all your data__. Kinda like what blogs should have evolved into.

[Converspace](https://converspace.org) will be an open-source reference implementation of this specification in PHP+Mysql.

TL;DR
-----
__Activty Web allows you to aggregate your public online activity, public activity around the content you publish and follow public activity around resources of interest, in one place, that you control, no matter where it happens on the web.__

Like blogs you publicly publish original content. All public activity (comment, like, share, etc.) around it that happens anywhere on the web is aggregated on your website. When you share third-party resources, all activity around it is aggregated on your and the third-party website. Like social networking sites, you can follow resources and get updates about them. Any public activity (comment, like, share, etc.) you perform on third-party resources happens on your website (irrespective of whether it is initiated on your website via your activity stream or on a third-party website) and notifications are sent to the third-party website for aggregation.



Activity Web is built on:
* [PubSubHubbub](https://code.google.com/p/pubsubhubbub/)
* [Activity Streams](http://activitystrea.ms/)
* [Activity Pingback](http://activitypingback.org/)
* [Activity Dialog](http://activitydialog.org/)

Imagine
-------
* You write an article on your website about the technology behind your startup.
* Someone that follows you via [PubSubHubbub](https://code.google.com/p/pubsubhubbub/), discovers the article and shares it on [Hacker News](http://news.ycombinator.com/).
* If Hacker News supports the simple [Activity Pingback Specification](http://activitypingback.org/)
 * your website will receive a notification about your article being shared there.
 * anytime someone comments on the shared link on Hacker News, your website will receive a notification about the comment on Hacker News.
 * Your website will show you these notification as an activity stream on your website.
 * Comments on Hacker News will appear inline on your website on the relevant article and you can reply to them from your website itself.
* If Hacker News also supports the simple [Activity Dialog Specification](http://activitydialog.org/), any action you want to perform on Hacker News posts like upvote, comment, share, etc. will actually be performed on your website, appear on the activity stream on your website and then a notification will be sent out to Hacker News about it.

![Initial Mock](https://raw.github.com/converspace/activity-web/master/mocks/converspace.png)

Builds on the good parts of what's come before
----------------------------------------------
* Like social networks, it is a platform for both publishing and consuming content.
* Like blogs, it focuses on long-form original content.
* Like social networks, updates are realtime. ([PubSubHubbub](https://code.google.com/p/pubsubhubbub/))
* Like social networks, it has no admin panel. There is an unified interface for publishing and consuming content.
* Like social networks, there is the simplicity and immediacy of the always present and inviting textarea for publishing.
* Like microblogging services, meta-data like tags, mentions and replies can be present anywhere in the content and have no special interface elements, just syntax. Titles are optional and part of the syntax.
* Like wikis, content is not temporal. Updates to content is equally important as new content.
* Like asymmetrical social networks, you can follow other resources. ([PubSubHubbub](https://code.google.com/p/pubsubhubbub/))
* Like social networks, there is an activity stream. ([Activity Streams](http://activitystrea.ms/), [Activity Pingback](http://activitypingback.org/))
* Like popular blogging software, is built on LAMP, the least common denominator platform, to facilitate mass-adoption of self-hosting.

Centered around URI addressable resources
-----------------------------------------
* Resources are treated as opaque URIs and you can follow any URI addressable resource for updates.
 * Following a user resource might send updates about all content by that user. Following a category resource might send all updates about all content in that category. Following a website resource might send updates about all content by all users on that website.
* Creation of or updates to a resource, sends out PubSubHubbub notifications to anyone that is subscribed (following) to that resource.
  * Followers will see an activity stream of all updates to resources they are following.
* Any activity (comment, mention, like, share, etc.) performed (using an [Activity Dialog](http://activitydialog.org/)) on resources will send out an [Activity Pingback](http://activitypingback.org/) to the resource. 


TODO
----
* Data Portability: Could be done via Atom feeds just like with blogs if there is a way to associate content with all its activities and a way to represent the list of resources being followed as just another content resource.
* Push to and pull from non-compatible services like Twitter via plugins.


Out of scope
------------
* __Private messaging__: Since Activity Web is aiming to be the natural successor of blogging, it is only concerned with public conversations and activities.
* __Client API/Apps__: IMO, a protocol/standard for distributed social activities should treat URIs opaquely (and not get into application API space) to allow for interop with existing software. Client APIs can be varied as long as you have data portability, similiar to the blogging space (you might have different client APIs for wordpress and drupal for building clients, but they interop at the data level using ATOM/RSS).


FAQ
---
* __Why not OStatus?__

 [OStatus](http://ostatus.org/) is built on procotols that I don't consider easy to implement (see [Watch, trust, friend](http://markpasc.typepad.com/blog/2011/03/watch-trust-friend.html)). An explicit goal of [Activity Pingback](http://activitypingback.org/) is to be easy to implement to encourage adoption.

* __Why not WebIntents?__

 Activity Web is about performing all activities on your own site so that you own all your data. WebIntents are about performing specific activities using specific services. You could achieve the same thing [Activity Dialog](http://activitydialog.org/) does using WebIntents, but that'll mean taking on a lot of unnecessary complexity.


Similar Projects
----------------
* http://tantek.pbworks.com/w/page/21743425/Falcon


See also
--------
* [OStatus](http://ostatus.org/)
* [Tent.io](http://tent.io/)
* [Pump.io](http://pump.io/) ([API](https://github.com/e14n/pump.io/blob/master/API.md))
* [Watch, trust, friend](http://markpasc.typepad.com/blog/2011/03/watch-trust-friend.html)
* [Private Webhooks. Private Feeds.](http://blog.romeda.org/2011/03/private-webhooks-private-feeds.html)


Credits
-------
* Mocks built with the awesome freely available web demo of [Balsamiq](http://www.balsamiq.com/).