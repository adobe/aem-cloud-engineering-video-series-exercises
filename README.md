# Cloud Acceleration Bootcamp - Session 7 Search and Indexing

# Cloud Acceleration Bootcamp - Session 7 Pre-work

1). Download and Install the [Content Transfer Tool](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

2). Transfer content from your AEM 6.4 to the sandbox [Assets Here](https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session6-transfercontent/assets) using the Content Transfer Tool (CTT).

## Bootcamp: Topics covered in Session 7: Search and Indexing


### Review Notable Changes

This section will cover the notable changes from legacy indexes in AEM as a Cloud Service

### Transform Legacy Indexes using the Index Converter

This section will cover the index converter tool and how to use it with legacy indexes. 

### Transform Legacy Indexes using the Index Converter

This section will cover how to deploy newly created OAK indexed to AEM as a Cloud Service. 

### Troubleshooting Tips/Real World Scenarios

This section will cover troubleshooting tips and a deep diver scenario into some real world use cases. 

# Cloud Acceleration Bootcamp - Session 7 Homework

1. Review https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#changes-in-aem-as-a-cloud-service to understand changes related to indexes in AEM as a Cloud Service
2. Clone https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session7-indexes/new-index-content GIT Repository.
3. Clone https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session7-indexes/sample-ethos-image GIT Repository
4. Copy ` /new-index-content/src/main/content/jcr_root/_oak_index ` folder to the Cloud Manager GIT Project
5. Modify the ` filter.xml ` to include the ` _oak_index ` folder
6. Add ` <allowIndexDefinitions>true</allowIndexDefinitions> ` to ` filevault-package-maven-plugin ` plugin configuration in Parent `pom.xml`.
7. Do a local maven build and deploy.
8. Commit the new code with index definitions to Cloud Manager Git.


