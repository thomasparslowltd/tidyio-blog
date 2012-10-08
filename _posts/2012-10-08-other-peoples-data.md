---
layout: post
title: Other People's Data
--- 

When you build software that stores  other people's data you take on a huge responsibility.  Losing someone's data  just isn't an  option and neither is allowing others to gain access to it. This is the situation we're in with tidy.io and of course we're taking it seriously! 

Keeping the customer's data safe and secure requires a whole set of things. A non exhaustive list of a few of them is below.

# HTTPS everywhere 

It goes without saying that all pages shown to logged in users should be served over HTTPS (the secure varient of the HTTP protocol used to serve up web pages, look for the padlock in your address bar.) But that isn't quite enough, it's not much good having all the logged in pages served via HTTPS if you serve the login form over HTTP. A surprising number of sites do this and it makes the whole HTTPS thing a bit pointless, an attacker can simply send a modified version of the login form that forwards the user's details to them. HTTPS is easy to do and servers are plenty fast these days so there's really no excuse not to use it on all your pages, just do it!

# Encrypt all the things

If you store private user data on another service you really need to encrypt it. tidy.io uses Amazon's [Glacier](http://aws.amazon.com/glacier/) and [S3](http://aws.amazon.com/s3/) services. Both of these services encrypt the data stored in them, but that's not enough. So tidy.io also encrypts the data itself before storing it.

# Don't write it yourself 

Every line of code your write is a chance to screw things up, even for the very best coders. So if there's a well tested and reliable library available then use that. This is extra important for encryption stuff, it's so easy to mess this stuff up in non-obvious ways so that it will still seem to work but which gives an attacker an easy way in. So use a well tested library!

# Sanity checks

Sanity checks are your friend. Anywhere you're making an assumption why not add an assertion that confirms it. Assertions are great as a form of documentation as well (as long as they're not the *only* form!). It's (almost) always better to fail early then it is to continue running with potentially invalid data.

# Test test test

Automated tests are vital to reliable software. From unit tests for the individual pieces all the way up to full integration tests, these let you know right away if anything breaks.
  
# Integrate Continuously

Tests on their own are great, but they still leave one vulnerable to the dreaded "works on my machine". It's also easy to forget to run the tests after a change. The fix to both of these issues is automatic CI (Continuous Integration). Every time new code is pushed to the repository the CI server checks it out and runs all the tests in a clean environment. Traditionally CI servers have been a pain in the neck to run (or maybe it's just me?) but thanks to a great new startup called [CircleCI](https://circleci.com/) that isn't such an issue anymore, do check them out!

# Conclusion

No system is perfect but by taking care testing well and not trusting any one part it's possible to make something that is pretty darn reliable and safe.

Thanks for listening!

Oh, and do check out [tidy.io](https://www.tidy.io/) for your DropBox archive and backup needs!