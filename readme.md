# Github actions CICD based on Spring PetClinic Sample Application
This repository contains an example Github actions CICD workflow which:

- Compiles the PetClinic code
- Runs tests using Maven
- Packages the project as a runnable Docker image
- Publishes the image to JFrog Artifactory in your pipeline

You can examine example runs of this workflow in the [Github actions tab](https://github.com/GShuttleworth/spring-petclinic-cicd/actions) in this Github repository. This allows you to view results of tests and security scans.

The workflow is defined in the `maven-build.yml` file located [here](https://github.com/GShuttleworth/spring-petclinic-cicd/blob/main/.github/workflows/maven-build.yml).

## Pulling Docker Image
To test the Docker image you first must download the image locally: 

> `sudo` may be required to successfully run the following commands.
1.  ```bash
    docker login gshuttleworth.jfrog.io
    ```
2. No password should be required as the Artifactory repository will allow annonymous users.

3.  ```bash
    docker pull gshuttleworth.jfrog.io/gshuttleworth-docker/spring-petclinic-cicd-image:10
    ```
    > Image version tag may need to be updated as new builds are created. 

4. Verify image has been pulled by running:
    ```bash
    docker image list
    ```
## Running Docker Image
To run the docker image:
```bash
docker run -p 8080:8080 gshuttleworth.jfrog.io/gshuttleworth-docker/spring-petclinic-cicd-image:10
```
This will run the PetClinic application locally at [localhost:8080](http://localhost:8080).
