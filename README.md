# meveo-frontend.github.io
meveo frontend site


## Meveo components and their demo page
Each component (for instance mv-breadcrumbs) is a github repository of the meveo-org organization with Github pages activated, served from master branch.

So that the demo page can be accessed by its name (typically breadcrumbs.meveo.org) we need to go to the mv-breadcrumbs github repository settings, serve the github page with a custom domain (breadcrumbs.meveo.org). Since the meveo.org domain as a wildcard CNAME record *.meveo.org that point to meveo-org.github.io. the subdomain should work immediatly

The demo page is the index.html page found in the root directory of the master branch.

in order to serve over internet the files (js, css,...) stored in the webcomponent repositories, we use jsdelivr.net
so for instance to insert the meveo-theme.css stylesheet wichi is located on the css directory of the master branch of the mv-dependencies repository of the meveo-org organisation we insert:

    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/meveo-org/mv-theme@master/css/meveo-theme.css" /> 
    
or add the components as submodules to the project, i.e.

    git submodule add https://github.com/meveo-org/mv-dependencies.git src/webapp/web_modules/mv-dependencies

    git submodule add https://github.com/meveo-org/mv-modules.git src/webapp/web_modules/mv-modules

    git submodule add https://github.com/meveo-org/mv-theme.git src/webapp/web_modules/mv-theme

    git submodule add https://github.com/meveo-org/mv-main.git src/webapp/web_modules/mv-main

    git submodule add https://github.com/meveo-org/mv-menu-panel.git src/webapp/web_modules/mv-menu-panel

    git submodule add https://github.com/meveo-org/mv-header.git src/webapp/web_modules/mv-header

    git submodule add https://github.com/meveo-org/mv-footer.git src/webapp/web_modules/mv-footer
    
Note that in this example, the components will be placed in `src/webapp/web_modules`

since the demo pages are not themselves served by meveo (for now...) but by github, we have to manually take care of the browser that dont know what are ES-modules or other related features, so it is recommended to include [es-module-shim](https://github.com/guybedford/es-module-shims) that we forked in [mv-dependencies repo](https://github.com/meveo-org/mv-dependencies/tree/master/es-module-shims) and should be (in the minimified form) included as

    <script defer src="https://cdn.jsdelivr.net/gh/meveo-org/mv-dependencies@master/es-module-shims.min.js"></script>

you can then import your modules using an "importmap-shim" type of script including the meveo component you use and the lit-element dependency (all meveo components are litElement components)

    {
        "imports": {
          "lit-element": "https://cdn.jsdelivr.net/gh/meveo-org/mv-dependencies@master/lit-element.js",
          "mv-button": "https://cdn.jsdelivr.net/gh/meveo-org/mv-button@master/mv-button.js",
          "mv-font-awesome": "https://cdn.jsdelivr.net/gh/meveo-org/mv-font-awesome@master/mv-font-awesome.js"
        }
    }

you can then import your demo component 
    
    <script type="module-shim" src="./demo.js"></script>

and use it in the body.

## special repositories
- meveo-fronted.github.io (this) repo is bound to http://front.meveo.org and is aimed to serve the frontend framework documentation
- mv-frontend.github.io repo is bound to http://frontend.meveo.org and is serving the kitchensink demo of all webcomponents
- meveo.github.io repo is bound to http://meveo.org and is currently to serving the backend documentation


