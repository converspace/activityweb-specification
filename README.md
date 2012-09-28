The Converspace Specification
=============================

A specification for a __personal publishing__ and __distributed social platform__ where __you own all your data__. Kinda like what blogs should have evolved into.

TL;DR
-----
__Converspace allows you to aggregate your public online activity, public activity around the content you publish and follow public activity around resources of interest, in one place, that you control, no matter where it happens on the web.__

Like blogs you publicly publish original content. All public activity (comment, like, share, etc.) around it that happens anywhere on the web is aggregated on your website. When you share third-party resources, all activity around it is aggregated on your and the third-party website. Like social networking sites, you can follow resources and get updates about them. Any public activity (comment, like, share, etc.) you perform on third-party resources happens on your website (irrespective of whether it is initiated on your website via your activity stream or on a third-party website) and notifications are sent to the third-party website for aggregation.



Converspace is built on:
* [PubSubHubbub](https://code.google.com/p/pubsubhubbub/)
* [Activity Streams](http://activitystrea.ms/)
* [Activity Pingback](http://converspace.github.com/activity-pingback/)
* [Activity Dialog](http://converspace.github.com/activity-dialog/)


![Initial Mock](https://raw.github.com/converspace/specification/master/mocks/converspace.png)

Builds on the good parts of what's come before
----------------------------------------------
* Like social networks, it is a platform for both publishing and consuming content.
* Like blogs, it focuses on long-form original content.
* Like social networks, updates are realtime.
* Like social networks, it has no admin panel. There is an unified interface for publishing and consuming content.
* Like social networks, there is the simplicity and immediacy of the always present and inviting textarea for publishing.
* Like microblogging services, meta-data like tags, mentions and replies can be present anywhere in the content and have no special interface elements, just syntax. Titles are optional and part of the syntax.
* Like wikis, content is not temporal. Updates to content is equally important as new content.
* Like asymmetrical social networks, you can follow other resources.
* Like social networks, there is an activity stream.
* Like popular blogging software, is built on LAMP, the least common denominator platform, to facilitate mass-adoption of self-hosting.

Centered around URI addressable resources
-----------------------------------------
* Resources are treated as opaque URIs and you can follow any URI addressable resource for updates.
 * Following a user resource might send updates about all content by that user. Following a category resource might send all updates about all content in that category. Following a website resource might send updates about all content by all users on that website.
* Creation of or updates to a resource, sends out PubSubHubbub notifications to anyone that is subscribed (following) to that resource.
  * Followers will see an activity stream of all updates to resources they are following.
* Any activity (comment, mention, like, share, etc.) performed (using an [Activity Dialog](http://converspace.github.com/activity-dialog/)) on resources will send out an [Activity Pingback](http://converspace.github.com/activity-pingback/) to the resource. 


TODO
----
* Data Portability: Could be done via Atom feeds just like with blogs if there is a way to associate content with all its activities and a way to represent the list of resources being followed as just another content resource.
* Push to and pull from non-compatible services like Twitter via plugins.

Out of scope
------------
* Private messaging
* Client API/Apps

FAQ
---
* __Why not oStatus?__

 [Salmon](http://www.salmon-protocol.org/) and [WebFinger](http://code.google.com/p/webfinger/) seem unnecessarily complex. [Activity Pingback](http://converspace.github.com/activity-pingback/) aims to be the natural successor of [Pingback](http://www.hixie.ch/specs/pingback/pingback).

* __Why not WebIntents?__

 Converspace is about performing all activities on your own site so that you own all your data. WebIntents are about performing specific activities using specific services. You could achieve the same thing [Activity Dialog](http://converspace.github.com/activity-dialog/) does using WebIntents, but that'll mean taking on a lot of unnecessary complexity.

Similar Projects
----------------
* http://tantek.pbworks.com/w/page/21743425/Falcon

Credits
-------
* Mocks built with the awesome freely available web demo of [Balsamiq](http://www.balsamiq.com/).
