---
date: '2026-10-08T15:26:51Z'
draft: false
title: 'My Experience (Setting Up Hugo)'
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowWordCount: true

url: "/blog/d2042b1d/setting-up-hugo/"
aliases: [
    "/blog/d2042b1d",
]
---

The astute may have noticed, this blog is on Hugo and PaperMod. A common choice. A sensible choice. A Just Works choice. It wasn't hard. So why hasn't this one before? Because, just like [My Homelab][exp]. Hugo has been pretty nice to use actually. Same for PaperMod. It looks nice, it Just Works, and it gets this one started.

But there are many theme options to choose from, and the choice between Zola and Hugo. Writing this is making it look at Zola themes and fuck they're looking pretty nice and making it want to switch. Maybe. Now that something exists to fall back to. It probably would have been fine just deciding to use Zola and- *see this is the trap, and what?* PaperMod, in this one's mind, is the classic default-choice hugo theme that It ended up falling back on, but what is Zola's and does It even like it?

Anyway. So this one sucked it up and decided on *something*, and this is the result. But even then, this isnt exactly default hugo and papermod, you may have noticed this one's posts have IDs in their URL. The first thing It did when deciding to use Hugo and PaperMod, with no prior experience with them and so concurrent with setting them up and learning enough to *Get A Post Out:tm:*, It was immediately fighting against the fact that titles are URLs.

This wasn't actually too difficult to solve. The magic that makes this happen is 3 lines in the archetye.

```yaml
{{ $id := substr (now.UnixNano | sha1) 0 8 -}}
url: "/{{.Section | urlize}}/{{ $id }}/{{ .Name | urlize }}/"
aliases: ["/{{.Section | urlize}}/{{ $id }}"]
```

This gives every post a canonical URL, with an automatic random ID because how many posts a nanosecond do you think are being made, independent of its title, which will html redirect to the SEO url with the title in it.

This one wanted this so It could potentially change titles with no breakage and without worry of title collisions. The title can always be changed and the previous one added as an alias, and even if it isnt, if you just try removing the title from the URL so its just the ID, it'll work. It often has to do this for old or broken links, and it often works, so this one assumes others do too.

This causes hugo to create stub pages with redirects in `<head>`. Since this is a static site, this is the best they can do, which does have UX conseuqneces; Social cards dont work because those are only on the main page, browsers have to load and parse the html page to know to redirect it, and so such.

This is an acceptable trade-off for now. So are social cards. It could probably modify papermod to insert social card stuff into the stub pages so that It can social-post the stable ID link *and* have the canonical URL include the title text, keeping the nice cards on the stable id.

Is this the "best" way to do this? The "right" way? It didnt ask and didnt care, It just did *something*. If this one wants to get anything out, and It does, then It has to learn when and how to make that trade off. This is blog post number two, so Progress has been made.

[exp]: /blog/2a74bf3f
[zola-themes]: https://www.getzola.org/themes/
