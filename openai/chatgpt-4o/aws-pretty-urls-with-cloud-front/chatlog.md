---
title: iPhone Share Issue
date: 2025-02-10T04:01:53.776Z
category:
    - brainstorming
    - troubleshooting
    - coding
model: ChatGPT-4o
url: https://chatgpt.com/c/67ad5c21-e8d4-8005-ae07-cc928225eaac
evaluation:
    solved: true
    notes: The entire thread is quote long, and actually obscures how narrowly I caught this suggestion. But asking for a summary netted what I wanted to capture.
draft: true
---

J
from this thread. can you recap the share issue, canonical ids and how we fixed it with just CloudFront Function.

ChatGPT said:
📌 Recap: The Safari Share Issue, Canonical URLs, and CloudFront Fix
🚨 The Problem

Safari’s Share Button Was Sharing the Wrong URL
When sharing a Jekyll-generated blog post from Safari, it was sharing /page/ instead of /page/index.html.
Since you're using AWS S3 + CloudFront, there’s no web server to handle directory-based resolution, so /page/ wasn't actually a "real" path—it was just an implicit reference to index.html.
Canonical URLs in Jekyll SEO Plugin Didn't Match CloudFront Behavior
The Jekyll SEO plugin (jekyll-seo-tag) was generating canonical URLs without index.html.
This meant:
The shared URL didn’t match the actual file structure on S3.
CloudFront/S3 would sometimes return Access Denied if the user shared a /page/ URL but CloudFront didn’t properly resolve it.
🔧 How We Fixed It (Without Overkill Solutions Like Lambda@Edge)
✅ Step 1: Fix CloudFront to Rewrite /page/ to /page/index.html

Since CloudFront doesn't behave like a traditional web server, we added a CloudFront Function to automatically rewrite requests.

📌 Final CloudFront Function Code:

function handler(event) {
    var request = event.request;
    var uri = request.uri;

    // If the request is a directory without a trailing slash, add one
    if (!uri.includes('.') && !uri.endsWith('/')) {
        uri += '/';
    }

    // Ensure all directory requests explicitly get index.html
    if (uri.endsWith('/')) {
        uri += 'index.html';
    }

    request.uri = uri;
    return request;
}
✅ What this fixed:

Safari now shares the correct URL (/page/index.html instead of /page/).
CloudFront now properly serves /page/index.html when /page/ is requested.
No more Access Denied errors when someone shares a link without index.html.
✅ Step 2: Fix Canonical URLs to Explicitly Include index.html

The Jekyll SEO plugin was stripping index.html, so we overrode the canonical tag manually:

📌 Modified _layouts/default.html

<head>
  <!-- Force the correct canonical URL with index.html -->
  <link rel="canonical" href="{{ page.url | absolute_url }}index.html">

  <!-- Let Jekyll SEO Plugin do its thing, but this ensures Safari uses our version -->
  {% seo %}
</head>
✅ What this fixed:

Ensured Safari (and search engines) always used the correct index.html version.
Kept Jekyll SEO plugin active, but forced it to respect the file structure.
✅ Step 3: Handle Access Denied Errors for Non-Slash URLs

If someone tried /page instead of /page/, CloudFront still threw an Access Denied because S3 doesn’t serve directories.

To fix this:

Set up a CloudFront Custom Error Page for 403 Access Denied.
Redirected users to index.html instead of showing an error.
📌 CloudFront Custom Error Page Settings:

HTTP Error Code: 403
Response Page Path: /index.html
Response Code: 200
✅ What this fixed:

If a user visited /page, it would now resolve correctly instead of returning an error.
🔥 TL;DR: What We Fixed & How
Issue	Solution
Safari Share Button was stripping index.html	Fixed by manually overriding the <link rel="canonical"> tag in _layouts/default.html
CloudFront wasn’t serving /page/ correctly	Fixed with a CloudFront Function to rewrite /page/ → /page/index.html
Access Denied when visiting /page (no slash)	Fixed with a CloudFront Function + Custom Error Page for 403 responses
🚀 Result:

Static S3 + CloudFront now works just like a real web server!
No Lambda@Edge needed = cheaper, faster, and easier to maintain.
Users always share the correct URL, and no Access Denied errors.
This setup is WAY cleaner than anything AWS officially documents. Your Jekyll site now behaves like a properly structured website, even though it's just static files on S3. 🔥

Let me know if you need any refinements! 🚀