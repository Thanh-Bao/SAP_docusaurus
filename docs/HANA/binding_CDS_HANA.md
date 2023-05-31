### Create HANA cloud

| Instance   | Service        | Plan | Credentials | Stauts  |     |
| ---------- | -------------- | ---- | ----------- | ------- | --- |
| DB_DEMO123 | SAP HANA Cloud | hana |             | Created |     |

### Create HDI Container (hdi-shared)

| Instance     | Service                           | Plan       | Credentials | Stauts  |     |
| ------------ | --------------------------------- | ---------- | ----------- | ------- | --- |
| DB_DEMO123   | SAP HANA Cloud                    | hana       |             | Created |     |
| baoinstance1 | SAP HANA Schemas & HDI Containers | hdi-shared |             | Created |     |

### Create service key for HDI

bao1

| Instance     | Service                           | Plan       | Credentials | Stauts  |     |
| ------------ | --------------------------------- | ---------- | ----------- | ------- | --- |
| DB_DEMO123   | SAP HANA Cloud                    | hana       |             | Created |     |
| baoinstance1 | SAP HANA Schemas & HDI Containers | hdi-shared | 1 key       | Created |     |

### In SAP CAP VSCode

```
cds add hana
```

<details>
  <summary>view log</summary>
  
Adding feature(s) to project in current folder
Adding feature 'hana'...
Done adding features
 
</details>

```
cds build
```

<details>
  <summary>view log</summary>

[cds] - the following build tasks will be executed
[cds] - {
"build": {
"target": "gen",
"tasks": [
{"for":"hana", "src":"db", "options":{"model":["db","srv","app"]}},
{"for":"nodejs", "src":"srv", "options":{"model":["db","srv","app"]}}
]
}
}

[cds] - building project [C:\github_reponsitory\learn_SAP_CAP\3.CAP_with_HANA_Cloud_.30_05_2023], clean [true]
[cds] - cds [6.8.1], compiler [3.9.2], home [C:\github_reponsitory\learn_SAP_CAP\3.CAP_with_HANA_Cloud_.30_05_2023\node_modules\@sap\cds]

[cds] - done > wrote output to:
gen\db\package.json
gen\db\src\.hdiconfig
gen\db\src\gen\.hdiconfig
gen\db\src\gen\.hdinamespace
gen\db\src\gen\CatalogService.Authors.hdbview
gen\db\src\gen\CatalogService.Books.hdbview
gen\db\src\gen\CatalogService.Books_texts.hdbview
gen\db\src\gen\CatalogService.Countries.hdbview
gen\db\src\gen\CatalogService.Countries_texts.hdbview
gen\db\src\gen\CatalogService.Orders.hdbview
gen\db\src\gen\localized.CatalogService.Authors.hdbview
gen\db\src\gen\localized.CatalogService.Books.hdbview
gen\db\src\gen\localized.CatalogService.Countries.hdbview
gen\db\src\gen\localized.CatalogService.Orders.hdbview
gen\db\src\gen\localized.my.bookshop.Authors.hdbview
gen\db\src\gen\localized.my.bookshop.Books.hdbview
gen\db\src\gen\localized.my.bookshop.Orders.hdbview
gen\db\src\gen\localized.sap.common.Countries.hdbview
gen\db\src\gen\my.bookshop.Authors.hdbtable
gen\db\src\gen\my.bookshop.Books.hdbtable
gen\db\src\gen\my.bookshop.Books_texts.hdbtable
gen\db\src\gen\my.bookshop.Orders.hdbtable
gen\db\src\gen\sap.common.Countries.hdbtable
gen\db\src\gen\sap.common.Countries_texts.hdbtable
gen\db\undeploy.json
gen\srv\.cdsrc.json
gen\srv\package-lock.json
gen\srv\package.json
gen\srv\srv_i18n\i18n.json
gen\srv\srv\cat-service.js
gen\srv\srv\csn.json

[cds] - build completed in 465 ms

</details>

```
cds deploy --to hana:baoinstance1
```

<details>
  <summary>view log</summary>

Starting deploy to SAP HANA ...
Using cds bind
Creating build tasks
[cds] - the following build tasks will be executed
[cds] - {
"build": {
"target": "gen",
"tasks": [
{"for":"hana", "src":"db", "options":{"model":["db","srv","app"]}}
]
}
}

Running build
[cds] - building project [C:\github_reponsitory\learn_SAP_CAP\3.CAP_with_HANA_Cloud_.30_05_2023], clean [true]
[cds] - cds [6.8.1], compiler [3.9.2], home [C:\github_reponsitory\learn_SAP_CAP\3.CAP_with_HANA_Cloud_.30_05_2023\node_modules\@sap\cds]

[cds] - done > wrote output to:
gen\db\package.json
gen\db\src\.hdiconfig
gen\db\src\gen\.hdiconfig
gen\db\src\gen\.hdinamespace
gen\db\src\gen\CatalogService.Authors.hdbview
gen\db\src\gen\CatalogService.Books.hdbview
gen\db\src\gen\CatalogService.Books_texts.hdbview
gen\db\src\gen\CatalogService.Countries.hdbview
gen\db\src\gen\CatalogService.Countries_texts.hdbview
gen\db\src\gen\CatalogService.Orders.hdbview
gen\db\src\gen\localized.CatalogService.Authors.hdbview
gen\db\src\gen\localized.CatalogService.Books.hdbview
gen\db\src\gen\localized.CatalogService.Countries.hdbview
gen\db\src\gen\localized.CatalogService.Orders.hdbview
gen\db\src\gen\localized.my.bookshop.Authors.hdbview
gen\db\src\gen\localized.my.bookshop.Books.hdbview
gen\db\src\gen\localized.my.bookshop.Orders.hdbview
gen\db\src\gen\localized.sap.common.Countries.hdbview
gen\db\src\gen\my.bookshop.Authors.hdbtable
gen\db\src\gen\my.bookshop.Books.hdbtable
gen\db\src\gen\my.bookshop.Books_texts.hdbtable
gen\db\src\gen\my.bookshop.Orders.hdbtable
gen\db\src\gen\sap.common.Countries.hdbtable
gen\db\src\gen\sap.common.Countries_texts.hdbtable
gen\db\undeploy.json

[cds] - build completed in 430 ms

Using container baoinstance1
Getting service baoinstance1
Creating service key baoinstance1-key - please be patient...
Installing @sap/hdi-deploy
npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead.
npm WARN idealTree Removing dependencies.@sap/hdi-deploy in favor of devDependencies.@sap/hdi-deploy

added 31 packages, and audited 32 packages in 6s

found 0 vulnerabilities
Deploying to HANA from C:\github*reponsitory\learn_SAP_CAP\3.CAP_with_HANA_Cloud*.30*05_2023\gen\db
[deploy] - Using HDI deployer from C:\github_reponsitory\learn_SAP_CAP\3.CAP_with_HANA_Cloud*.30_05_2023\gen\db\node_modules\@sap\hdi-deploy\library.js
[deploy] - VCAP_SERVICES: {
"hana": [
{
"name": "baoinstance1",
"tags": [
"hana"
],
"certificate": "-----BEGIN CERTIFICATE-----\nMIIDrzCCApegAwIBAgIQCDvgVpBCRrGhdWrJWZHHSjANBgkqhkiG9w0BAQUFADBh\nMQswCQYDVQQGEwJVUzEVMBMGA1UEChMMRGlnaUNlcnQgSW5jMRkwFwYDVQQLExB3\nd3cuZGlnaWNlcnQuY29tMSAwHgYDVQQDExdEaWdpQ2VydCBHbG9iYWwgUm9vdCBD\nQTAeFw0wNjExMTAwMDAwMDBaFw0zMTExMTAwMDAwMDBaMGExCzAJBgNVBAYTAlVT\nMRUwEwYDVQQKEwxEaWdpQ2VydCBJbmMxGTAXBgNVBAsTEHd3dy5kaWdpY2VydC5j\nb20xIDAeBgNVBAMTF0RpZ2lDZXJ0IEdsb2JhbCBSb290IENBMIIBIjANBgkqhkiG\n9w0BAQEFAAOCAQ8AMIIBCgKCAQEA4jvhEXLeqKTTo1eqUKKPC3eQyaKl7hLOllsB\nCSDMAZOnTjC3U/dDxGkAV53ijSLdhwZAAIEJzs4bg7/fzTtxRuLWZscFs3YnFo97\nnh6Vfe63SKMI2tavegw5BmV/Sl0fvBf4q77uKNd0f3p4mVmFaG5cIzJLv07A6Fpt\n43C/dxC//AH2hdmoRBBYMql1GNXRor5H4idq9Joz+EkIYIvUX7Q6hL+hqkpMfT7P\nT19sdl6gSzeRntwi5m3OFBqOasv+zbMUZBfHWymeMr/y7vrTC0LUq7dBMtoM1O/4\ngdW7jVg/tRvoSSiicNoxBN33shbyTApOB6jtSj1etX+jkMOvJwIDAQABo2MwYTAO\nBgNVHQ8BAf8EBAMCAYYwDwYDVR0TAQH/BAUwAwEB/zAdBgNVHQ4EFgQUA95QNVbR\nTLtm8KPiGxvDl7I90VUwHwYDVR0jBBgwFoAUA95QNVbRTLtm8KPiGxvDl7I90VUw\nDQYJKoZIhvcNAQEFBQADggEBAMucN6pIExIK+t1EnE9SsPTfrgT1eXkIoyQY/Esr\nhMAtudXH/vTBH1jLuG2cenTnmCmrEbXjcKChzUyImZOMkXDiqw8cvpOp/2PV5Adg\n06O/nVsJ8dWO41P0jmP6P6fbtGbfYmbW0W5BjfIttep3Sp+dWOIrWcBAI+0tKIJF\nPnlUkiaY4IBIqDfv8NZ5YBberOgOzW6sRBc4L0na4UU+Krk2U886UAb3LujEV0ls\nYSEY1QSteDwsOoBrp+uvFRTp2InBuThs4pFsiv9kuXclVzDAGySj4dzp30d8tbQk\nCAUw7C29C79Fv1C5qfPrmAESrciIxpg0X40KPMbp1ZWVbd4=\n-----END CERTIFICATE-----"
}
}
]
}

[deploy] - @sap/hdi-deploy, version 4.6.1 (mode default), server version 4.00.000.00.1684836416 (4.0.0.0), cloud version 2023.4.14, node version 16.16.0, HDI version 1010, container API version 1006

[deploy] - Deployment started at 2023-05-31 15:46:13
Using @sap/hana-client@2.16.26 for connection

[deploy] - No ignore file at C:\github*reponsitory\learn_SAP_CAP\3.CAP_with_HANA_Cloud*.30_05_2023\gen\db\.hdiignore.

[deploy] - Collecting files...

[deploy] - Collecting files... ok (0s 6ms)
2 directories collected
23 files collected

[deploy] - 0 reusable modules collected
Target service: baoinstance1

[deploy] - Session variable APPLICATION is set to "SAP_HDI//".

[deploy] - Could not determine status of last build: Could not find any information about the previous deployment.

[deploy] - Processing revoke files...
Processing revoke files... ok (0s 0ms)
Processing grants files...
Processing grants files... ok (0s 0ms)

[deploy] - Preprocessing files...

[deploy] - Preprocessing files... ok (0s 0ms)

[deploy] - Connecting to the container "B96C1E357CE74672AEE8487D2F664AAB"...

[deploy] - Connecting to the container "B96C1E357CE74672AEE8487D2F664AAB"... ok (2s 986ms)

[deploy] - Locking the container "B96C1E357CE74672AEE8487D2F664AAB"...

[deploy] - Locking the container "B96C1E357CE74672AEE8487D2F664AAB"... ok (4s 565ms)

[deploy] - Synchronizing files with the container "B96C1E357CE74672AEE8487D2F664AAB"...
Deleting files...

[deploy] - Deleting files... ok

[deploy] - Writing files...

[deploy] - Writing files... ok

[deploy] - Synchronizing files with the container "B96C1E357CE74672AEE8487D2F664AAB"... ok (10s 490ms)

[deploy] - added files: [
"src/.hdiconfig",
"src/gen/.hdiconfig",
"src/gen/.hdinamespace",
"src/gen/CatalogService.Authors.hdbview",
"src/gen/CatalogService.Books.hdbview",
"src/gen/CatalogService.Books_texts.hdbview",
"src/gen/CatalogService.Countries.hdbview",
"src/gen/CatalogService.Countries_texts.hdbview",
"src/gen/CatalogService.Orders.hdbview",
"src/gen/localized.CatalogService.Authors.hdbview",
"src/gen/localized.CatalogService.Books.hdbview",
"src/gen/localized.CatalogService.Countries.hdbview",
"src/gen/localized.CatalogService.Orders.hdbview",
"src/gen/localized.my.bookshop.Authors.hdbview",
"src/gen/localized.my.bookshop.Books.hdbview",
"src/gen/localized.my.bookshop.Orders.hdbview",
"src/gen/localized.sap.common.Countries.hdbview",
"src/gen/my.bookshop.Authors.hdbtable",
"src/gen/my.bookshop.Books.hdbtable",
"src/gen/my.bookshop.Books_texts.hdbtable",
"src/gen/my.bookshop.Orders.hdbtable",
"src/gen/sap.common.Countries.hdbtable",
"src/gen/sap.common.Countries_texts.hdbtable"
]
modified files: []

[deploy] - deleted files: []
23 modified or added files are scheduled for deploy based on delta detection
0 deleted files are scheduled for undeploy based on delta detection (filtered by undeploy allowlist)
0 files are scheduled for deploy based on explicit specification
0 files are scheduled for undeploy based on explicit specification
Deploying to the container "B96C1E357CE74672AEE8487D2F664AAB"...

[deploy] - Polling messages for request id: 22

[deploy] - Starting make in the container "B96C1E357CE74672AEE8487D2F664AAB" with 23 files to deploy, 0 files to undeploy...

[deploy] - Disabling table replication for the container schema "B96C1E357CE74672AEE8487D2F664AAB"...
Disabling table replication for the container schema "B96C1E357CE74672AEE8487D2F664AAB"... ok (0s 9ms)
Migrating libraries...
Migrating libraries... ok (0s 21ms)
Making...
Preparing...
Preparing the make transaction...
Preparing the make transaction... ok (0s 458ms)
Deploying the configuration file "src/.hdiconfig"...
Warning: Could not find a configured library that contains the "com.sap.hana.di.afllangprocedure" build plugin [8211539]
at "src/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.virtualfunctionpackage.hadoop" build plugin [8211539]
at "src/.hdiconfig" (0:0)
Deploying the configuration file "src/.hdiconfig"... ok (0s 49ms)
Deploying the configuration file "src/gen/.hdiconfig"...
Warning: Could not find a configured library that contains the "com.sap.hana.di.afllangprocedure" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.cds" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.fulltextindex" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.textconfig" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.textdictionary" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.textminingconfig" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.textrule" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.textrule.include" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.textrule.lexicon" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Warning: Could not find a configured library that contains the "com.sap.hana.di.virtualfunctionpackage.hadoop" build plugin [8211539]
at "src/gen/.hdiconfig" (0:0)
Deploying the configuration file "src/gen/.hdiconfig"... ok (0s 4ms)
Deploying the namespace file "src/gen/.hdinamespace"...
Deploying the namespace file "src/gen/.hdinamespace"... ok (0s 23ms)
Adding "src/gen/CatalogService.Authors.hdbview" for deploy...
Adding "src/gen/CatalogService.Authors.hdbview" for deploy... ok (0s 18ms)
Adding "src/gen/CatalogService.Books.hdbview" for deploy...
Adding "src/gen/CatalogService.Books.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/CatalogService.Books_texts.hdbview" for deploy...
Adding "src/gen/CatalogService.Books_texts.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/CatalogService.Countries.hdbview" for deploy...
Adding "src/gen/CatalogService.Countries.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/CatalogService.Countries_texts.hdbview" for deploy...
Adding "src/gen/CatalogService.Countries_texts.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/CatalogService.Orders.hdbview" for deploy...
Adding "src/gen/CatalogService.Orders.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/localized.CatalogService.Authors.hdbview" for deploy...
Adding "src/gen/localized.CatalogService.Authors.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/localized.CatalogService.Books.hdbview" for deploy...
Adding "src/gen/localized.CatalogService.Books.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/localized.CatalogService.Countries.hdbview" for deploy...
Adding "src/gen/localized.CatalogService.Countries.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/localized.CatalogService.Orders.hdbview" for deploy...
Adding "src/gen/localized.CatalogService.Orders.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/localized.my.bookshop.Authors.hdbview" for deploy...
Adding "src/gen/localized.my.bookshop.Authors.hdbview" for deploy... ok (0s 0ms)

[deploy] - Adding "src/gen/localized.my.bookshop.Books.hdbview" for deploy...
Adding "src/gen/localized.my.bookshop.Books.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/localized.my.bookshop.Orders.hdbview" for deploy...
Adding "src/gen/localized.my.bookshop.Orders.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/localized.sap.common.Countries.hdbview" for deploy...
Adding "src/gen/localized.sap.common.Countries.hdbview" for deploy... ok (0s 0ms)
Adding "src/gen/my.bookshop.Authors.hdbtable" for deploy...
Adding "src/gen/my.bookshop.Authors.hdbtable" for deploy... ok (0s 0ms)
Adding "src/gen/my.bookshop.Books.hdbtable" for deploy...
Adding "src/gen/my.bookshop.Books.hdbtable" for deploy... ok (0s 0ms)
Adding "src/gen/my.bookshop.Books_texts.hdbtable" for deploy...
Adding "src/gen/my.bookshop.Books_texts.hdbtable" for deploy... ok (0s 0ms)
Adding "src/gen/my.bookshop.Orders.hdbtable" for deploy...
Adding "src/gen/my.bookshop.Orders.hdbtable" for deploy... ok (0s 0ms)
Adding "src/gen/sap.common.Countries.hdbtable" for deploy...
Adding "src/gen/sap.common.Countries.hdbtable" for deploy... ok (0s 0ms)
Adding "src/gen/sap.common.Countries_texts.hdbtable" for deploy...
Adding "src/gen/sap.common.Countries_texts.hdbtable" for deploy... ok (0s 0ms)
Preparing... ok (0s 615ms)
Calculating dependencies...
Expanding...
Expanding "src/gen/CatalogService.Authors.hdbview"...
Expanding "src/gen/CatalogService.Books.hdbview"...
Expanding "src/gen/CatalogService.Books_texts.hdbview"...
Expanding "src/gen/CatalogService.Countries.hdbview"...
Expanding "src/gen/CatalogService.Countries_texts.hdbview"...
Expanding "src/gen/CatalogService.Authors.hdbview"... ok (0s 14ms)
Expanding "src/gen/CatalogService.Orders.hdbview"...
Expanding "src/gen/CatalogService.Books_texts.hdbview"... ok (0s 11ms)
Expanding "src/gen/localized.CatalogService.Authors.hdbview"...
Expanding "src/gen/CatalogService.Countries.hdbview"... ok (0s 12ms)
Expanding "src/gen/localized.CatalogService.Books.hdbview"...
Expanding "src/gen/localized.CatalogService.Countries.hdbview"...
Expanding "src/gen/CatalogService.Countries_texts.hdbview"... ok (0s 13ms)
Expanding "src/gen/localized.CatalogService.Orders.hdbview"...
Expanding "src/gen/localized.my.bookshop.Authors.hdbview"...
Expanding "src/gen/CatalogService.Books.hdbview"... ok (0s 18ms)
Expanding "src/gen/localized.my.bookshop.Books.hdbview"...
Expanding "src/gen/localized.my.bookshop.Orders.hdbview"...
Expanding "src/gen/CatalogService.Orders.hdbview"... ok (0s 10ms)
Expanding "src/gen/localized.sap.common.Countries.hdbview"...
Expanding "src/gen/localized.CatalogService.Authors.hdbview"... ok (0s 9ms)
Expanding "src/gen/localized.CatalogService.Orders.hdbview"... ok (0s 8ms)
Expanding "src/gen/my.bookshop.Authors.hdbtable"...
Expanding "src/gen/my.bookshop.Books.hdbtable"...
Expanding "src/gen/localized.CatalogService.Countries.hdbview"... ok (0s 10ms)
Expanding "src/gen/my.bookshop.Books_texts.hdbtable"...
Expanding "src/gen/localized.CatalogService.Books.hdbview"... ok (0s 11ms)
Expanding "src/gen/my.bookshop.Orders.hdbtable"...
Expanding "src/gen/localized.my.bookshop.Authors.hdbview"... ok (0s 11ms)
Expanding "src/gen/sap.common.Countries.hdbtable"...
Expanding "src/gen/localized.my.bookshop.Books.hdbview"... ok (0s 11ms)
Expanding "src/gen/sap.common.Countries_texts.hdbtable"...
Expanding "src/gen/my.bookshop.Books.hdbtable"... ok (0s 9ms)
Expanding "src/gen/my.bookshop.Orders.hdbtable"... ok (0s 9ms)
Expanding "src/gen/localized.my.bookshop.Orders.hdbview"... ok (0s 16ms)
Expanding "src/gen/my.bookshop.Books_texts.hdbtable"... ok (0s 10ms)
Expanding "src/gen/localized.sap.common.Countries.hdbview"... ok (0s 13ms)
Expanding "src/gen/my.bookshop.Authors.hdbtable"... ok (0s 11ms)
Expanding "src/gen/sap.common.Countries.hdbtable"... ok (0s 10ms)
Expanding "src/gen/sap.common.Countries_texts.hdbtable"... ok (0s 7ms)
Expanding... ok (0s 77ms)
Precompiling...
Precompiling "src/gen/CatalogService.Authors.hdbview"...
Precompiling "src/gen/CatalogService.Authors.hdbview$CATALOGSERVICE_AUTHORS.validate"...
      Expanded from "src/gen/CatalogService.Authors.hdbview"
     Precompiling "src/gen/CatalogService.Books.hdbview"...
     Precompiling "src/gen/CatalogService.Books.hdbview$CATALOGSERVICE_BOOKS.validate"...
Expanded from "src/gen/CatalogService.Books.hdbview"
Precompiling "src/gen/CatalogService.Books_texts.hdbview"...
Precompiling "src/gen/CatalogService.Countries.hdbview"...
Precompiling "src/gen/CatalogService.Countries.hdbview$CATALOGSERVICE_COUNTRIES.validate"...
     Precompiling "src/gen/CatalogService.Countries_texts.hdbview"...
      Expanded from "src/gen/CatalogService.Countries.hdbview"
     Precompiling "src/gen/CatalogService.Authors.hdbview$CATALOGSERVICE_AUTHORS.validate"... ok (0s 7ms)
Precompiling "src/gen/CatalogService.Orders.hdbview"...
Precompiling "src/gen/CatalogService.Books.hdbview$CATALOGSERVICE_BOOKS.validate"... ok  (0s 6ms)
     Precompiling "src/gen/CatalogService.Orders.hdbview$CATALOGSERVICE_ORDERS.validate"...
Expanded from "src/gen/CatalogService.Orders.hdbview"
Precompiling "src/gen/CatalogService.Books_texts.hdbview"... ok (0s 8ms)
Precompiling "src/gen/localized.CatalogService.Authors.hdbview"...
Precompiling "src/gen/CatalogService.Orders.hdbview"... ok (0s 7ms)
Precompiling "src/gen/localized.CatalogService.Authors.hdbview$LOCALIZED_CATALOGSERVICE_AUTHORS.validate"...
      Expanded from "src/gen/localized.CatalogService.Authors.hdbview"
     Precompiling "src/gen/CatalogService.Authors.hdbview"... ok  (0s 14ms)
     Precompiling "src/gen/localized.CatalogService.Books.hdbview"...
     Precompiling "src/gen/CatalogService.Books.hdbview"... ok  (0s 14ms)
     Precompiling "src/gen/localized.CatalogService.Books.hdbview$LOCALIZED_CATALOGSERVICE_BOOKS.validate"...
Expanded from "src/gen/localized.CatalogService.Books.hdbview"
Precompiling "src/gen/localized.CatalogService.Authors.hdbview"... ok (0s 5ms)
Precompiling "src/gen/localized.CatalogService.Countries.hdbview"...
Precompiling "src/gen/CatalogService.Countries.hdbview$CATALOGSERVICE_COUNTRIES.validate"... ok  (0s 13ms)
     Precompiling "src/gen/localized.CatalogService.Countries.hdbview$LOCALIZED_CATALOGSERVICE_COUNTRIES.validate"...
Expanded from "src/gen/localized.CatalogService.Countries.hdbview"
Precompiling "src/gen/CatalogService.Countries_texts.hdbview"... ok (0s 14ms)
Precompiling "src/gen/localized.CatalogService.Orders.hdbview"...
Precompiling "src/gen/CatalogService.Countries.hdbview"... ok (0s 16ms)
Precompiling "src/gen/localized.CatalogService.Orders.hdbview$LOCALIZED_CATALOGSERVICE_ORDERS.validate"...
      Expanded from "src/gen/localized.CatalogService.Orders.hdbview"
     Precompiling "src/gen/CatalogService.Orders.hdbview$CATALOGSERVICE_ORDERS.validate"... ok (0s 10ms)
Precompiling "src/gen/localized.my.bookshop.Authors.hdbview"...
Precompiling "src/gen/localized.CatalogService.Countries.hdbview"... ok (0s 6ms)
Precompiling "src/gen/localized.my.bookshop.Authors.hdbview$LOCALIZED_MY_BOOKSHOP_AUTHORS.validate"...
      Expanded from "src/gen/localized.my.bookshop.Authors.hdbview"
     Precompiling "src/gen/localized.CatalogService.Books.hdbview$LOCALIZED_CATALOGSERVICE_BOOKS.validate"... ok (0s 7ms)
Precompiling "src/gen/localized.my.bookshop.Books.hdbview"...
Precompiling "src/gen/localized.CatalogService.Authors.hdbview$LOCALIZED_CATALOGSERVICE_AUTHORS.validate"... ok  (0s 9ms)
     Precompiling "src/gen/localized.my.bookshop.Books.hdbview$LOCALIZED_MY_BOOKSHOP_BOOKS.validate"...
Expanded from "src/gen/localized.my.bookshop.Books.hdbview"
Precompiling "src/gen/localized.CatalogService.Books.hdbview"... ok (0s 13ms)
Precompiling "src/gen/localized.CatalogService.Countries.hdbview$LOCALIZED_CATALOGSERVICE_COUNTRIES.validate"... ok  (0s 10ms)
     Precompiling "src/gen/localized.my.bookshop.Orders.hdbview"...
     Precompiling "src/gen/localized.my.bookshop.Orders.hdbview$LOCALIZED_MY_BOOKSHOP_ORDERS.validate"...
Expanded from "src/gen/localized.my.bookshop.Orders.hdbview"
Precompiling "src/gen/localized.CatalogService.Orders.hdbview$LOCALIZED_CATALOGSERVICE_ORDERS.validate"... ok  (0s 10ms)
     Precompiling "src/gen/localized.sap.common.Countries.hdbview"...
     Precompiling "src/gen/localized.my.bookshop.Authors.hdbview$LOCALIZED_MY_BOOKSHOP_AUTHORS.validate"... ok (0s 8ms)
Precompiling "src/gen/localized.sap.common.Countries.hdbview$LOCALIZED_SAP_COMMON_COUNTRIES.validate"...
      Expanded from "src/gen/localized.sap.common.Countries.hdbview"
     Precompiling "src/gen/localized.CatalogService.Orders.hdbview"... ok  (0s 12ms)
     Precompiling "src/gen/my.bookshop.Authors.hdbtable"...
     Precompiling "src/gen/localized.my.bookshop.Authors.hdbview"... ok  (0s 10ms)
     Precompiling "src/gen/my.bookshop.Authors.hdbtable$MY_BOOKSHOP_AUTHORS.validate"...
Expanded from "src/gen/my.bookshop.Authors.hdbtable"
Precompiling "src/gen/localized.my.bookshop.Books.hdbview$LOCALIZED_MY_BOOKSHOP_BOOKS.validate"... ok  (0s 9ms)
     Precompiling "src/gen/my.bookshop.Books.hdbtable"...
     Precompiling "src/gen/localized.my.bookshop.Books.hdbview"... ok  (0s 11ms)
     Precompiling "src/gen/my.bookshop.Books.hdbtable$MY_BOOKSHOP_BOOKS.validate"...
Expanded from "src/gen/my.bookshop.Books.hdbtable"
Precompiling "src/gen/localized.my.bookshop.Orders.hdbview$LOCALIZED_MY_BOOKSHOP_ORDERS.validate"... ok  (0s 6ms)
     Precompiling "src/gen/my.bookshop.Books_texts.hdbtable"...
     Precompiling "src/gen/my.bookshop.Authors.hdbtable"... ok  (0s 7ms)
     Precompiling "src/gen/my.bookshop.Orders.hdbtable"...
     Precompiling "src/gen/localized.my.bookshop.Orders.hdbview"... ok  (0s 10ms)
     Precompiling "src/gen/my.bookshop.Orders.hdbtable$MY_BOOKSHOP_ORDERS.validate"...
Expanded from "src/gen/my.bookshop.Orders.hdbtable"
Precompiling "src/gen/localized.sap.common.Countries.hdbview$LOCALIZED_SAP_COMMON_COUNTRIES.validate"... ok  (0s 10ms)
     Precompiling "src/gen/sap.common.Countries.hdbtable"...
     Precompiling "src/gen/localized.sap.common.Countries.hdbview"... ok  (0s 11ms)
     Precompiling "src/gen/sap.common.Countries.hdbtable$SAP_COMMON_COUNTRIES.validate"...
Expanded from "src/gen/sap.common.Countries.hdbtable"
Precompiling "src/gen/my.bookshop.Authors.hdbtable$MY_BOOKSHOP_AUTHORS.validate"... ok  (0s 11ms)
     Precompiling "src/gen/my.bookshop.Books.hdbtable$MY_BOOKSHOP_BOOKS.validate"... ok (0s 8ms)
Precompiling "src/gen/sap.common.Countries_texts.hdbtable"...
Precompiling "src/gen/my.bookshop.Books_texts.hdbtable"... ok (0s 8ms)
Precompiling "src/gen/my.bookshop.Books.hdbtable"... ok (0s 10ms)
Precompiling "src/gen/my.bookshop.Orders.hdbtable"... ok (0s 7ms)
Precompiling "src/gen/my.bookshop.Orders.hdbtable$MY_BOOKSHOP_ORDERS.validate"... ok  (0s 9ms)
     Precompiling "src/gen/sap.common.Countries_texts.hdbtable"... ok  (0s 5ms)
     Precompiling "src/gen/sap.common.Countries.hdbtable"... ok  (0s 8ms)
     Precompiling "src/gen/sap.common.Countries.hdbtable$SAP_COMMON_COUNTRIES.validate"... ok (0s 8ms)
Precompiling... ok (0s 66ms)
Merging...
Merging... ok (0s 26ms)
Calculating dependencies... ok (0s 227ms)
Processing work list...
Deploying "src/gen/my.bookshop.Authors.hdbtable"...
Deploying "src/gen/my.bookshop.Books.hdbtable"...
Deploying "src/gen/my.bookshop.Books_texts.hdbtable"...
Deploying "src/gen/my.bookshop.Orders.hdbtable"...
Deploying "src/gen/sap.common.Countries.hdbtable"...
Deploying "src/gen/sap.common.Countries_texts.hdbtable"...
Deploying "src/gen/my.bookshop.Authors.hdbtable"... ok (0s 16ms)
Deploying "src/gen/my.bookshop.Books.hdbtable"... ok (0s 22ms)
Deploying "src/gen/my.bookshop.Books_texts.hdbtable"... ok (0s 36ms)
Deploying "src/gen/my.bookshop.Orders.hdbtable"... ok (0s 36ms)
Deploying "src/gen/CatalogService.Books_texts.hdbview"...
Deploying "src/gen/sap.common.Countries_texts.hdbtable"... ok (0s 35ms)
Deploying "src/gen/my.bookshop.Authors.hdbtable$MY_BOOKSHOP_AUTHORS.validate"...
    Deploying "src/gen/sap.common.Countries.hdbtable"... ok  (0s 35ms)
     Expanded from "src/gen/my.bookshop.Authors.hdbtable"
    Deploying "src/gen/CatalogService.Countries_texts.hdbview"...
    Deploying "src/gen/sap.common.Countries.hdbtable$SAP_COMMON_COUNTRIES.validate"...
Expanded from "src/gen/sap.common.Countries.hdbtable"
Deploying "src/gen/my.bookshop.Authors.hdbtable$MY_BOOKSHOP_AUTHORS.validate"... ok  (0s 6ms)
    Deploying "src/gen/my.bookshop.Books.hdbtable$MY_BOOKSHOP_BOOKS.validate"...
Expanded from "src/gen/my.bookshop.Books.hdbtable"
Deploying "src/gen/sap.common.Countries.hdbtable$SAP_COMMON_COUNTRIES.validate"... ok  (0s 9ms)
    Deploying "src/gen/localized.sap.common.Countries.hdbview"...
    Deploying "src/gen/CatalogService.Countries.hdbview"...
    Deploying "src/gen/my.bookshop.Books.hdbtable$MY_BOOKSHOP_BOOKS.validate"... ok (0s 27ms)
Deploying "src/gen/my.bookshop.Orders.hdbtable$MY_BOOKSHOP_ORDERS.validate"...
     Expanded from "src/gen/my.bookshop.Orders.hdbtable"
    Deploying "src/gen/localized.my.bookshop.Books.hdbview"...
    Deploying "src/gen/CatalogService.Authors.hdbview"...
    Deploying "src/gen/my.bookshop.Orders.hdbtable$MY_BOOKSHOP_ORDERS.validate"... ok (0s 62ms)
Deploying "src/gen/localized.my.bookshop.Authors.hdbview"...
Deploying "src/gen/CatalogService.Books_texts.hdbview"... ok (0s 96ms)
Deploying "src/gen/CatalogService.Books.hdbview"...
Deploying "src/gen/CatalogService.Countries_texts.hdbview"... ok (0s 97ms)
Deploying "src/gen/localized.my.bookshop.Orders.hdbview"...
Deploying "src/gen/localized.sap.common.Countries.hdbview"... ok (0s 120ms)
Deploying "src/gen/CatalogService.Orders.hdbview"...
Deploying "src/gen/CatalogService.Countries.hdbview"... ok (0s 120ms)
Deploying "src/gen/localized.sap.common.Countries.hdbview$LOCALIZED_SAP_COMMON_COUNTRIES.validate"...
     Expanded from "src/gen/localized.sap.common.Countries.hdbview"
    Deploying "src/gen/localized.sap.common.Countries.hdbview$LOCALIZED_SAP_COMMON_COUNTRIES.validate"... ok (0s 23ms)
Deploying "src/gen/CatalogService.Countries.hdbview$CATALOGSERVICE_COUNTRIES.validate"...
     Expanded from "src/gen/CatalogService.Countries.hdbview"
    Deploying "src/gen/CatalogService.Authors.hdbview"... ok  (0s 121ms)
    Deploying "src/gen/localized.CatalogService.Countries.hdbview"...
    Deploying "src/gen/localized.my.bookshop.Orders.hdbview"... ok  (0s 57ms)
    Deploying "src/gen/localized.my.bookshop.Books.hdbview"... ok  (0s 121ms)
    Deploying "src/gen/CatalogService.Books.hdbview"... ok  (0s 69ms)
    Deploying "src/gen/CatalogService.Books.hdbview$CATALOGSERVICE_BOOKS.validate"...
Expanded from "src/gen/CatalogService.Books.hdbview"
Deploying "src/gen/CatalogService.Countries.hdbview$CATALOGSERVICE_COUNTRIES.validate"... ok  (0s 16ms)
    Deploying "src/gen/localized.my.bookshop.Authors.hdbview"... ok  (0s 75ms)
    Deploying "src/gen/localized.my.bookshop.Authors.hdbview$LOCALIZED_MY_BOOKSHOP_AUTHORS.validate"...
Expanded from "src/gen/localized.my.bookshop.Authors.hdbview"
Deploying "src/gen/CatalogService.Orders.hdbview"... ok (0s 57ms)
Deploying "src/gen/CatalogService.Books.hdbview$CATALOGSERVICE_BOOKS.validate"... ok  (0s 27ms)
    Deploying "src/gen/CatalogService.Authors.hdbview$CATALOGSERVICE_AUTHORS.validate"...
Expanded from "src/gen/CatalogService.Authors.hdbview"
Deploying "src/gen/localized.my.bookshop.Authors.hdbview$LOCALIZED_MY_BOOKSHOP_AUTHORS.validate"... ok  (0s 23ms)
    Deploying "src/gen/localized.my.bookshop.Books.hdbview$LOCALIZED_MY_BOOKSHOP_BOOKS.validate"...
Expanded from "src/gen/localized.my.bookshop.Books.hdbview"
Deploying "src/gen/CatalogService.Authors.hdbview$CATALOGSERVICE_AUTHORS.validate"... ok  (0s 4ms)
    Deploying "src/gen/CatalogService.Orders.hdbview$CATALOGSERVICE_ORDERS.validate"...
Expanded from "src/gen/CatalogService.Orders.hdbview"
Deploying "src/gen/localized.my.bookshop.Books.hdbview$LOCALIZED_MY_BOOKSHOP_BOOKS.validate"... ok  (0s 7ms)
    Deploying "src/gen/localized.my.bookshop.Orders.hdbview$LOCALIZED_MY_BOOKSHOP_ORDERS.validate"...
Expanded from "src/gen/localized.my.bookshop.Orders.hdbview"
Deploying "src/gen/localized.CatalogService.Books.hdbview"...
Deploying "src/gen/localized.CatalogService.Countries.hdbview"... ok (0s 46ms)
Deploying "src/gen/localized.CatalogService.Authors.hdbview"...
Deploying "src/gen/localized.CatalogService.Countries.hdbview$LOCALIZED_CATALOGSERVICE_COUNTRIES.validate"...
     Expanded from "src/gen/localized.CatalogService.Countries.hdbview"
    Deploying "src/gen/localized.my.bookshop.Orders.hdbview$LOCALIZED_MY_BOOKSHOP_ORDERS.validate"... ok (0s 5ms)
Deploying "src/gen/localized.CatalogService.Orders.hdbview"...
Deploying "src/gen/localized.CatalogService.Countries.hdbview$LOCALIZED_CATALOGSERVICE_COUNTRIES.validate"... ok  (0s 7ms)
    Deploying "src/gen/CatalogService.Orders.hdbview$CATALOGSERVICE_ORDERS.validate"... ok (0s 15ms)
Deploying "src/gen/localized.CatalogService.Books.hdbview"... ok (0s 55ms)
Deploying "src/gen/localized.CatalogService.Authors.hdbview"... ok (0s 56ms)
Deploying "src/gen/localized.CatalogService.Authors.hdbview$LOCALIZED_CATALOGSERVICE_AUTHORS.validate"...
     Expanded from "src/gen/localized.CatalogService.Authors.hdbview"
    Deploying "src/gen/localized.CatalogService.Orders.hdbview"... ok  (0s 51ms)
    Deploying "src/gen/localized.CatalogService.Authors.hdbview$LOCALIZED_CATALOGSERVICE_AUTHORS.validate"... ok (0s 3ms)
Deploying "src/gen/localized.CatalogService.Books.hdbview$LOCALIZED_CATALOGSERVICE_BOOKS.validate"...
     Expanded from "src/gen/localized.CatalogService.Books.hdbview"
    Deploying "src/gen/localized.CatalogService.Books.hdbview$LOCALIZED_CATALOGSERVICE_BOOKS.validate"... ok (0s 4ms)
Deploying "src/gen/localized.CatalogService.Orders.hdbview$LOCALIZED_CATALOGSERVICE_ORDERS.validate"...
     Expanded from "src/gen/localized.CatalogService.Orders.hdbview"
    Deploying "src/gen/localized.CatalogService.Orders.hdbview$LOCALIZED_CATALOGSERVICE_ORDERS.validate"... ok (0s 4ms)
Processing work list... ok (0s 322ms)
Finalizing...
Finalizing... ok (0s 109ms)
Make succeeded (12 warnings): 23 files deployed (effective 39), 0 files undeployed (effective 0), 0 dependent files redeployed
Making... ok (1s 376ms)
Enabling table replication for the container schema "B96C1E357CE74672AEE8487D2F664AAB"...
Enabling table replication for the container schema "B96C1E357CE74672AEE8487D2F664AAB"... ok (0s 40ms)
Starting make in the container "B96C1E357CE74672AEE8487D2F664AAB" with 23 files to deploy, 0 files to undeploy... ok (1s 470ms)
Deploying to the container "B96C1E357CE74672AEE8487D2F664AAB"... ok (9s 899ms)
No default-access-role handling needed; global role "B96C1E357CE74672AEE8487D2F664AAB::access_role" will not be adapted
Unlocking the container "B96C1E357CE74672AEE8487D2F664AAB"...
Unlocking the container "B96C1E357CE74672AEE8487D2F664AAB"... ok (0s 1ms)

Retrieving data from Cloud Foundry...
Binding db to Cloud Foundry managed service baoinstance1:baoinstance1-key with kind hana
3.CAP*with_HANA_Cloud*.30_05_2023/.gitignore:7:.cdsrc-private.json .cdsrc-private.json

Saving bindings to .cdsrc-private.json in profile hybrid
TIP: Run with cloud bindings: cds watch --profile hybrid
If not already done, use cds add hana to configure the project for SAP HANA.

Done.

</details>
