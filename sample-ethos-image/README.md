# Sample Ethos image

This repository contains a Maven project that can be used for building a Docker image set, which can be deployed on Ethos, eg. with the [aem-k8-base](https://git.corp.adobe.com/Granite/aem-k8-base/blob/master/docs/custom-provisioning-model.md).

## Setting a custom name for the images

The name of the image can be set in the `<properties>` section of the [pom.xml](pom.xml) file - it's the `${docker.image.name}` property. Since multiple images will be build (one for the author and one for the publish), the name should depend on the `${content_mode}` property.

## Configuring the application

The application can be defined in the feature file [application-model.json](src/main/features/application.json). If some Linux scripts should be executed before starting the instance, they should be added to the [docker_entrypoint.d](src/main/docker/container/root/docker_entrypoint.d) directory. Any other customizations can be done in the [Dockerfile](Dockerfile).

## Building the image

The images can be build with command:

```
mvn clean package -Dcontent_mode=author-samplecontent
mvn clean package -Dcontent_mode=publish-samplecontent
```

### Docker requirements

In order to build the images we recommend following minimal settings:
* CPUs: **2**
* Memory: **7.0 GiB**

## Deploying the image

They can be also deployed to the remote repository with:

```
mvn clean deploy -Dcontent_mode=author-samplecontent
mvn clean deploy -Dcontent_mode=publish-samplecontent
```

### Logging in

Deploying images requires logging it to the docker2-granite-release-local.dr-uw2.adobeitc.com registry. The password can be found in the profile section of https://artifactory-uw2.adobeitc.com/ - it's available as API key:

```
docker login https://docker2-granite-release-local.dr-uw2.adobeitc.com -u LDAP_NAME
```
