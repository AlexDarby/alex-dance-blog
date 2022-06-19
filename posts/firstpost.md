---
title: Stop fucking around and deploy an SSR blog with StackBlitz, Eleventy, and Netlify. Now.
description: Just getting a blog stood up for the indecisive.
date: 2022-06-15
tags:
  - tech
layout: layouts/post.njk
---

# Summary.

1. Clone the Eleventy [sample project](https://11ty.new/).
2. Change /_data/metadata.json.
3. Change the /posts.
4. Save your workspace to GitHub.
5. Go to [Netlify](https://app.netlify.com/start) and deploy.  

# Expanded.

If you are in decision paralysis about technical choices, what templates and styles to use for your site, hosting, frameworks. Just start here. Let me choose for you. These technologies are not terrible, and 

## 1. Get a web based IDE up and running.

Lets not mess around with a local dev environment. You can always set this up later if you want to get really comfortable with your config. The point of this post is to get us from zero to deployed with as little nonsense in between as possible. 

So there are lots of web based IDE's out there these days, I found [StackBlitz](https://stackblitz.com/) linked from some Vue course I was doing. I have used things like Codepen in the past but hadn't really got my hands dirty with a proper web container environment before. 

If you are comfortable in a VSCode-like environment, you wont have any issues with StackBlitz. There is an open [issue](https://github.com/stackblitz/core/issues/20) for including Vim, but at the time of writing its 5 years old, so don't get your hopes up. you can always use... Vim.

and found that it didn't suck and had quite a few starters available for a swathe of frontend and fullsack frameworks, including Nuxt, SvelteKit and the one I ended up using Eleventy (11ty). I mostly like Eleventy as it feels quite a bit like the excellent Jekyll in terms of static site generation, . 

The [11ty starter project](https://11ty.new/) builds in a couple of seconds and you are ready to do some super basic configuration.


## 2. Fork and configure the Eleventy starter project.

Once we're in the new dev environment, as the splash page in the preview window suggests all we need to do is update the site metadata...

```text/2-3
_data/metadata.json
```

This file contains the core site information which we can amend with our details...

```text/2-3
{
  "title": "Your Blog Name",
  "url": "https://example.com/",
  "language": "en",
  "description": "I am writing about my experiences as a naval navel-gazer.",
  "feed": {
    "subtitle": "I am writing about my experiences as a naval navel-gazer.",
    "filename": "feed.xml",
    "path": "/feed/feed.xml",
    "id": "https://example.com/"
  },
  "jsonfeed": {
    "path": "/feed/feed.json",
    "url": "https://example.com/feed/feed.json"
  },
  "author": {
    "name": "Your Name Here",
    "email": "youremailaddress@example.com",
    "url": "https://example.com/about-me/"
  }
}
```

After the site information is updated we only need to change two more things before moving on to deployment.

Update the 'About' page...

```text/2-3
about/index.md
```

```text/2-3
---
layout: layouts/post.njk
title: About Me
templateClass: tmpl-post
eleventyNavigation:
  key: About Me
  order: 3
---

I am a person that writes stuff.
```

.. and remove the boilerplate posts to create our own...

```text/2-3
posts/
```


## 3. Hook up GitHub, Netlify, and CI/CD.

Right, after a laborious development process, we are finally ready to release our fledgeling site into the wide blue yonder.

If you haven't already you should hook up your StackBlitz project to a GitHub repository through StackBlitz's UI.

Once this is done, we can headover to [Netlify](https://app.netlify.com/start).

Here, if you don't already have Netlify associated with your github account you wil need to grant permissions for Netlify to read the contents of your repo's.



# Next steps...


### Style.

So much choice. From here we can start adding some of our own flare by updating the theme's CSS, installing our own theme, or adding a framework like TailwindCSS with TailwindUI componenets if you want to go hard. 

### Admin.

Configure Netlify's excellent headless CMS. This will allow you to manage and create posts without having to delve into the code unless you want to. They have a ready-to-go [sample](https://templates.netlify.com/template/eleventy-netlify-boilerplate/) you can check out.