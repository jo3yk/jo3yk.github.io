---
layout: post
title:  "Setting up Jekyll and GitHub pages"
date:   2020-08-24
categories: jekyll github-pages
---

Welcome to Rubber Duck! My first post is a bit meta - it's about how this blog was set up. I chose to host it on GitHub Pages and therefore use Jekyll to generate the site. Why? Once the setup is complete, I can add a new post via a simple markdown file, and all I need to do is commit it - GitHub will automatically build and redeploy the site. Easy peasy! Plus, it's free :smile:

So, without further ado: how to set up a basic Jekyll-generated blog on GitHub pages.

_Instructions are for Ubuntu, and should work for other Debian-based Linux distros._

### Install pre-reqs

Jekyll is a Ruby tool, so you'll need a Ruby dev environment set up. Plus Git, of course! Install the required packages with the following command:

```
sudo apt install ruby git ruby-full build-essential zlib1g-dev
```

#### Ruby Gems config

By default, Ruby packages ("Gems" in Ruby parlance) are installed under /var/lib/gems, and therefore installation requires root permissions. This isn't ideal, so you can configure Ruby to install under your user directory instead:

```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

(This sets the GEM_HOME environment variable and adds the gems directory to your PATH. These vars are set in your .bashrc file, so that they're applied every time you launch a new shell. Finally, source the .bashrc script to apply the changes to your current shell.)

### Install Jekyll

Now you can use `gem` to install Jekyll:

```
gem install jekyll bundler
```

### Set up site

First, create a new public repo in GitHub, named <your-github-user-id>.github.io.

Create a local git repo and cd into it:

```
git init my-blog
cd my-blog
```

Create a new jekyll site:

```
jekyll new .
```

This is a vanilla Jekyll site. Some small configuration changes are required to make it play nicely with GitHub. Edit the generated Gemfile as follows:

Remove (or comment out with #) the following line:

```
gem "jekyll", "~> 4.1.1"
```

Uncomment the line:

```
gem "github-pages", "~> 207", group: :jekyll_plugins
```

_Note: version 207 is correct at the time of writing, but please check [GitHub pages dependency versions](https://pages.github.com/versions/) for the current version._

Run the following command to apply the changes:

```
bundle update
```

You can now test your site:

```
bundle exec jekyll serve
```

If all is good, you'll be able to view your skeleton site in a browser at http://localhost:4000 

Push it to GitHub as follows (replacing USER and REPOSITORY as appropriate):

```
git remote add origin https://github.com/USER/REPOSITORY.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

That's it! GitHub automatically publishes from the master branch, so your site should now be available at <your-github-user-id>.github.io - hooray!

If you want to publish from a different branch, go into your repository settings and scroll down to the GitHub pages section.

### What's next?

- Update your basic site info by editing `_config.yml`
  - Update the title and description
  - Add your own contact info (email/twitter/github)
- Add your first post
  - An example is auto-generated in the `_posts` directory 
  - Add a new post by creating a file named as follows: `YEAR-MONTH-DAY-title.MARKUP`


### Links

- [GitHub pages docs](https://pages.github.com/)
- [Jekyll docs](https://jekyllrb.com/docs/home)
- [Markdown cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)



