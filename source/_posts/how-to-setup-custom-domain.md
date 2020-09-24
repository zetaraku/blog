---
title: How to Setup Custom Domain for GitHub Pages and Heroku
date: 2020-09-24 16:02:21
categories:
tags: [custom-domain, github-pages, heroku, cloudflare]
---

## Buy a domain name from a domain name registrar

I use **Google Domains** as my domain name registrar:

https://domains.google.com/

## Support SSL/TLS for your website (optional)

Use **CloudFlare** to add ***free*** SSL/TLS support and other protection for your website:

https://www.cloudflare.com/

<!-- more -->

## Setup custom domain for GitHub Pages

Follow the instruction from [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site).

## Setup custom domain for Heroku

Go to the **Domains** section of **Settings** in Heroku dashboard and follow the instruction.

## Redirect page from Heroku (*.herokuapp.com) to custom domain name

According to [Custom Domain Names for Apps](https://devcenter.heroku.com/articles/custom-domains):

{% note info %}
Your app’s Heroku domain always remains active, even if you set up a custom domain.
If you want users to use the custom domain exclusively, your app should send HTTP status 301 Moved Permanently to tell web browsers to use the custom domain.
The Host HTTP request header field will show which domain the user is trying to access; send a redirect if that field is example.herokuapp.com.
{% endnote %}

If you are using `heroku-buildpack-static`, you're in luck!
You can simply set the `canonical_host` in `static.json` to perform a **HTTP 301 Moved Permanently** redirect.

See: https://github.com/heroku/heroku-buildpack-static/#canonical-host

## About custom domain for Heroku when using CloudFlare Full SSL

All Heroku apps already come with a default certificate for **\*.herokuapp.com** which enables HTTPS.

But if you are using `<haiku>.herokudns.com` as the **CloudFlare** DNS target with **Full SSL**, it will result a **525 SSL handshake failed** error because the domain doesn't match.

See: https://help.heroku.com/GVS2BTB5/why-am-i-getting-error-525-ssl-handshake-failed-with-cloudflare-when-using-a-herokudns-com-endpoint

Note that **free** plans of Heroku don't allow you to use custom certificate,
so it's impossible to upload your certificate (acquired from [**Let's Encrypt**](https://letsencrypt.org/) or **Cloudflare**) to Heroku as a free plan user. Please give up.

The solution is to use `<appname>.herokuapp.com` instead of `<haiku>.herokudns.com` as the DNS target.

It is the only solution but discouraged by Heroku now.

See:

* https://stackoverflow.com/questions/58384706/connecting-cloudflare-to-heroku-with-full-ssl-for-free-problem-with-uploading
