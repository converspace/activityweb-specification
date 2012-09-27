Converspace
===========

A __personal publishing__ and __distributed social platform__ where __you own all your data__. Kinda like what blogs should have evolved into.

TL;DR
-----
Converspace allows you to aggregate your public online activity, public activity around the content you publish and follow public activity around resources of interest, in one place, that you control, no matter where it happens on the web.

Like blogs you publicly publish original content. All public activity (comment, like, share, etc.) around it that happens anywhere on the web is aggreggated on your website. When you share third-party resources, all activity around it is aggregated on your and the third-party website. Like social netwroking sites, you can follow resources and get updates about them. Any public activity (comment, like, share, etc.) you perform on third-party resources happens on your website (irrespective of whether it is initiated on your website via your activity stream or on a third-party website) and notifications are sent to the third-party website for aggregation.



Connverspace is built on:
* [PubSubHubbub](https://code.google.com/p/pubsubhubbub/)
* [Activity Streams](http://activitystrea.ms/)
* [Activity Pingback](http://converspace.github.com/activity-pingback/)
* [Activity Dialog](http://converspace.github.com/activity-dialog/)


![Initial Mock](https://raw.github.com/converspace/specification/master/mocks/converspace.png)

Converspace builds on the good parts of what's come before
----------------------------------------------------------
* Like social networks, it is a platform for both publishing and consuming content.
* Like blogs, it focuses on long-form original content.
* Like social networks, updates are realtime.
* Like social networks, it has no admin panel. There is an unified interface for publishing and consuming content.
* Like social networks, there is the simplicity and immediacy of the always present and inviting textarea for publishing.
* Like microblogging services, meta data like tags, mentions and replies have no special interface elements, just syntax. Even titles are part of the syntax.
* Like wikis, content is not temporal. Updates to content is equally imporant as new content.
* Like asymmetrical social networks, you can follow other resources.
* Like social networks, there is an activity stream.


Converspace is:
---------------
* Admin-less (does not have an admin interface).
* Built on LAMP, the least common denominator platfrom, to facilitate mass-adoption of self-hosting.
* Like a blog that allows publishing of content of any size or type (long-form, mirco-updates, videos & photos using oembed, links, quotes) via a single textarea.
  * Titles are optional and are part of the syntax (markdown?)
  * #tags are part of the syntax and can be present anywhere in the content (like twitter)
  * Any URI mentioned in the content will be sent a notification (see below). Is agnostic to the types of things being mentioned. Which means even other users are mentioned via URIs (kinda like linking to the other users blog when you wrote about them, in the good old days of blogging).
* Like twitter/facebook in that it will show an ActivityStream.
* Centered around resources (addressable using a URI), not users and/or content. 
  * You can follow any resource for updates. Resource could be hierarchical. e.g. subscribing to a category will send updates to any posts in it, subscribing to the whole site will send updates to any post on it. 
  * Creation of or updates to a resource sends out PubSubHubbub notifications to anyone that is subscribed (following).
  * Followers will see a stream of all updates to resource they are following.
    * So a user has 3 views
      * All their content
      * Their own activity stream onsite and offsite (via [Activity Dialog](http://converspace.github.com/activity-dialog/))
      * Activity stream of resources they are following.
  * Followers can comment on or mention resources in their content or like/share resources in their following activity stream.
    * This will send out an [Activity Pingback](http://converspace.github.com/activity-pingback/) to each of the resources in the content with an ActivityStream payload describing the activity (comment, mention, like, share, etc.)

TODO
----
* Data Portability: Could be done via Atom feeds or might require an API.
* Apps: Requires an API + oAuth (or something like it).

FAQ
---
* __Why not oStatus?__

 [Salmon](http://www.salmon-protocol.org/) and [WebFinger](http://code.google.com/p/webfinger/) seem unnecessarily complex. [Activity Pingback](http://converspace.github.com/activity-pingback/) aims to be the natural successor of [Pingback](http://www.hixie.ch/specs/pingback/pingback).

* __Why not WebIntents?__

 Converspace is about performing all activities on your own site so that you own all your data. WebIntents are about performing specific activitites using specific services. You could achieve the same thing [Activity Dialog](http://converspace.github.com/activity-dialog/) does using WebIntents, but that'll mean taking on a lot of unnecessary complexity.

Credits
-------
* Mocks built with the awesome freely available web demo of [Balsamiq](http://www.balsamiq.com/).
