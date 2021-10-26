# Adobe Experience Manager Best Practice Analyzer code examples

## URC - Unsupported Run mode Configuration

* [URC Documentation](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/urc.html)

## Update summary

This example illustrates how custom runmode-based OSGi configurations can be updated to adhere with [AEM as a Cloud Service's supported run modes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html#custom-runmodes).

### Key changes

_All OSGi configurations should be stored in a project names `ui.config` under a JCR path `/apps/<example-app>/osgiconfig/<runmode.folder>`_

* Rename run mode folder `config.staging` to the supported `config.stage` format. 
* Consolidate OSGi configurations for non-Production run modes,  , and `config.dev`, into `config.dev` which is the only non-Production run mode allowed in AEM as a Cloud Service.
    * Any OSGi configuration values that differ between the logical "QA" and "Dev" environments, must be set [using OSGi configuration environment variables](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#how-to-choose-the-appropriate-osgi-configuration-value-type).

_As part of this migration, the OSGi configuration files were converted from the legacy `xml` format defining `sling:OsgiConfig` nodes to recommended `.cfg.json` format._
