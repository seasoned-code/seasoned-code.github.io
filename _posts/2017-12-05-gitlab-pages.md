---
layout: post
title: GitLab Pages
category: code
excerpt_separator:  <!--more-->
---

### GitHub Pages

Static website engines are bit of a craze for the last few years. Many are aware of GitHub Pages, which supports a number of static website engines. It works really, really well. Particularly if you are looking for a free solution to keep your blog with your code (heck it is managed through Git!). It has <a href="https://github.com/blog/2186-https-for-github-pages" target="_blank">HTTPS</a> for the github.io domain name. It even supports custom domain names. Did I mention it's free?

### What a minute?

Why am I talking about GitHub Pages and not what the title of this post is about? AHH! Right, something that I failed to mention is that GitHub Pages has a great bargain, you get all of the above. However, <a href="https://gist.github.com/cvan/8630f847f579f90e0c014dc5199c337b" target="_blank">unless you proxy your custom domain through something such as "Cloudflare"</a> there will be no support for SSL/TLS, in fact this solution is not even true security!

### GitLab Pages

What if I told you, there is a way to get all of that and a bag of chips!? Yes, with <a href="https://about.gitlab.com/features/pages/" target="_blank">GitLab Pages</a>, you CAN get everything that GitHub Pages offers but also allow you to add a custom domain name with a SSL/TLS Certificate, and if you follow this little <a href="https://about.gitlab.com/2016/04/11/tutorial-securing-your-gitlab-pages-with-tls-and-letsencrypt/" target="_blank">post</a> you can configure it yourself with a free TLS certificate from <a href="https://letsencrypt.org/" target="_blank">Let's Encrypt</a>. You can get all of this through their [Free] Community Edition account. Also, another boon over GitHub's offerings is that you can also maintain a private repo for your website.

If you did not want to create a new account for signing in, they even support using third party authentication which includes using GitHub as a provider!

### Closing

I searched, and waited, to see if GitHub would support what I was looking for and it just did not turn up. I would like to thank GitLab for their services. I will likely be adding my future projects to GitLab as well.