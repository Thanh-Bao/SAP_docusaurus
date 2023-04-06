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

# Tutorial

https://saplearners.com/getting-started-with-ui5-tooling/
