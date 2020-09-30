# Create a front end app for a module frtom scratch

Let say you have a module SOCIAL_LOOKUP with some custom entities SOCIAL_ACCOUNT and you want to generate a basic website with cruds for those entities.

Make sure you import the last version of [webapprouter module](https://github.com/meveo-org/module-webapprouter/tree/master/meveo%20module)

We call our webapp social-lookup and assume we created an empty git repo, let say https://github.com/meveo-org/social-lookup.git

The first is to clone the meveo webapp template with all its webcomponents as [git submodules](https://www.git-scm.com/book/en/v2/Git-Tools-Submodules)

```
git clone https://github.com/meveo-org/mv-template.git social-lookup
cd social-lookup
git submodule update --init
git remote remove origin
git remote add origin https://github.com/meveo-org/social-lookup.git
git push --set-upstream origin master
```

open your repo in VsCode

in the index.html page, replace the default title by "Social lookup"

in the pages directory duplicate the Demo directory and its files then rename them by replacing "Demo" with "SocialAcout"
then rename Demo dir and its files by replacing "Demo" by "TelImport" 

you should get this :
```
\social-lookup\pages\ImportTel
\social-lookup\pages\ImportTel\ListImportTel.js
\social-lookup\pages\ImportTel\NewImportTel.js
\social-lookup\pages\ImportTel\UpdateImportTel.js
\social-lookup\pages\ImportTel\ViewImportTel.js
\social-lookup\pages\SocialAccount
\social-lookup\pages\SocialAccount\ListSocialAccount.js
\social-lookup\pages\SocialAccount\NewSocialAccount.js
\social-lookup\pages\SocialAccount\UpdateSocialAccount.js
\social-lookup\pages\SocialAccount\ViewSocialAccount.js
\social-lookup\pages\appDashboard.js
```
