---
layout: post
title: "Why validation should be done with string to string comparison"
date: 2025-07-14 14:00:00 +0000
image: https://oauth.net/images/oauth-logo-square.png
---

I've worked on a few OAuth frameworks and when developing these the bible is the RFC https://datatracker.ietf.org/doc/html/rfc3986. Look at it, it's massive. And there are specs you can bolt on, bits of it say SHOULD instead of MUST implying you can ignore them. This inevitably can cause issues. One aspect it's clear on, but is just lost in the noise, is string comparison.

You want to validate a callback uri or redirect uri? Compare the strings, character for character. But you cannot blame people for being tempted to throw in a bit of flexibility in there. After all the uri you have in config might all be lowercase and the input string can be provided with some upppercase. So maybe you use a URL parser? What can go wrong. 

The lowly carriage return steps in %0A%0D. I'm pleased to say nowadays your browser will actually ignore this in a URL. And even won't follow redirects with URLs containing it. This was not always the case. Likewise URL parsers throw invalid URL errors when passed a domain containing these characters.

It'll just ignore them though when they are in a query parameter though:

```javascript
const url = "https://google.com?test=https://test.co%0A%0Dm/callback";

const test = new URL(url);
const redirect = test.searchParams.get("test");
// no error thrown
// https://test.com/callback
const parsedUrl = new URL(redirect);

// check protocol, domain and path matches whitelist
// ...

return redirect;
```

This was the cause of an open redirect in our auth framework. The attacker could register test.co, and the carriage return would terminate the domain parsing in browser, but sail through our whitelisting because of parsing.

It's nice to see though things have moved on since discovering this and the browser will not tolerate urls containing these characters.