# kobo-support-docker

This repository handles redirection and reverse proxying for our
support-related websites.

* support.kobotoolbox.org:
    1. If the request path matches something in `files/redirections.conf`,
       then the request is redirected;
    1. The request is reverse-proxied to https://kobotoolbox.github.io, which
       is our documentation website.
* help.kobotoolbox.org:
    1. Requests to the base hostname are now redirected to the Discourse forum,
       https://community.kobotoolbox.org;
    1. Requests for anything else are redirected to
       https://support.kobotoolbox.org.
* forum.kobotoolbox.org: this was the very short-lived original hostname for
    our Discourse forum. This redirect could probably be removed, but for
    now, it steers people to https://community.kobotoolbox.org.


This also handles redirection for the "apex" kobotoolbox.org domain and
secondary domain names:

* kobotoolbox.org:
    1. Requests to https://kobotoolbox.org/anything are redirected to
       https://www.kobotoolbox.org/anything;
* kobo.ngo:
    1. Requests to the base hostname and `www` sub-domain are redirected to
       https://www.kobotoolbox.org;
* kobo.ong:
    1. Requests to the base hostname and `www` sub-domain are redirected to
       https://www.kobotoolbox.org;

## How to use

After making any modifications to the redirect rules or other NGINX
configuration settings, build a new Docker image and push it to Docker Hub. Use
the tag `kobotoolbox/kobo-support-docker`:
```
docker build -t kobotoolbox/kobo-support-docker .
```
Once the build completes, push it to Docker Hub:
```
docker push kobotoolbox/kobo-support-docker
```
The new image can now be used with cloud container services such as AWS ECS.
