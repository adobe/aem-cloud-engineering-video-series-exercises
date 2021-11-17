# Hands-on exercise: Introduction and Thinking Differently 

Now that you understand what AEM as a Cloud Service is, how it's different from AEM 6.x, and why its important to ensure your application aligns with AEM as a Cloud Services best practices prior to deployment, try running the Best Practice Analyzer (BPA) against the WKND Legacy project (that contains example violations) and review the BPA report.

Apply your knowledge by trying out what you learned with this hands-on exercise.

## Supporting content 

Prior to trying the hands-on exercise, ensure you're familiar with the following topics, or review the following materials:

+ [What is AEM as a Cloud Service?](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/introduction/what-is-aem-as-a-cloud-service.html?lang=en)
+ [Architecture of AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/introduction/architecture.html?lang=en)
+ [Thinking Differently](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/introduction.html?lang=en)
+ [Mutable and immutable content](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/basics/mutable-immutable.html?lang=en)
+ [Differences in developing for AEM as a Cloud Service and AEM 6.x](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#developing)
+ [Best Practices Analyzer and Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/bpa-and-cam.html?lang=en)

## Hands-on exercise steps

1. Set up a local AEM 6.4 environment on which the WKND legacy app will be installed, including Java 8 and Maven.
    + [AEM 6.x local development set up](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
    + [Download AEM 6.4](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).
2. Clone the legacy Customer Code Repository available in the `wknd-legacy` branch of [this Git repository](https://github.com/adobe/aem-cloud-engineering-video-series-exercises).
3. Install the legacy WKND legacy app to your local AEM 6.4 environment using Maven.
4. [Download and install the BPA](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=Best*+Practices*+Analyzer*&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=1) using Package Manager. Run the BPA on the WKND Legacy Site using AEM 6.4 [Download BPA](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). 
5. Examine the BPA report in your local AEM 6.4
6. Review this video to understand package structure [AEM project package structure](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/basics/repository-structure-package.html?lang=en#developing). 
