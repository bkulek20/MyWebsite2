---
layout: post
title:  "How to Use Jekyll for GitHub Pages?"
date:   2025-05-07 02:46:48 +0300
categories: jekyll update
---
In this post, I’ll walk you through how I built my own website using `GitHub Pages` and `Jekyll`, and share some key steps and lessons I learned along the way.

Setting Up the Project

I started by creating a public repository on GitHub called `MyWebsite2` and cloned it to my local machine using the following command:

{% highlight ruby %}
git clone <clone_url>
{% endhighlight %}

You can access the GitHub repo here: [MyWebsite2 GitHub][github-website] 

Next, I created a simple `index.html` file to serve as the homepage.

To publish my site via GitHub Pages, I followed these steps:

  1. Navigated to Settings → Pages in my GitHub repository.

  2. Under Build and Deployment, I set the source to Deploy from a branch.

  3. Selected the`main` branch and saved the changes.

Within minutes, my website was live and accessible through the auto-generated URL.
Everything worked smoothly at this stage.

![alt text](image.png)

Installing and Integrating Jekyll

To add a blog section and make use of Markdown files, I decided to install Jekyll.
Jekyll is a static site generator that integrates perfectly with GitHub Pages and makes it easy to build stylish websites without needing to manually handle CSS.

I followed this guide closely during the setup process:
[GitHub Pages + Jekyll Setup Guide][guide-jekyll] 

Here, I'll focus mainly on the challenges I faced.

Step 1: Installing Ruby and Bundler

Since Jekyll requires Ruby and Bundler, I installed them using my terminal.
Helpful resources:

1. [Jekyll MacOS Installation][jekyll-install]  

2. [Bundler][bundler-install]  

Step 2: Creating a New Branch and Starting the Jekyll Project

I created a new branch for Jekyll using:

{% highlight ruby %}
git checkout --orphan gh-pages
{% endhighlight %}

Then I initialized a new Jekyll site:

{% highlight ruby %}
jekyll new --skip-bundle .
{% endhighlight %}

This command automatically generated the `Gemfile` and set up the default minima theme.

Important tip:
Make sure to uncomment this line in the Gemfile:

{% highlight ruby %}
gem "minima", "~> 2.5"
{% endhighlight %}

I missed this initially, which caused my site to appear broken and without styling when published on GitHub Pages.

Additionally, I added the following to the Gemfile to make sure everything works smoothly:

{% highlight ruby %}
gem "github-pages", "~> 232", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.17"
  gem "jekyll-seo-tag"
end
{% endhighlight %}

Step 3: Build and Local Testing
After finalizing the setup, I built the site:

{% highlight ruby %}
bundle exec jekyll build
{% endhighlight %}

Then, I served it locally to test:

{% highlight ruby %}
bundle exec jekyll serve
{% endhighlight %}

The site loaded perfectly in my browser with the correct format and styling.

Troubleshooting Common Issues

After committing and pushing my changes:

{% highlight ruby %}
git add .
git commit -m 'Initial GitHub pages site with Jekyll'
git push origin gh-pages
{% endhighlight %}

I noticed that the live site looked broken again — this is actually a very common issue.
Here’s what I did to fix it:

✅ Remove `_site` from `.gitignore` so GitHub Pages can access those files.
✅ If the site still can’t find the files, make sure the files from `_site` are moved up to the root directory. Sometimes GitHub Pages fails to reach into subdirectories, which causes the site to lose formatting.

Once I handled that, the website loaded correctly. I then personalized my blog to suit my needs.

Conclusion

This process taught me about combining GitHub Pages and Jekyll to create a simple yet functional personal website.
If you're looking to create your own blog or personal site, I highly recommend using these tools :)


[github-website]: https://github.com/bkulek20/MyWebsite2
[guide-jekyll]:  https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll 
[jekyll-install]: https://jekyllrb.com/docs/installation/macos/
[bundler-install]: https://bundler.io/
