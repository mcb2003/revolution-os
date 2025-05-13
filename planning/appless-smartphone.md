# Imagine a Smartphone without Apps ...

This is a document I wrote some months ago in October 2024, before this project was on the table. I think, however, it
provides more detail on my thaughts of the topic of appless operating systems, and could apply to virtually any device
paradime, not just phones. It's just a brain-dump, don't expect deep thaught here! :)

----------------------------------------

Apps these days are a pain! Everybody wants you to download one to "make working with us easier!", so you end up with
bagillions of them, all screaming at you via notifications, all constantly asking for permissions, none of them easy to
find because who has time to organise their home-screen. I say fuck that!

The app model decentralises information that any given user may find to be very important. Why should I have to check 5
different apps to catch up with instant-messaging conversations? Why should I need to switch between a multitude of apps
from different vendors just to doom-scroll social media? And why should I have to hunt down online personas (content
creators, influencers, etc) that I want to follow on each platform individually?

The app model for smartphones is broken. So here's my solution

## Make Providers, not Apps

Providers are sources of data, and collections of commands that can be performed on that data. A YouTube provider, for
instance, would provide timelines of videos, and yes, even ads if you wanted to please our corporate overlords! The
YouTube provider would also provide a list of actions that can be performed on each item in a timeline, for example,
liking, disliking, or watching a video, leaving a comment, or sharing the video's link. Providers could be written for
any service, either by a third-party using that service's API, or by the entity that provides that service, just as apps
we use today.

It would then be the job of the operating environment of the device to aggregate the data sources from all providers
providing similar data (E.G. videos, social media posts, calendar events, etc), and presenting them in a consistent user
interface, with controls on each item to allow the user to execute the actions defined by the provider for each item. Of
course, at the API level, some mechanism for customising the action interface, and indeed the interface of the widget
displaying the item itself, would need to be implemented (perhaps actions could be placed as buttons, in an overflow
menu, or wired directly to tapping or long-pressing via a hints system), but this is an implementation detail.

This idea is not new. Trillion and Adium were doing it 20+ years ago for instant messaging protocols, and
ActivityStreams + ActivityPub (which incidentally may be a good starting point for designing an API around this idea)
have emerged as an interoperable standard that many decentralised social media softwares can use to share data and send
user actions between each other. Where the chat clients of old fell apart was because they lacked the backing of the
providers they were integrating with, who wanted users to use *their* bespoke client software. This indeed is one of the
biggest hurdles to a system like this taking off.

But I'm not done yet.

## What do People Use Apps For?

Applications on any computing device exist to offer the user of said device a way to run experiences custom-made by
different people (individuals or corporations). The potential of apps is pretty much limitless: from games, to sources
of information, to entertainment, to simple helper utilities. There is no doubt that giving users the power to install
arbitrary programs on their device makes that device much more useful.

It would be a shame then, if a device centred around providers, not apps, missed out on this. Would this idea really be
able to show its true merit if the *kinds* of providers that could be developed were a static list, chosen by the
operating system vendor, and implemented as APIs? Would this idea truly live up to my expectations if I limited it to
only the types of experience Apple or Google wants you to have?

I don't think so.

## Build Experiences Instead

The operating environment should provide a way for developers to design new aggregators, that pull data from providers
specifically designed to provide information to them. As a developer, I should be able to, for instance, build a
stock-tracking experience, define a standard, public format in which my experience receives stock ticker information,
and have my experience automatically aggregate this information from several data providers, none of which have to be
developed by me (though they certainly could be).

These third-party experiences should stick to interfaces with providers that already exist where possible, to avoid
fragmentation (otherwise we're back at square 1, where you need to use 5 different experiences to get the same kind of
data from 5 different sources). Perhaps to allow flexibility, the operating environment's API should provide a standard
way for experiences to define extension properties that providers can chose to implement, to better integrate their data
and actions with a specific vendor's experience.

## The General Workflow

With this setup, you no longer install 50 apps when you get a new phone, but 50 different providers, and a few
experiences. Then, when you want to browse social media, you launch the social experience, whether it be provided by
your phone's OS, or a third-party (maybe you like the layout and aesthetics of another developer's social experience over
the stock Android one). Each experience pulls data from all of the logged in providers you have that is able to provide
data in a format that experience understands, so with the social experience, you get a reverse-chronological, or even
recommendations based, timeline of posts).

No longer do you have to worry about which app you normally contact a certain person on. Just open the messages app, and
find their name. You, as the user, no longer have to care what backend service is being used to talk with your friends
(though there will need to be controls for choosing a default route to someone, if for example you have them on multiple
providers).

## All the Same Permissions and Accounts, Less Annoying pop-ups

Users should, of course, be able to choose what data and device permissions are to be shared with each provider and
experience vendor. The benefit to the provider + experience system is that, since I anticipate vendors building
providers that bundle several of their services together, and that users generally choose the same permissions for every
app from the same vendor (for example, they don't want any Google app to have access to their location), with some
exceptions, these permissions only need to be asked for once, at provider install time. Likewise, only one login needs
to be maintained for all services in the bundle. Naturally, people *will* occasionally want to override a permission for
a specific vendor's service, so the operating environment should natively support provider bundling, and allow the user
to set per-service permissions as well.

## Taking Advantage of AI

With a system like this, privacy preserving, on-device machine learning becomes a lot more powerful! Since all the data
is already in standard, machine-readable, non-proprietary formats, ML models could pull data from all providers at once,
and provide functionality such as surfacing the most important notifications and conversations, summarising long-form
content, etc.

## Centralised Search

Likewise, all data could be made searchable from one search bar. No more getting confused as to which search button does
what in an app, it's all findable from one place (of course some compromises would have to be made to preserve user
privacy, and limit the network bandwidth used by searching all providers at once for the same phrase).

## Integrating Your Private Cloud

The traditional app model does support use of home labs and personal server software, but because every app needs to
re-implement an entire sync chain, interface for viewing your data, etc, there is a lot of fragmentation, UIs that are
similar, but different enough to confuse the user, and in general, wasted effort. With the provider + experience model,
projects like NextCloud, Immich, Paperless and others wouldn't have to worry about making a user-friendly graphical
interface to their software, and can do what they do best: building the data storage and processing backend you can run
yourself. The job of the UI goes to the vendors of experiences. This makes the approval factor of using such software
better: if my Immich server automatically integrates with the photos experience I'm already using, I don't even have to
care that that's where the images are coming from, and I'm already used to the interface I use to browse them. Don't
find that interface intuitive? Install a new photo-browsing experience, and it picks up all the same data.
