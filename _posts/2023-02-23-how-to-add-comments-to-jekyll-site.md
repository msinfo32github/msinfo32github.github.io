---
title: How to add comments to a jekyll site (with Giscus or utterances!)
date: 2023-02-23 17:30:00 +0100
categories: [website, jekyll,giscus]
tags: [comments,jekyll,website]
---

Jekyll is a wonderful piece of software for static sites, but by default it does not include comments. This is why I have created this guide. It will show you the differences between Giscus and utterances, how to setup GitHub Discussions, configuration and how to use it with a Jekyll site (or any HTML site if you wanted!)

# Credits

- [giscus.app](https://giscus.app/) ([GitHub](https://github.com/giscus/giscus))
- [utteranc.es](https://utteranc.es) ([GitHub](https://github.com/utterance/utterances))

# Pick your software

Giscus and utterances are pretty similar. The only differences is that Giscus uses GitHub Discussions instead of GitHub Issues that utterances uses. Giscus is heavily inspired by utterances, so installation is very similar.

# GitHub Discussion setup

You need to setup a discussion for Giscus/utterances to create a comment section. You can do this by doing the following steps.

In your GitHub repo:

1. **Settings** > General > **Features** sections > Enable **Discussions**
2. Discussions tab > Click the pencil icon
3. Click **New Category** > Set a title (I use **Comments**) > Add a Description (optional) > Select **Announcement** under **Discussion Format** > **Create**

# Configuration

Giscus and utterances have easy to use pages to generate configurations you can input into Jekyll. You can find these pages here.

- [giscus.app](https://giscus.app/) ([GitHub](https://github.com/giscus/giscus))
- [utteranc.es](https://utteranc.es) ([GitHub](https://github.com/utterance/utterances))

![giscus-app](/assets/img/2023-02-23-how-to-add-comments-to-jekyll-site/giscus-app.png)
![utterances-app](/assets/img/2023-02-23-how-to-add-comments-to-jekyll-site/utterances-app.png)

## Giscus Settings

Follow along with the configurations offered on these sites. Giscus configuration is the same as utterances. You just follow the settings under utterances instead of Giscus (and paste the script generated from utterances)

I use Giscus and my settings were:

```yaml
Repository: msinfo32github/msinfo32github.github.io
Page Discussion Mapping: Pathname, Use strict title matching
Discussion Category: Comments
Features: Enable reactions for the main post, Place the comment box above the comments, Load the comments lazily
Theme: Preferred color scheme
```

You will now see a HTML script like the one below:

```html
<script src="https://giscus.app/client.js"
        data-repo="msinfo32github/msinfo32github.github.io"
        data-repo-id="R_kgDOJAMLFA"
        data-category="Comments"
        data-category-id="DIC_kwDOJAMLFM4CUaz8"
        data-mapping="pathname"
        data-strict="1"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="top"
        data-theme="preferred_color_scheme"
        data-lang="en"
        data-loading="lazy"
        crossorigin="anonymous"
        async>
</script>
```

## Add to your site

With Jekyll, you will have previously installed a "theme" (or the default theme). I use [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy)

This can be found by using opening a terminal and running:

```bash
bundle info --path theme
```

Now, navigate to the path from the command above plus `/layouts/post.html`.

Edit 'post.html' and paste the ```<script>``` at the bottom of the file, without removing any content previously there

If you would like to comment this to note what it is, you can use the HTML comment tag like this:

```html
<!-- Comment here!>
```

Copy `post.html` to the directory of your site plus `/_layouts/post.html` (**create this `_layouts` directory if it doesn't already exist!**)

Jekyll will now use this modified version of your `post.html` for all of your posts.

# Test

You can now test this (either running locallly or on a server) by going to the bottom of a post. You should see a box similar to this.

![test-example](/assets/img/2023-02-23-how-to-add-comments-to-jekyll-site/test-example.png)

This will now allow users to sign in with GitHub and comment. It also has Markdown support.

# Conclusion

If there are any further tweaks or any issues, leave them under my GitHub issues [here](https://github.com/msinfo32github/msinfo32github.github.io/issues/) or in the ***comment section below***!