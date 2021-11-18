# Hands-on exercise: Dispatcher

> This hands-on exercise builds on [Hands-on exercise: Onboarding](https://github.com/adobe/aem-cloud-engineering-video-series-exercises/tree/session4-cloud-manager)

Now that you understand how the deployment process works for AEM as a Cloud Service using Cloud Manager, let's explore some of the details of how to define Dispatcher configurations and how to validate them.

Apply your knowledge by trying out what you learned with this hands-on exercise.

## Supporting content 

Prior to trying the hands-on exercise, ensure you're familiar with the following topics, or review the following materials:
 
+ [aio CLI Cloud Manager plugin](https://github.com/adobe/aem-enablement/tree/master/AEMAsACloudService/11_CloudManager_AIO)
+ [Repository modernization](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/repository-modernization.html?lang=en)
+ [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/dispatcher.html?lang=en)

## Hands-on exercise steps

1. Transform the WKND Legacy project's AMS Dispatcher configuration using Repository modernization's Dispatcher converter tool. 
    + Configuration is available here: [Default AMS dispatcher configuration](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

2. Validate and deploy the modernized Dispatcher configuration on the AEM SDK's Dispatcher Tools to test. 

### Step 1. Setting up Docker locally

1. Navigate to (Docker Hub)[https://hub.docker.com/signup] and Sign up for a Docker ID
1. Download and Install [Docker for Mac](https://download.docker.com/mac/stable/Docker.dmg) or for [Windows](https://download.docker.com/win/stable/Docker%20Desktop%20Installer.exe)
1. Sign in to your local Docker instance

### Step 2. Setup the Dispatcher SDK Validator

1. Unzip the downloaded `aem-sdk-XXX.zip` file
1. Unpack the Dispatcher Tools into ~/aem-sdk/dispatcher
    > ` Windows `: Unzip aem-sdk-dispatcher-tools-2.0.20-windows.zip into C:\Users\<My User>\aem-sdk\dispatcher (creating missing folders as needed)
    > ` macOS `: Execute the accompanying shell script aem-sdk-dispatcher-tools-2.0.20-unix.sh to unpack the Dispatcher Tools
     > `$ chmod a+x aem-sdk-dispatcher-tools-2.0.20-unix.sh && ./aem-sdk-dispatcher-tools-2.0.20-unix.sh `


### Step 3. Run the Dispatcher SDK Validator

1. Navigate to the ` dispatcher-sdk-x.x.x` folder
1. Run the following commands: <br>
    `For Windows`<br>
    > `bin\validator full -d out src` <br>

    `For Mac`<br>
    > `./bin/validator full -d ./out ./src`

---

> The validation is dual purpose:<br>
>    `Validates the Apache HTTP Web server and Dispatcher configuration files for correctness.`<br>
>    `Transpiles the configurations into a file-set compatible with the Docker container's Apache HTTP Web Server.`

### Step 4. Run the Dispatcher SDK using Docker

> `Once validated, the transpiled configurations are used run Dispatcher locally in the Docker container. It is important to ensure the latest configurations have been validated and output using the validator's -d option.`

1. Start AEM SDK Publish service on Port 4503.
2. Run the following commands: <br>
    `For Windows`<br>
    > `bin\docker_run out host.docker.internal:4503 8080` <br>

    `For Mac`<br>
    > `./bin/docker_run.sh ./out docker.for.mac.localhost:4503 8080`

3. Be sure the Apache Server is started on Port 8080. 
4. In the browser window, navigate to http://localhost:8080
5. Onboard the WKND-legacy project code with the validated Dispatcher using Cloud Manager. Troubleshoot if needed. 
