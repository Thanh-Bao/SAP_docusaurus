```
git clone https://github.com/SAP/openui5-sample-app demo
```

# OR Use UI5 Tooling

- https://sap.github.io/ui5-tooling/v3/pages/GettingStarted

- https://www.youtube.com/watch?v=YZDeq4HHF_s&ab_channel=CodeWithBrandon

use **git bash**:

```
mkdir demo ; /
cd demo ; /
mkdir webapp ; /
touch manifest.json ; /
touch index.html ; /
touch index.js ; /
```

```
npm install --global @ui5/cli
```

```
npm init --yes
```

```
ui5 init
```

```
vi manifest.json
```

paste https://help.sap.com/saphelp_snc700_ehp04/helpdata/de/3a/9babace121497abea8f0ea66e156d9/content.htm?no_cache=true

or https://github.com/SAP/ui5-tooling/issues/530#issuecomment-872862794

```json title="/webapp/manifest.json"
{
  "_version": "1.1.0",
  "start_url": "<startUrl>",
  "sap.app": {
    "_version": "1.1.0",
    "id": "<id>",
    "type": "application",
    "i18n": "<i18nPathRelativeToManifest>",
    "applicationVersion": {
      "version": "<version>"
    },
    "title": "{{<title>}}",
    "tags": {
      "keywords": ["{{<keyword1>}}", "{{<keyword2>}}"]
    },
    "dataSources": {
      "<dataSourceAlias>": {
        "uri": "<uri>",
        "settings": {
          "localUri": "<localUri>"
        }
      }
    }
  },
  "sap.ui": {
    "_version": "1.1.0",
    "icons": {
      "icon": "<icon>",
      "favIcon": "<favIcon>",
      "phone": "<phone>",
      "phone@2": "<phone@2>",
      "tablet": "<tablet>",
      "tablet@2": "<tablet@2>"
    },
    "deviceTypes": {
      "desktop": true,
      "tablet": true,
      "phone": true
    },
    "supportedThemes": ["sap_hcb", "sap_bluecrystal"]
  },
  "sap.ui5": {
    "_version": "1.1.0",
    "resources": {
      "js": [
        {
          "uri": "<uri>"
        }
      ],
      "css": [
        {
          "uri": "<uri>",
          "id": "<id>"
        }
      ]
    },
    "dependencies": {
      "minUI5Version": "<minUI5Version>",
      "libs": {
        "<ui5lib1>": {
          "minVersion": "<minVersion1>"
        },
        "<ui5lib2>": {
          "minVersion": "<minVersion2>"
        }
      },
      "components": {
        "<ui5component1>": {
          "minVersion": "<minComp1Version>"
        }
      }
    },
    "models": {
      "i18n": {
        "type": "sap.ui.model.resource.ResourceModel",
        "uri": "<uriRelativeToManifest>"
      },
      "": {
        "dataSource": "<dataSourceAlias>",
        "settings": {}
      }
    },
    "rootView": "<rootView>",
    "handleValidation": false,
    "config": {},
    "routing": {},
    "extends": {
      "component": "<extendedComponentId>",
      "minVersion": "<minComp1Version>",
      "extensions": {}
    },
    "contentDensities": {
      "compact": false,
      "cozy": false
    }
  },
  "sap.platform.abap": {
    "_version": "1.1.0",
    "uri": "<uri>"
  },
  "sap.platform.hcp": {
    "_version": "1.1.0",
    "uri": "<uri>"
  }
}
```

```
ui5 use openui5@latest
```

```
ui5 add sap.ui.core sap.m sap.ui.table themelib_sap_fiori_3
```

```html title="/webapp/index.html"
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Quickstart Tutorial</title>
    <script
      id="sap-ui-bootstrap"
      src="https://sdk.openui5.org/resources/sap-ui-core.js"
      data-sap-ui-theme="sap_belize"
      data-sap-ui-libs="sap.m"
      data-sap-ui-resourceroots='{"Quickstart": "./"}'
      data-sap-ui-onInit="module:Quickstart/index"
      data-sap-ui-compatVersion="edge"
      data-sap-ui-async="true"
    ></script>
  </head>

  <body class="sapUiBody" id="content"></body>
</html>
```

```javascript title="/webapp/index.js"
// sap.ui.getCore().

sap.ui.define(
  ["sap/m/Button", "sap/m/MessageToast"],
  function (Button, MessageToast) {
    "use strict";

    new Button({
      text: "Ready...",
      press: function () {
        MessageToast.show("Hello World!");
      },
    }).placeAt("content");
  }
);
```

```
ui5 serve
```

```
yarn add -D @openui5/ts-types-esm
yarn add -D @sapui5/ts-types-esm
```

https://sap.github.io/ui5-typescript/

#### To install hot reload

https://www.npmjs.com/package/ui5-middleware-livereload
https://github.com/Thanh-Bao/Fiori_hello_world/tree/5d99e4ec9c2faf3d84e94f382720f1040046daf2

```json title=./package.json
{
  "name": "baobaostore.com",
  "version": "0.3.0",
  "description": "baobaostore.com build with OpenUI5",
  "private": true,
  "engines": {
    "node": "^16.18.0 || >=18.12.0",
    "npm": ">= 8"
  },
  "scripts": {
    "start": "ui5 serve",
    "lint": "eslint webapp",
    "build": "ui5 build -a --clean-dest",
    "build-self-contained": "ui5 build self-contained -a --clean-dest",
    "serve-dist": "ws --compress -d dist"
  },
  "devDependencies": {
    "@openui5/ts-types-esm": "^1.112.0",
    "@sapui5/ts-types-esm": "^1.108.12",
    "@ui5/cli": "^3.0.6",
    "eslint": "^8.37.0",
    "local-web-server": "^5.3.0",
    "rimraf": "^4.4.1",
    "ui5-middleware-livereload": "^0.8.2",
    "ui5-middleware-simpleproxy": "^0.9.5"
  },
  "ui5": {
    "dependencies": ["ui5-middleware-livereload"]
  }
}
```

```yaml title=./ui5.yaml
specVersion: "2.0"
metadata:
  name: openui5-sample-app
type: application
framework:
  name: OpenUI5
  version: "1.112.0"
  libraries:
    - name: sap.f
    - name: sap.m
    - name: sap.ui.core
    - name: themelib_sap_fiori_3
server:
  customMiddleware:
    - name: ui5-middleware-livereload
      afterMiddleware: compression
      configuration:
        debug: true
        ext: "xml,json,properties"
        port: 35729
        path: "webapp"
```

# Tutorial

https://saplearners.com/getting-started-with-ui5-tooling/
