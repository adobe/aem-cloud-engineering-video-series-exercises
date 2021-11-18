session4-cloud-manager
# Hands-on exercise: Cloud Manager, Develop and Deploy

> This hands-on exercise builds on [Hands-on exercise: Onboarding](https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session3-onboarding)

Now that you understand the AEM as a CLoud Service onboarding process, and how to used Adobe Admin Console to provide access to Cloud Manager and AEM as a Cloud Service, let's explore how to deploy an AEM application to AEM as a Cloud Service using Cloud Manager.

Apply your knowledge by trying out what you learned with this hands-on exercise.

## Supporting content 

Prior to trying the hands-on exercise, ensure you're familiar with the following topics, or review the following materials:

+ [Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/cloud-manager.html?lang=en)
+ [aio CLI Cloud Manager plugin](https://github.com/adobe/aem-enablement/tree/master/AEMAsACloudService/11_CloudManager_AIO)

## Hands-on exercise steps
=======
# Adobe Experience Manager Best Practice Analyzer code examples

This project is intended to illustrate example conditions identified by Adobe's Best Practice Analyzer (BPA) and how they can be remediated.

Please not that this Git repository contains a project rife with bad practices and incompatible code and configuration. These violations are used to illustrate a starting condition which can then be juxtaposed against the remediation for specific Best Practice Analyzer codes, broken out by Git branches.

## Legacy branch 

This branch is the starting point generated for Adobe's Maven Project Archetype 10 with several violations intentionally added.

## Best Practice Analyzer code branches

Adobe Best Practice Analyzer reports violations by [code](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html), and each code provides details about what the violation is, and how to resolve it.

For violations this project's `main` Git branch a corresponding Git branch, in the format `code/<bpa code>` contains the changes required for resolve that, and only that, violation.

Performing a Github.com Compare between the `main` and `code/<bpa code>` provides a clear view of the changes required to mitigate the violation.
wknd-legacy

1. Configure your user in the Adobe Admin Console to have have full access to Adobe Cloud Manager.
1. Login to and explore Adobe Cloud manager.
1. Install the aio CLI and Cloud Manager plugin, and configure it for your development Program
1. Push the updated WKND Legacy project code to your Cloud Manager Git repository.
1. Attach a Cloud Manager pipeline to the WKND Legacy code in Cloud Manager Git
1. Trigger a build of the attached Cloud Manager pipeline using the Cloud Manager AIO Plugin. 
1. Validate in both Cloud Manager and with the aio CLI Cloud Manager plugin the Cloud Manager pipeline completed
