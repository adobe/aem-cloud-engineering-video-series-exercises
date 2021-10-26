# Cloud Acceleration Bootcamp - Session 8 Assets and Microservices

## Pre-Work

1. Review https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#changes-in-aem-as-a-cloud-service to understand changes related to indexes in AEM as a Cloud Service

2. Clone https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session7-indexes/new-index-content GIT Repository.

3. Clone https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session7-indexes/sample-ethos-image GIT Repository

4. Copy /new-index-content/src/main/content/jcr_root/_oak_index folder to the Cloud Manager GIT Project

5. Modify the filter.xml to include the _oak_index folder

6. Add <allowIndexDefinitions>true</allowIndexDefinitions> to filevault-package-maven-plugin plugin configuration in Parent pom.xml.

7. Do a local maven build and deploy.


## Bootcamp: Topics covered in Session 8: Assets and Microservices

Homework review: <br>
Verify new index definitions are correctly deployed and being used by search queries.<br>
Introduction <br>
Overview<br>
High level Architecture <br>
What's new and notable changes<br>
Asset Processing Options <br>
Standard processing profiles<br>
Custom processing profiles with project firefly<br>
Post Processing Workflows <br>
Asset Ingestion Use cases <br>
aem-upload tool <br>
aio-cli aem-upload plugin <br>
Asset bulk ingestor tool<br>
Session homework<br>
Create standard and custom processing profiles<br>
Create and utilize Asset post processing workflows<br>
Use asset ingestion tools<br>



# Cloud Acceleration Bootcamp - Session 8 Homework

In this scenario, we will define a custom processing profile and apply it to an AEM assets folder.

1. Navigate to Tools > Assets > Processing Profiles

 > ![1.PNG](./images/1.png)
 
2. Click 'Create'

3. Provide a name for the new profile.

4. Create a custom rendition for png and jpg.

  Set the appropriate height and width.

> ![5.PNG](./images/5.png)

5. 'Save'

6. Select Profile and use the Apply Profile to Folder(s) wizard.

> ![8.PNG](./images/8.png)

7. You can also Assign/Remove Processing Profile to folder via folder properties page, to do so

  > Navigate to the desired folder <br>

Select folder and click the "Properties" button in the Action Bar

> ![9.PNG](./images/9.png)

Select Processing Profile from "Processing Profiles" tab

 ![10.PNG](./images/10.png)<br>
 
8. Upload an asset to the folder.

9. Verify the custom renditions being generated.

#### Usage of Asset Upload Tool

This library supports uploading files to a target instance, while providing support for monitoring transfer progress, cancelling transfers, and other features.

To install the and use the command locally

> ``` npm install -g @adobe/aio-cli-plugin-aem ```

> ```  aio-aem (-v|--version|version) ```

> ``` aio-aem --help ```

#### Upload asset binaries to AEM

1. Navigate to AEM as a Cloud Service Instance.

2. Go to Tools > Security > Users

3. Create a new user, set his password and set user group to `administrators`.

4. Download these images (or use your own) [Demo_Images.zip](https://git.corp.adobe.com/aem-enablement/CloudAccelerationBootcamp/tree/session9/images)

5. Open command prompt/terminal

6. Run the following command
    > aio-aem aem:upload path_to_Demo_Images_folder -h <AEM as Cloud Service Instance URL> -c username:password

    e.g.
    > aio-aem aem:upload Demo_Images -h https://author-p9357-e17906.adobeaemcloud.com -c ksaner:password

7. Following output should be displayed on the terminal window

    > ![2.PNG](./images/two.png)

    > Verify the uploadURIs pointing to azure blob storage

    > ![3.PNG](./images/four.png)
    
8. Go to Assets > Files > aem-upload-xxxxx and verify the uploaded assets

    > ![3.PNG](./images/three.png)



