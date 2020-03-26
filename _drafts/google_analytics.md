---
layout: post
title:  "Google Analytics dla Jekyll"
categories: Jekyll
---
Google Analytics setup for Jekyll
Written on April 10, 2016
Google Analytics is the goto web tool to understand web traffic that comes to your site. It provides useful information like, where a user is from, how long they are on your website and what pages they have visited. Google Analytics could be used to make powerful design and business decisions based on what your users are doing.

One of the first things that I do when setting up a new website with Jekyll, is create a new Google Analytics account so that I could start tracking visitors to the website the moment the site is up and running.

If you've got a Google account, getting Google Analytics is super easy. Since the steps in getting a Google Analytics account are better explained in their official website, I won't be covering it here. Instead here is a link to the site.

Once you've created a new Google Analytics account for the site you want to track, you'll want to grab the Google Analytics tracking code. This tracking code is a short piece of JavaScript that you include on all the pages you want to track visitors to your website.

The tracking code could usually be found under Admin > Property > Tracking Info > Tracking Code.

On the Tracking Code page, take note to write down both the tracking number and the tracking code. What I usually do is open up a blank text file and copy and paste both the tracking ID and code in there, to have it handy later.

# Adding Google Analytics to all your pages and posts in Jekyll

Now that you've got your Google Analytics tracking code, it's time to put it in all the pages and posts of your Jekyll project. This may sound daunting since immediately you might think to yourself, I have to copy and paste that tracking code in every single page that I create with Jekyll?

The answer to your question is no! Thanks to the templating system found in Jekyll, we can paste the tracking code once into a file and reference that file to have Jekyll include Google Analytics into every page it generates for us.

To start, create a new file called `analytics.html` in the `_includes` folder found in your Jekyll project.

```
├── _includes
│   ├── analytics.html
```

Paste the Google Analytics tracking code into `analytics.html`. And you should have something like this:

```html
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-XXXXXXXX-X', 'auto');
  ga('send', 'pageview');
</script>
```

Where `UA-XXXXXXXX-X` is your tracking ID.

Now we'll include it in your layout so that it'll be included on all your pages when Jekyll builds your project.

Open up the file `default.html` found in the `_layouts` folder.

Then right above the closing `</body>` tag you'll want to add `{% include analytics.html %}`.

```html
// _layouts/default.html
...
    {% include analytics.html %}
  </body>
</html>
```

Now if you run `jekyll build` from the command-line and open up a page like `index.html` found in the `_site` folder, you'll see that your Google Analytics tracking code is included in the page.

This is great, since you define it once and your tracking code is automatically added to every single page Jekyll generates for you. Even any new post you create will automatically have Google Analytics added to it.

However there is one problem with the way Google Analytics is currently implemented. If you run `jekyll serve` to serve up your website locally on your machine, all your pages will still have Google Analytics added into them and by navigating to those pages, it will actually ping Google Analytics as a site visit.

What this means is, if you visit your Google Analytics account, you'll see a bunch of visits from `localhost:4000` or `127.0.0.1:4000` depending on the type of operating system you're developing your Jekyll project. This can potentially muddy up your analytics, so to mitigate this problem, we'll set Jekyll to only render Google Analytics when its environment is set to `production`.

To do this, you'll want to open up `default.html` again found in the `_layouts` folder. Then you'll want to wrap `{% include analytics.html %}` with `{% if jekyll.environment == 'production' %}{% endif %}` like this:

```html
// _layouts/default.html
...
    {% if jekyll.environment == 'production' %}
    {% include analytics.html %}
    {% endif %}
  </body>
</html>
```

Now when you run `jekyll serve`, your Google Analytics tracking code shouldn't render at all in any pages. The reason for this is, by default Jekyll's environment is set to `development`.

So then, how do you get the analytics to only show up on a production environment? When building your Jekyll project with `jekyll build`, you'll want to prefix it with `JEKYLL_ENV=production` so the complete command looks like this:

```
JEKYLL_ENV=production jekyll build
```

Now when you check your files in the `_site` folder, you'll see that they are being built with the Google Analytics tracking code in them.
