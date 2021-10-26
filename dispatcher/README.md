# Dispatcher configuration

This module contains the AMS variant of dispatcher configurations converted using [Dispatcher Convertor tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=en) compatible with AEM as Cloud Service. 

## File Structure

```
├── conf.d
│   ├── README
│   ├── available_vhosts
│   │   └── wknd_publish.vhost
│   ├── enabled_vhosts
│   │   └── wknd_publish.vhost
│   ├── rewrites
│   ├── rewritesrewrite.rules
│   ├── variables
│   │   └── global.vars
│   └── whitelists
│       └── 000_base_whitelist.rules
└── conf.dispatcher.d
    ├── available_farms
    │   └── 999_ams_publish.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   └── 999_ams_publish.farm
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
        ├── default_virtualhosts.any
        └── virtualhosts.any
```

## Sample Migration config 

Review below sample *aem-migration-config.yaml* to convert AMS dispatcher configurations to be compatible with AEM Cloud Service.

```
dispatcherConverter:
    # Absolute path to the src folder of the dispatcher sdk. You must include the src folder itself in the path.
    sdkSrc: "/Users/John/dispatcher-sdk-2.0.40/src"
    ams:
        # Path to dispatcher configuration folder
        # (expected immediate subfolders - conf, conf.d, conf.dispatcher.d and conf.modules.d)
        cfg: "/Users/John/aem-guides-wknd-legacy/dispatcher/src"
```


## Help & Resources

* [Dispatcher in the Cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html)
* [Dispatcher Convertor](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#aio-aem-migrationdispatcher-converter)
