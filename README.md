This repository contains a `docker-compose.yml` with a NginX container only,
intended to be run behind another nginx. See `mother-nginx.conf` for an example
configuration that could be included in the outward-facing nginx.
 
Its main goal is to redirect old `http://support.kobotoolbox.org` links to their `http://help.kobotoolbox.org` counterparts.

All redirections rules are configured in `files/redirections.conf`. 

#### Important
All rules must be declared above the last one. The last one is the fallback.  
If no rules match, user is redirected to `http://help.kobotoolbox.org` root.
