# Create a front end app for a module frtom scratch

Let say you have a module SOCIAL_LOOKUP with some custom entities SOCIAL_ACCOUNT and IMPORT_TEL and you want to generate a basic website with cruds for those entities.

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

Edit the file ListSocialAccount.js and chage Demo (and its variations) to SocialAccount :
```
import { LitElement, html, css } from "lit-element";
import { parseColumns } from "mv-table-utils";
import SocialAccountSchema from "SocialAccountSchema";
import "mv-button";
import "mv-container";
import "mv-font-awesome";
import "mv-pagination";
import "mv-table";
import "mv-tooltip";
import "../../components/layout/PageLayout.js";

const DEFAULT_COLUMNS = Object.keys(SocialAccountSchema.properties);

export default class ListSocialAccount extends LitElement {
  static get properties() {
    return {
      pages: { type: Number },
      currentPage: { type: Number },
      columns: { type: Array },
      items: { type: Array },
    };
  }

  static get styles() {
    return css`
      h1 {
        margin-top: 0;
      }
    `;
  }

  constructor() {
    super();
    this.pages = 1;
    this.currentPage = 1;
    this.items = [];
  }

  render() {
    return html`
      <page-layout>
        <mv-container>
          <h1>Social Accounts</h1>
          <mv-button type="rounded" @button-clicked="${this.newItem}">
            <mv-fa icon="plus"></mv-fa>New
          </mv-button>
          <mv-table
            .columns="${this.columns || []}"
            .rows="${this.items}"
            with-checkbox
            .action-column="${this.actionColumn}"
          ></mv-table>
          <mv-pagination
            type="text"
            .page="${this.currentPage}"
            .pages="${this.pages}"
            @change-page="${this.gotoPage}"
          ></mv-pagination>
        </mv-container>
      </page-layout>
    `;
  }

  connectedCallback() {
    super.connectedCallback();
    this.columns = this.columns || parseColumns(
      SocialAccountSchema.properties,
      DEFAULT_COLUMNS
    );
  }

  gotoPage = (event) => {
    const { detail = {} } = event || {};
    this.currentPage = detail.page || 1;
  };

  newItem = () => {
    history.pushState(null, "", "./SocialAccount/new");
  };
}

customElements.define("list-SocialAccount", ListSocialAccount);
```

Since we modified the class and component name, update AppDashboard by replacing the entity codes and Entrypoint accordingly.

Download the json schema files for each custoim entity from meveo either using the file explorer and going to `/git/Meveo/src/main/java/custom/entities` or by cloning this repo first 
```
git clone http://meveo.admin:meveo@localhost:8080/meveo/git/Meveo meveo-git
```
then taking them (`SOCIAL_ACCOUNT.json` and `TEL_IMPORT.json`) from `src/main/java/custom/entities`

put those two json schema files in /model/ and delte Demo.js and DemoChild.js

update index.htm to import those model instead of Demo and DemoChild

