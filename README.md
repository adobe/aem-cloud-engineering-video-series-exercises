# Cloud Acceleration Bootcamp - Session 5: Dispatcher

## Pre-Work

1). Onboard the project code to AEM as a Cloud Service.

2). Trigger a pipeline execution using the CM AIO plugin.

3). Install the Dispatcher SDK on your local machine.

4). Be sure Docker installed on your system.

5). Install the aio-cli-plugin-aem-cloud-service-migration plugin.


## Bootcamp: Topics covered in Session 5: Dispatcher

### Notable Changes to the Dispatcher in AEM as a Cloud Service

This section will cover the changes in the Cloud Service Dispatcher, and tips and tricks for making the transition smoother. 

### How the Dispatcher Converter tool works

This section will cover the why of the Dispatcher tool, and how to use it. 

### Transforming a legacy Dispatcher configuration using the tool

This session will demo how to use the Dispatcher tool to convert a stock AMS Dispatcher configuration to Cloud Service. 

### Test the Dispatcher Configuration using the Dispatcher SDK 

This section will show how to test your Dispatcher configuration using the Dispatcher SDK.

### Deploy the Dispatcher Configuration on a Cloud Service sandbox

This session will demo how to deploy the Dispatcher configuration on a sandbox.

### Troubleshooting Tips & Tricks

This session will feature a consultant who can talk about some real world Dispatcher migration tactics. 


# Cloud Acceleration Bootcamp - Session 5 Homework

1). Transform the legacy AMS Dispatcher configuration using the Dispatcher tool. Configuration is available here: [Default AMS dispatcher configuration](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

2). Deploy this configuration on the Dispatcher SDK to test. 

### Step 1. Setting up Docker locally

1. Navigate to (Docker Hub)[https://hub.docker.com/signup] and Sign up for a Docker ID
2. Download and Install [Docker for Mac](https://download.docker.com/mac/stable/Docker.dmg) or for [Windows](https://download.docker.com/win/stable/Docker%20Desktop%20Installer.exe)
3. Sign in to your Local Docker Instance.

### Step 2. Setup the Dispatcher SDK Validator

1. Unzip the downloaded aem-sdk-XXX.zip file
2. Unpack the Dispatcher Tools into ~/aem-sdk/dispatcher
    > ` Windows `: Unzip aem-sdk-dispatcher-tools-2.0.20-windows.zip into C:\Users\<My User>\aem-sdk\dispatcher (creating missing folders as needed) <br><br>

    > ` macOS `: Execute the accompanying shell script aem-sdk-dispatcher-tools-2.0.20-unix.sh to unpack the Dispatcher Tools
    
     > ``` chmod a+x aem-sdk-dispatcher-tools-2.0.20-unix.sh && ./aem-sdk-dispatcher-tools-2.0.20-unix.sh ```


### Step 3. Run the Dispatcher SDK Validator
1. Navigate to the ` dispatcher-sdk-2.0.20 ` folder
2. Run the following commands: <br>
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


1. Start AEM Publish server on Port 4503.
2. Run the following commands: <br>
`For Windows`<br>
    > `bin\docker_run out host.docker.internal:4503 8080` <br>

    `For Mac`<br>
    > `./bin/docker_run.sh ./out docker.for.mac.localhost:4503 8080`

3. Be sure the Apache Server is started on Port 8080. 

4. In the browser window, navigate to http://localhost:8080
    
5. Onboard the WKND-legacy project code with the validated Dispatcher using Cloud Manager. Troubleshoot if needed. 








