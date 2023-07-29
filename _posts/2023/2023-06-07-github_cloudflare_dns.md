---
title: Configure a GitHub Repository to Use A Cloudflare DNS Custom Subdomain
date: 2023-06-07 01:00:00 -0500
categories: [linux, cloudflare, website]
tags: [cloudflare,website,dns,github]
---


<img src="/assets/img/posts/2023/github_cloudflare_dns/github_cloudflare_dns.jpg" alt="Configure a GitHub Repository to Use A Cloudflare DNS Custom Subdomain" style="height:400px; width:600px;" />


Have you ever wanted to set up a custom subdomain for your GitHub repository? By using Cloudflare DNS, you can easily achieve this. In this guide, we will walk you through the steps to configure your GitHub repository to use a Cloudflare DNS custom subdomain. Let's get started!

## Adding a Subdomain to Cloudflare

1. Login to Cloudflare at [cloudflare.com](https://www.cloudflare.com).
2. In the upper left of your screen, click on your domain name where you want the redirect to take place.
3. Click the DNS tab in the menu on the left.
4. Under the records section, click **Add Record**.
5. Set the **Type** to CNAME.
6. Enter the **Name** of your subdomain (e.g., "blog").
7. Set the **Target** to "githubusername.github.io" (replace "githubusername" with your actual GitHub username).
8. Leave the **TTL** as automatic and enable **Proxy status**.
9. Click the **Save** button.

Congratulations!!! You have now added your subdomain to Cloudflare.

## Setting up GitHub Pages for Your Custom Subdomain

1. Login to GitHub at [github.com](https://github.com).
2. Click on your account/organization and navigate to the repository you want to configure the subdomain for (githubusername.github.io).
3. While inside your repository's code section, click **Settings**.
4. Scroll down to the **Pages** section and select the main branch or the branch you are using for this repository.
5. In the **Custom domain** field, enter your subdomain (e.g., "blog.yourdomain.com").
6. Click the **Save** button.

Great job! You have successfully set up GitHub Pages for your custom subdomain.

## Updating the Repository URL

1. Edit the `_config.yml` file in your repository.
2. Change the URL from `url: 'https://githubusername.github.io'` to `url: 'https://yoursubdomain.yourdomain.com'` (replace "yoursubdomain" and "yourdomain" with your actual subdomain and domain).

And you're done! You have now updated the URL that your repository is pointing to.

**Summary:**

By following these steps, you have configured a custom subdomain for your GitHub repository using Cloudflare DNS. Your subdomain, such as "blog.yourdomain.com," now points to your GitHub Pages site. You can access your site using either the custom subdomain or the original GitHub URL, and both will display identical information.

Now you can personalize your GitHub repository and make it even more accessible to your audience. Enjoy sharing your projects with the world!!

*Note: The instructions in this guide assume you already have a registered domain and have access to manage its DNS settings on Cloudflare.*

