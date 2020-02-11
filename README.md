# meveo-frontend.github.io
meveo frontend site


## Meveo components and their demo page
Each component (for instance mv-breadcrumbs) is a github repository of the meveo-org organization with Github pages activated, served from master branch.

So that the demo page can be accessed by its name (typically breadcrumbs.meveo.org) we need to :
- in meveo.org domain DNS settings : add a CNAME record  (with name breadcrumbs) is added to the meveo.org domain.
- in mv-breadcrumbs github repository settings, serve the github page with a custom domain (breadcrumbs.meveo.org)

The demo page is the index.html page found in the root directory of the master branch.

in order to serve over internet the files (js, css,...) stored in the webcomponent repositories, we use jsdelivr.net
so for instance to insert the meveo-theme.css stylesheet wichi is located on the css directory of the master branch of the mv-dependencies repository of the meveo-org organisation we insert:

<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/meveo-org/mv-theme@master/css/meveo-theme.css" /> 

## special repositories
- meveo-fronted.github.io (this) repo is bound to http://front.meveo.org and is aimed to serve the frontend framework documentation
- mv-frontend.github.io repo is bound to http://frontend.meveo.org and is serving the kitchensink demo of all webcomponents
- meveo.github.io repo is bound to http://meveo.org and is currently to serving the backend documentation


