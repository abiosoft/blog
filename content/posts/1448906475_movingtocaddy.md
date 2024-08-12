+++
comments = true
date = "2015-11-30T19:01:15+01:00"
draft = false
image = ""
tags = ["caddy", "server", "https", "letsencrypt", "git", "webhook"]
title = "Moving to Caddy"
toc =  false
readTime = true
autonumber = false
+++

This static blog has been on [AppEngine](http://cloud.google.com/appengine) for a while and I wrote a blog post about my [migration to Hugo and Appengine](/moving-to-hugo).

Hugo is wonderful and I stick with it but its time to wave AppEngine goodbye. I am not taking advantage of any of the provided services by Google other than the free tier and it is
not that big of deal to fork out few bucks to get more control.

This blog is now powered by [Caddy](http://caddyserver.com) and of course [Hugo](http://gohugo.io).

Let us take a look at how I publish articles before and now; and some other cool things Caddy has to offer. I know I don't have enough posts :P but I hope I can get a renewed spirit.

Just like everyone, my Hugo site has its GitHub repository.

### Before

It takes 3 steps to publish an article.

* Write the blog post and push to GitHub.
* Generate static content with Hugo.
* Publish to AppEngine.

You can argue that I can automate this with a script but I have to worry about those 3 things every time I need to publish.

### Now

It takes just 1 step.

* Write the blog post and push to GitHub.

Yeah, that's all.

### How ?

Well, the answer is Caddy.

Caddy has a [git](http://caddyserver.com/docs/git) add-on that has some nice features including webhooks and running a command after pull.

I configured the webhook endpoint in Caddy, added the webhook to my GitHub repo and I also configured Caddy's git add-on to execute Hugo for static site generation after successful pull.

My `Caddyfile` looks like this.

```caddyfile
yourblogurl.com {
	git github.com/user/app app {
		hook /webhook some-secret-here
		then hugo --destination=/home/user/blog
	}

	root /home/user/blog
}
```

### What else does Caddy offer ?

Free SSL. Yeah, free SSL. This site is on https thanks to [Let's Encrypt](http://letsencrypt.org).

But that's not a Caddy feature ? Well, maybe after I tell you the details of my procedure in setting it up.

All that is required is that `Caddyfile` above. You only need to remove the scheme and port, then use a domain instead of IP address and Caddy takes over the responsibility for you.

Finally, your site is gonna score **A** on [SSL Labs](https://www.ssllabs.com/ssltest/analyze.html?d=abiosoft.com) and you probably know little or nothing about SSL.

### I need this free SSL too
Yeah I know, everyone needs it. I happen to be on the bleeding edge for Let's Encrypt and Caddy. This is currently only available to beta testers.

Let's Encrypt will be out of private beta soon (December 3) and Caddy 0.8 will be out few days after.

Keep an eye on [Caddy Blog](http://caddyserver.com/blog) for 0.8 announcement and get ready to enjoy this.

### Note

* You only need to wait for Caddy 0.8 for free SSL feature. Everything else is available in the current stable release.

### Update. [Dec 04, 2015]

* Caddy 0.8 is out :) Read the [announcement post](https://caddyserver.com/blog/caddy-0_8-released) and start having fun.
