# OpenShift s2i Docker Image Java Applications

An OpenShift source to image Docker Image builder for Java applications.

## How to use the image

### Create a new build

Create a build configuration for the Dockerfile and an image stream in OpenShift as follows:

```bash
# clone the repository
git clone https://github.com/gatblau/ocp_s2i_java.git

# create a build configuration
oc new-build https://github.com/gatblau/ocp_s2i_java.git --name=java --to=java --strategy=docker -n myproject

# check the build progress
oc logs -f bc/java

```

### Build a Java application

```bash
# create a binary build from the 'java' image stream 
oc new-build  -i java --binary=true --to=my_app --strategy=source

# start the build using the application jar file
oc start-build my_app --from-file=./target/my_app-0.0.1-SNAPSHOT.jar --follow
```

