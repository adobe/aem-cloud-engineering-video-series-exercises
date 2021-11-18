# Hands-on exercise:  Assets and Microservices

> This hands-on exercise builds on [Hands-on exercise: Search and Indexes](https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session7-indexes)

Now that you understand how to move content from AEM 6.x to AEM as a Cloud Service and index it, let's explore how AEM as a Cloud Service processes and renditions assets.

Apply your knowledge by trying out what you learned with this hands-on exercise.

## Supporting content 

Prior to trying the hands-on exercise, ensure you're familiar with the following topics, or review the following materials:

+[Asset Compute Microservices](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/asset-compute-microservices.html?lang=en)

## Hands-on exercise steps

In this exercise, we will define a custom processing profile and apply it to an AEM assets folder.

1. Navigate to __Tools > Assets > Processing Profiles__

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

1. Navigate to AEM as a Cloud Service

2. Go to __Tools > Security > Users__

3. Create a new user, set his password and set user group to `administrators`.

4. Download these images (or use your own) [Demo_Images.zip](https://git.corp.adobe.com/aem-enablement/CloudAccelerationBootcamp/tree/session9/images)

5. Open command prompt/terminal

6. Run the following command
    > `aio-aem aem:upload path_to_Demo_Images_folder -h <AEM as Cloud Service Instance URL> -c username:password`

    e.g.
    > `aio-aem aem:upload Demo_Images -h https://author-pXXXX-eXXXX.adobeaemcloud.com -c uploadUsers:myPassword`

7. Following output should be displayed on the terminal window

    > ![2.PNG](./images/two.png)

    > Verify the uploadURIs pointing to azure blob storage

    > ![3.PNG](./images/four.png)
    
8. Go to Assets > Files > aem-upload-xxxxx and verify the uploaded assets

    > ![3.PNG](./images/three.png)



