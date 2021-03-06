# SharedID - OptOut Proposal

**Purpose:** Support opt-out responsibility for sharedid.org & any publisher using the Prebid sharedid.org UserID module.

**Goal:** To help publishers and consumers manage opt-out of preferences. Sharedid.org will assist publishers by enabling a mechanism for opting out of the 1st (& 3rd) party sharedid cookie space.  A consumer must have confidence that when they opt out of sharedid they opt out of both the 3rd party version and the 1st party version.  We do not expect consumers to understand the difference.

**Description:** A user should not be required to understand the difference between the two sharedID identity spaces (first-party and third-party). Dropping a 1st and 3rd party identity cookie makes opt-out of sharedid.org tracking challenging.  Cookies are only allowed to be written or read by the TLD that set them.  In our case Sharedid.org can remove the 3rd party Sharedid.org cookie but not the sharedid.pub.com, aka the 1st party sharedid cookie. SharedID.org will handle the removal of the publisher's 1st party sharedid cookie by using the 3rd party cookie as a temporary bridge.

**Use Case**

As a viewer of content on the internet, I want to opt out of SharedID tracking, I do not understand the difference between the 1st party version of my SharedID and the 3rd party version, I simply do not want to be tracked by the entity or entities surrogates including publishes leveraging the SharedID’s UserID sub adapter. 

**Requirements**

1. When a user initiates an opt-out request on Sharedid.org, sharedId.org will remove the 3rd party sharedid.org uid, AND all 1st party sharedid.pub.com uids.
   1. Since sharedid.org cannot write directly to a publisher's cookie space, it will remove the uid via the wrapper, and set a “do not track” signal, to be read by the wrapper on subsequent page loads. SharedID.org will do this for all domains loading the SharedID sub-adapter. 
1. Once a user chooses to opt-out, that preference should persist so that if/when they visit a site with the sub-adapter in the future their preferences are respected.
   1. SharedID.org must remove each publisher's 1st party sharedid cookie but may replace it with a cookie signaling to the sub adapter, “this user has opted out.”
© 2020 GitHub, Inc.
