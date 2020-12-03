docker images for Jenkins
=========================

Based on https://hub.docker.com/r/jenkins/jenkins

1. add docker binary (for docked in docker)
2. add docker-credential-ecr-login


# Build

1. The repo will be built automaticlly with github action on `master` branch or tag match `v*` pattern.

2. The generated docker image will be push to docker hub `fahm/jenkins-build-dep`.

3. Make sure the github variable DOCKER_USERNAME and DOCKER_PASSWORD have access to https://hub.docker.com/u/fahm/

# Upgrade Jenkins

1. Modify `Dockerfile` to reference a new base jenkins image e.g. `jenkins/jenkins:2.263.1-lts-alpine`

2. Commit and push back to `master` branch

# Deploy

1. Login to Jenkins server (nonprod or prod) as root user

2. stop the Jenkins instance

```
# cd /root
# docker-compose down
```

3. pull the latest fahm/jenkins-build-dep

```
# docker pull fahm/jenkins-build-dep
```

4. start the Jenkins instance

```
# cd /root
# docker-compose up -d
```
