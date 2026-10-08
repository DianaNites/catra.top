---
date: '2026-10-07T11:37:06-06:00'
draft: false
title: 'My Experience (Trying For) Setting Up A Homelab'
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowWordCount: true

url: "/posts/2a74bf3f/my-experience-trying-for-setting-up-a-homelab/"
aliases: [
    "/posts/2a74bf3f",
    "/blog/2a74bf3f/my-experience-trying-for-setting-up-a-homelab/",
    "/blog/2a74bf3f",
]
---

I've been trying to "set up a homelab" for years. For me this really means, well, anything self hosted. Jellyfin, Nextcloud, Immich, a Bluesky PDS, so much as a static site for this blog post which is being written before any site exists, and will be hosted by the "homelab" this post will go on to create.

I dont know if its me, other people, guides, but I've always struggled here. There are lots of guides and "steps", but very little rationale, explanation, justification, "why this way and not that way"; I've always needed to know the rationale, the low-level details, how and why it works, and most of all: How and why its *secure* and *private*. I do not want my devices hacked, my data stolen, and so on, so I need what is sorely missing from most guides: The understanding of what i'm doing to be confident it is secure.

This means, for me, setting up a homelab requires as a first step much in-depth research and learning about networking, reading RFCs on what this shit means, best practice on security and cryptography, ipv4 and ipv6 and dual-mode sockets and NAT and legacy compatibility and firewalls and ports.

This is why I do not yet have a homelab, do not have anything self hosted. My threat model includes other devices on my home's LAN, it includes "evil parent attacks", commonly referred to in industry as "evil maid" attacks, which underscores how common and realistic a threat it is. If you're reading this, you're probably in tech, so you should understand how realistic a threat abusive parents, friends, and partners are, and the kind of damage they can do to unsecured devices on a LAN; For this reason I prefer the term "evil parent".

This led me to my interest in UEFI and Secure Boot, since the state of linux distribution security is abysmal, in particularly fully measured/integrity protected boot, something which is possible and Android has done for years, the kernel can do it, but no distribution does.

To build a homelab I now need to first make a secure linux distribution to run it on. This has spiraled out of control. This is my white whale, a project that many of my other projects and goals ultimate boil down to: Create a secure linux distro. It slightly predates my desire to self host things. When I was young, I used Linux off and on, driven back to windows mostly for games. I briefly used BackTrack linux(fucking lol)(now known as Kali Linux), I daily drove Gentoo off and on over many years before settling down on Arch. My interest in Linux and self-hosting came together at around the same times, intertwined. The specifics of what more secure means, of what best practice is, of what hardware features exist, have evolved over time.

This is even more out of control and over-whelming, and obviously does not get done. But still, I can't give up security, so I need to research best practice for development, and today that means Containers. It means Docker, it means Podman, it means figuring out that podman needs to be treated as an entirely separate container platform rather than a rootless/more secure docker alternative because podman has more spec bugs than it does compatibility, and outright missing important features; It means learning why all those projects say they dont support podman and wont take questions about it, they have good reason to, podman is not up to par, i wasted so much time fighting its many bugs that contradict the specs they implement as well as their own direct documentation. Many of them had been reported years ago, so this demoralized me on the idea of podman. Maybe in a few years.

ANYWAY, Containers. Well containers are annoying, and what the fuck is a kubernetes and a k3s and a minikube? Everything is YAML and Go now, and supply chain attacks on package registries are ramping up so i *really* start caring about security of my environment and pulling packages somewhere that isnt even nominally secured, so what the fuck are Dev Containers? I should be developing in containers, but theyre all so fucking insecure and open by default that theres no point security wise- UH OH now i want to make my own sandbox framework or at least my own more secure Dev Container than the default

But testing and working on that is.. oops, development, chicken and egg, so i dont work on it obviously. I still do not host so much as a static website.

I need to give up. I need to scope down. I need to focus. I need to figure out how to be okay with existing imperfect solutions, and figure out how they can be adapted or isolated or made more secure in a simpler manner, more containers, reverse proxies, go back to networking, just use docker and stop fighting podman, build more dev-tooling and ad-hoc scripts instead of giving up there or deciding they're "unprincipled" and trying to do it some "right way"

The timeline on all the above is probably(definitely) pretty fucky, this is a bad blog post, and doesn't do what it said at the start, and I will not go back to fix that. But it *is* a blog post. The first and only one I've written. If you are reading this, I got over it enough to host a static site, over embarrassment and fear and shame to put something this bad out, and maybe.. maybe more will come. Part 2: *My Experience (Actually) Setting Up A Homelab* (maybe) to come.

Why? I decided while writing the last two paragraphs to just finish it instead of trying to write it as I go on implementing the homelab, which would mean it would never get done. This post is a statement of intent as much as anything else.

## Postscript

I gave up on self hosting a static blog post and put it on github pages. Minimum viable. self host later, blog now. This is the only edit.
