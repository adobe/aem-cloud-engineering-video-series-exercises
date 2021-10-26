# Cloud Acceleration Bootcamp - Session 7 Search and Indexing


## Bootcamp: Topics covered in Session 7: Search and Indexing


### Review Notable Changes

This section will cover the notable changes from legacy indexes in AEM as a Cloud Service

### Transform Legacy Indexes using the Index Converter

This section will cover the index converter tool and how to use it with legacy indexes. 

### Transform Legacy Indexes using the Index Converter

This section will cover how to deploy newly created OAK indexed to AEM as a Cloud Service. 

### Troubleshooting Tips/Real World Scenarios

This section will cover troubleshooting tips and a deep diver scenario into some real world use cases. 

# Cloud Acceleration Bootcamp - Session 8 Homework

1. Review https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#changes-in-aem-as-a-cloud-service to understand changes related to indexes in AEM as a Cloud Service
2. Clone https://git.corp.adobe.com/rekawek/new-index-playground GIT Repository.
3. Copy ` /new-index-content/src/main/content/jcr_root/_oak_index ` folder to the Cloud Manager GIT Project
4. Modify the ` filter.xml ` to include the ` _oak_index ` folder
5. Add ` <allowIndexDefinitions>true</allowIndexDefinitions> ` to ` filevault-package-maven-plugin ` plugin configuration in Parent `pom.xml`.
6. Do a local maven build and deploy.
7. Commit the new code with index definitions to Cloud Manager Git.


