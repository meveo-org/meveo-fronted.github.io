# meveo-frontend.github.io
meveo frontend site


## Meveo components and their demo page
Each component (for instance mv-breadcrumbs) is a github repository with Github pages activated, served from master branch.
So that the demo page can be accessed by its name (typically breadcrumbs.meveo.org) we both:
- in meveo.org domain DNS settings : add a CNAME record  (with name breadcrumbs) is added to the meveo.org domain.
- in mv-breadcrumbs github repository settings, serve the github page with a custom domain (breadcrumbs.meveo.org)

The demo page is the index.html page found in the root directory of the master branch.

