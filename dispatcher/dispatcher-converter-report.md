# AEM as a Cloud Service - Dispatcher Conversion Report
This report contains the changes that have been made to your dispatcher configurations by the converter.  After reviewing these changes, you should simply run the dispatcher validator on the new configurations, with the `dispatcher` subcommand: `validator dispatcher .` to check the state. For any error, see the [Troubleshooting](./TroubleShooting.md) section of the
validator tool documentation.
#### Test your configuration with a local deployment (requires Docker installation)

Using the script `docker_run.sh` in the Dispatcher SDK, you can test that
your configuration does not contain any other error that would only show up in 
deployment:

##### Step 1: Generate deployment information with the validator

```
validator full -d out .
```
This validates the full configuration and generates deployment information in `out`

##### Step 2: Start the dispatcher in a docker image with that deployment information

With your AEM publish server running on your macOS computer, listening on port 4503,
you can run start the dispatcher in front of that server as follows:
``` 
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```
This will start the container and expose Apache on local port 8080.

If the validator no longer reports any issue and the docker container starts up without
any failures or warnings, you're ready to move your configuration to a `dispatcher/src`
subdirectory of your git repository.


## Dispatcher Configuration changes

The structure of the project's dispatcher configurations folder should be as shown bellow :
```./
├── conf.d
│   ├── available_vhosts
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── default.vhost -> ../available_vhosts/default.vhost
│   └── rewrites
│   │   ├── default_rewrite.rules
│   │   └── rewrite.rules
│   └── variables
|       ├── custom.vars
│       └── global.vars
└── conf.dispatcher.d
    ├── available_farms
    │   └── default.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   ├── README
    │   └── default.farm -> ../available_farms/default.farm
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
        ├── default_virtualhosts.any
        └── virtualhosts.any
```

For conversion of the provided configurations to Dispatcher configuration for AEM as a Cloud Service, we have made the following changes to the dispatcher configuration:

#### Get rid of ununsed subfolders and files
Remove subfolders `conf` and `conf.modules.d` as well as files matching `conf.d/*.conf` .

| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/autoindex.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/autoindex.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/dispatcher_vhost.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/dispatcher_vhost.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/logformat.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/logformat.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/mimetypes3d.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/mimetypes3d.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/remoteip.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/remoteip.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/security.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/security.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/userdir.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/userdir.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/welcome.conf |
| Deleted | target/dispatcher/src/conf.d | Deleted file target/dispatcher/src/conf.d/welcome.conf |

#### Get rid of all non-publish virtual hosts
Remove any virtual host file in `conf.d/enabled_vhosts` that has `author` `unhealthy` , `health` , `lc` or `flush` in its name. All virtual host files in `conf.d/available_vhosts` that are not linked to should be removed.

| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Deleted | target/dispatcher/src/conf.d/enabled_vhosts | Deleted file target/dispatcher/src/conf.d/enabled_vhosts/aem_author.vhost |
| Deleted | target/dispatcher/src/conf.d/enabled_vhosts | Deleted file target/dispatcher/src/conf.d/enabled_vhosts/aem_author.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/000_unhealthy_author.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/000_unhealthy_author.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_author.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_author.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/000_unhealthy_publish.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/000_unhealthy_publish.vhost |
| Deleted | target/dispatcher/src/conf.d/enabled_vhosts | Deleted file target/dispatcher/src/conf.d/enabled_vhosts/aem_health.vhost |
| Deleted | target/dispatcher/src/conf.d/enabled_vhosts | Deleted file target/dispatcher/src/conf.d/enabled_vhosts/aem_health.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_health.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_health.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_lc.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_lc.vhost |
| Deleted | target/dispatcher/src/conf.d/enabled_vhosts | Deleted file target/dispatcher/src/conf.d/enabled_vhosts/aem_flush.vhost |
| Deleted | target/dispatcher/src/conf.d/enabled_vhosts | Deleted file target/dispatcher/src/conf.d/enabled_vhosts/aem_flush.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_flush.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_flush.vhost |
| Deleted | target/dispatcher/src/conf.d/available_vhosts | Deleted file target/dispatcher/src/conf.d/available_vhosts/aem_publish.vhost |

#### Check rewrites folder In directory `conf.d/rewrites`, remove any file named `base_rewrite.rules` and `xforwarded_forcessl_rewrite.rules` and remove Include statements in the virtual host files referring to them.undefinedIf `conf.d/rewrites` now contains a single file, it should be renamed to `rewrite.rules` and adapt the Include statements referring to that file in the virtual host files as well.undefinedIf the folder however contains multiple, virtual host specific files, their contents should be copied to the Include statement referring to them in the virtual host files.


| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Deleted | target/dispatcher/src/conf.d/rewrites | Deleted file target/dispatcher/src/conf.d/rewrites/base_rewrite.rules |
| Deleted | target/dispatcher/src/conf.d/rewrites | Deleted file target/dispatcher/src/conf.d/rewrites/xforwarded_forcessl_rewrite.rules |

#### Check variables folderIn directory `conf.d/variables`, remove any file named `ams_default.vars` and remove Include statements in the virtual host files referring to them.undefinedConsolidate variable definitions from all remaining vars files in `conf.d/variables`into a single file named `custom.vars` and adapt the Include statements referring to them in the virtual host files.


| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Deleted | target/dispatcher/src/conf.d/variables | Deleted file target/dispatcher/src/conf.d/variables/ams_default.vars |

#### Get rid of all non-publish farmsRemove any farm file in `conf.dispatcher.d/enabled_farms` that has `author , unhealthy , health , lc , flush` in its name. All farm files in `conf.dispatcher.d/available_farms` that are not linked to can be removed as well.


| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Deleted | target/dispatcher/src/conf.dispatcher.d/enabled_farms | Deleted file target/dispatcher/src/conf.dispatcher.d/enabled_farms/000_ams_author_farm.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/enabled_farms | Deleted file target/dispatcher/src/conf.dispatcher.d/enabled_farms/000_ams_author_farm.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/available_farms | Deleted file target/dispatcher/src/conf.dispatcher.d/available_farms/000_ams_author_farm.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/available_farms | Deleted file target/dispatcher/src/conf.dispatcher.d/available_farms/000_ams_author_farm.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/available_farms | Deleted file target/dispatcher/src/conf.dispatcher.d/available_farms/001_ams_lc_farm.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/available_farms | Deleted file target/dispatcher/src/conf.dispatcher.d/available_farms/001_ams_lc_farm.any |

#### Check cacheIn directory `conf.dispatcher.d/cache`, remove any file prefixed `ams_`. undefinedIf `conf.dispatcher.d/cache` is now empty, copy the file `conf.dispatcher.d/cache/rules.any` from the standard dispatcher configuration to this folder. The standard dispatcher configuration can be found in the folder src of the dispatcher SDK. Adapt the `$include` statements referring to the `ams_*_cache.any` rule files in the farm files as well.undefined If instead `conf.dispatcher.d/cache` now contains a single file with suffix `_cache.any`, it should be renamed to `rules.any` and adapt the `$include` statements referring to that file in the farm files as well.undefinedIf the folder however contains multiple, farm specific files with that pattern, their contents should be copied to the `$include` statement referring to them in the farm files, and the delete the files. Remove any file that has the suffix `_invalidate_allowed.any`.undefinedCopy the file `conf.dispatcher.d/cache/default_invalidate_any` from the default AEM in the Cloud dispatcher configuration to that location. In each farm file, remove any contents in the `cache/allowedClients` section and replace it with: `$include "../cache/default_invalidate.any"`


| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Added | target/dispatcher/src/conf.dispatcher.d/cache | Copied file 'conf.dispatcher.d/cache/default_rules.any from the standard dispatcher configuration to target/dispatcher/src/conf.dispatcher.d/cache |
| Deleted | target/dispatcher/src/conf.dispatcher.d/cache | Deleted file target/dispatcher/src/conf.dispatcher.d/cache/ams_author_cache.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/cache | Deleted file target/dispatcher/src/conf.dispatcher.d/cache/ams_author_invalidate_allowed.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/cache | Deleted file target/dispatcher/src/conf.dispatcher.d/cache/ams_publish_cache.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/cache | Deleted file target/dispatcher/src/conf.dispatcher.d/cache/ams_publish_invalidate_allowed.any |
| Added | target/dispatcher/src/conf.dispatcher.d/cache | Consolidated content of rule files into target/dispatcher/src/conf.dispatcher.d/cache/rules.any |
| Replaced | target/dispatcher/src/conf.dispatcher.d/available_farms/999_ams_publish.farm | Replaced content of section '/allowedClients' with include statement $include "../cache/default_invalidate.any" |
| Replaced | target/dispatcher/src/conf.dispatcher.d/enabled_farms/999_ams_publish.farm | Replaced content of section '/allowedClients' with include statement $include "../cache/default_invalidate.any" |

#### Check client headers
In directory `conf.dispatcher.d/clientheaders`, remove any file prefixed `ams_` .undefinedIf `conf.dispatcher.d/clientheaders` now contains a single file with suffix `_clientheaders.any` , it should be renamed to `clientheaders.any` and adapt the `$include` statements referring to that file in the farm files as well.undefinedIf the folder however contains multiple, farm specific files with that pattern, their contents should be copied to the `$include` statement referring to them in the farm files.undefinedCopy the file `conf.dispatcher/clientheaders/default_clientheaders.any` from the default AEM as a Cloud Service dispatcher configuration to that location.undefinedIn each farm file, replace any clientheader include statements that looks the following : undefined`$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`undefined`$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"` undefinedwith the statement: `$include "../clientheaders/default_clientheaders.any"`

| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Deleted | target/dispatcher/src/conf.dispatcher.d/clientheaders | Deleted file target/dispatcher/src/conf.dispatcher.d/clientheaders/ams_author_clientheaders.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/clientheaders | Deleted file target/dispatcher/src/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/clientheaders | Deleted file target/dispatcher/src/conf.dispatcher.d/clientheaders/ams_lc_clientheaders.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/clientheaders | Deleted file target/dispatcher/src/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any |
| Added | target/dispatcher/src/conf.dispatcher.d/clientheaders | Copied file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' from the standard dispatcher configuration to target/dispatcher/src/conf.dispatcher.d/clientheaders |
| Added | target/dispatcher/src/conf.dispatcher.d/clientheaders | Copied file 'conf.dispatcher.d/clientheaders/clientheaders.any' from the standard dispatcher configuration to target/dispatcher/src/conf.dispatcher.d/clientheaders |

#### Check filter
In directory `conf.dispatcher.d/filters`, remove any file prefixed `ams_`.undefined If `conf.dispatcher.d/filters` now contains a single file it should be renamed to `filters.any` and adapt the `$include` statements referring to that file in the farm files as well.undefinedIf the folder however contains multiple, farm specific files with that pattern, their contents should be copied to the `$include` statement referring to them in the farm files.undefinedCopy the file `conf.dispatcher/filters/default_filters.any` from the default AEM as a Cloud Service dispatcher configuration to that location.undefinedIn each farm file, replace any filter include statements that looks as follows: `$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`undefined with the statement: `$include "../filters/default_filters.any"`

| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Deleted | target/dispatcher/src/conf.dispatcher.d/filters | Deleted file target/dispatcher/src/conf.dispatcher.d/filters/ams_author_filters.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/filters | Deleted file target/dispatcher/src/conf.dispatcher.d/filters/ams_lc_filters.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/filters | Deleted file target/dispatcher/src/conf.dispatcher.d/filters/ams_publish_filters.any |
| Added | target/dispatcher/src/conf.dispatcher.d/filters | Copied file 'conf.dispatcher.d/filters/default_filters.any' from the standard dispatcher configuration to target/dispatcher/src/conf.dispatcher.d/filters |
| Added | target/dispatcher/src/conf.dispatcher.d/filters | Copied file 'conf.dispatcher.d/filters/filters.any` 'from the standard dispatcher configuration to target/dispatcher/src/conf.dispatcher.d/filters |

#### Check renders
NaNCopy the file `conf.dispatcher.d/renders/default_renders.any` from the default AEM as a Cloud Service dispatcher configuration to that location.undefinedIn each farm file, remove any contents in the renders section and replace it with: `$include "../renders/default_renders.any"`

| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Deleted | target/dispatcher/src/conf.dispatcher.d/renders | Deleted file target/dispatcher/src/conf.dispatcher.d/renders/ams_author_renders.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/renders | Deleted file target/dispatcher/src/conf.dispatcher.d/renders/ams_lc_renders.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/renders | Deleted file target/dispatcher/src/conf.dispatcher.d/renders/ams_publish_renders.any |
| Added | target/dispatcher/src/conf.dispatcher.d/renders |  Copied file 'conf.dispatcher.d/renders/default_renders.any` 'from the standard dispatcher configuration to target/dispatcher/src/conf.dispatcher.d/renders |
| Replaced | target/dispatcher/src/conf.dispatcher.d/available_farms/999_ams_publish.farm | Replaced content of section '/renders' with include statement $include "../renders/default_renders.any" |
| Replaced | target/dispatcher/src/conf.dispatcher.d/enabled_farms/999_ams_publish.farm | Replaced content of section '/renders' with include statement $include "../renders/default_renders.any" |

#### Check VirtualHosts
Rename the directory `conf.dispatcher.d/vhosts` to `conf.dispatcher.d/virtualhosts`. Remove any file prefixed `ams_` .undefinedIf `conf.dispatcher.d/virtualhosts` now contains a single file it should be renamed to `virtualhosts.any` and adapt the `$include` statements referring to that file in the farm files as well.undefinedIf the folder however contains multiple, farm specific files with that pattern, their contents should be copied to the `$include` statement referring to them in the farm files.undefinedCopy the file `conf.dispatcher/virtualhosts/default_virtualhosts.any` from the default AEM as a Cloud Service dispatcher configuration to that location.undefinedIn each farm file, replace any filter include statement that looks like :`$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`undefined with the statement: `$include "../virtualhosts/default_virtualhosts.any"`

| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Renamed | target/dispatcher/src/conf.dispatcher.d | Renamed folder vhosts to virtualhosts |
| Deleted | target/dispatcher/src/conf.dispatcher.d/virtualhosts | Deleted file target/dispatcher/src/conf.dispatcher.d/virtualhosts/ams_author_vhosts.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/virtualhosts | Deleted file target/dispatcher/src/conf.dispatcher.d/virtualhosts/ams_author_vhosts.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/virtualhosts | Deleted file target/dispatcher/src/conf.dispatcher.d/virtualhosts/ams_lc_vhosts.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/virtualhosts | Deleted file target/dispatcher/src/conf.dispatcher.d/virtualhosts/ams_lc_vhosts.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/virtualhosts | Deleted file target/dispatcher/src/conf.dispatcher.d/virtualhosts/ams_publish_vhosts.any |
| Deleted | target/dispatcher/src/conf.dispatcher.d/virtualhosts | Deleted file target/dispatcher/src/conf.dispatcher.d/virtualhosts/ams_publish_vhosts.any |
| Added | target/dispatcher/src/conf.dispatcher.d/virtualhosts | Copied file 'conf.dispatcher.d/virtualhosts/default_virtualhosts.any''from the standard dispatcher configuration to target/dispatcher/src/conf.dispatcher.d/virtualhosts |
| Added | target/dispatcher/src/conf.dispatcher.d/virtualhosts | Copied file 'conf.dispatcher.d/virtualhosts/virtualhosts.any' from the standard dispatcher configuration to target/dispatcher/src/conf.dispatcher.d/virtualhosts |

#### Remove usage of non-whitelisted directives
Checking for usage of non-whitelisted directives and remove them.

| Action Type | Location | Action |
| ----------- | -------- | ------ |
| Removed | target/dispatcher/src/conf.d/available_vhosts/wknd_publish.vhost:32 <RequireAny>> | Commented out usage of non-whitelisted directives |
| Removed | target/dispatcher/src/conf.d/available_vhosts/wknd_publish.vhost:72 LogLevel | Commented out usage of non-whitelisted directives |
