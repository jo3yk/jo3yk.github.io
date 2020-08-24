---
layout: post
title:  "Adding a plugin to Jekyll"
date:   2020-08-24
categories: jekyll github-pages plugins jemoji
---

Jekyll is nice as it stands, but before long you'll likely find something missing. Luckily, it supports plugins so you can extend the functionality. Existing plugins are easy to install as Ruby gems, or you can create your own.

Let's start by installing a plugin to support emojis. There are a few out there, but we're slightly restricted - only some plugins are whitelisted for GitHub Pages. If we choose an unsupported plugin, we'll need to build our site locally rather than making use of the GitHub pipeline to do it for us automatically. That's fine, but detracts from the convenience so let's try to avoid it for now.

Start by adding the plugin to `_config.yml` - add `jemoji` as a new entry in the `plugins` section. My `plugins` section now looks like this:

```
plugins:
  - jekyll-feed
  - jemoji
```

Run `bundle update` to install the new plugin.

That's it! Add some emojis to your posts and test it locally by running `bundle exec jekyll serve` before committing your changes.

:smile: :sunglasses: :star: :+1:

### Links

- [Jekyll plugins docs](https://jekyllrb.com/docs/plugins/)
- [GitHub Pages supported plugins](https://pages.github.com/versions/)
- [Emoji reference](https://gist.github.com/rxaviers/7360908)


