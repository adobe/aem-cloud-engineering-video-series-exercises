# Adobe Experience Manager Best Practice Analyzer code examples

## INST - Installed Artifact

* [INST Documentation](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/inst.html)

## Update summary

This example illustrates how to properly include a 3rd party package-based dependency, that's available on Maven Central, to your AEM project.

### Key changes

* Remove inclusion of the 3rd party package in the AEM project as a sub-package
* Add the 3rd party dependency to the project's `all` project's `pom.xml` as an `embedded`
    * See [Embedding Sub-packages in the Container Package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#xml-embeddeds) for details and options.
