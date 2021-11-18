# Hands-on exercise: Search and Indexing

> This hands-on exercise builds on [Hands-on exercise: Migrating Content to AEM as a Cloud Service](https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session6-transfercontent)

Now that you understand how to move content from AEM 6.x to AEM as a Cloud Service, let's explore how to create custom indexes to AEM as a Cloud Service.

Apply your knowledge by trying out what you learned with this hands-on exercise.

## Supporting content 

Prior to trying the hands-on exercise, ensure you're familiar with the following topics, or review the following materials:

+ [Repository Modernization](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/repository-modernization.html?lang=en)
+ [Search and Indexing](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/search-and-indexing.html?lang=en)

## Hands-on exercise steps

1. [Understand changes related to indexes in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#changes-in-aem-as-a-cloud-service)
2. Clone [this Git repository](https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session7-indexes/new-index-content)
3. Clone [this Git repository](https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session7-indexes/sample-ethos-image)
4. Copy `/new-index-content/src/main/content/jcr_root/_oak_index` folder from the first Git repository clone to the Cloud Manager Git project
5. Modify the `filter.xml` to include the `_oak_index  folder
6. Add `<allowIndexDefinitions>true</allowIndexDefinitions>` to `filevault-package-maven-plugin` plugin configuration in parent `pom.xml`
7. Do a local maven build and deploy
8. Commit the new code with index definitions to Cloud Manager Git
