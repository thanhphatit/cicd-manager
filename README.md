# CICD MANAGER

This is tools created by bash shell to support for DevOps Engineer

NOTE:

    [+] Your machine need have bash and OS linux (Ubuntu is good)
    [+] The tools run only on x86-64
    [+] The tools must be placed in the git repository with located in the root folder

## SHORTENED NAME ENVIRONMENTS

| Environment | Shortened |
| --- | --- |
| Development | dev | 
| Staging | stg |
| User Acceptance Testing | uat |
| Production | prd|
| Disaster Recovery | drc |

## PATH

> environments/{env}/{provider}/{identifier}

## FILE INFO DATA

> `metadata.conf`

```
service_provider: ***
service_type: ***
service_identifier: ***
service_environment: ***
```

## VERSION

- Use character dash `.` between words, not using character underscore `-` between words.

```
0.0.1 => VALID
```

```
0-0-1 => NOT VALID
```

### DOCKER

#### Path

Usually a company will only need a Hub Registry containing images, so we will put the company name after the environment folder

> environments/itblognote/aws/itblognote-ecr/metadata.conf

#### Setting file `metadata.conf`

| NAME | DOCKER | DIGITAL OCEAN | AZURE | AWS | GOOGLE CLOUD |
| --- | --- | --- | --- | --- | --- |
| service_provider | docker | doc | azure | aws | gcp |
| service_type | docker | dcr | acr | ecr | gcr |

### Path

*  environments/<company-name>/<cloud>/<name-service>

- Example: environments/itblognote/azure/itblognote-images-acr/images

With Docker we will have folder images to easy control with helm

File `info.conf` support tools

```
name: apache2-alpine
tag: 0.0.1
```

Name >: Dockerfile
### Metadata.conf

Example:

```
service_provider: azure
service_type: acr
service_identifier: itblognote-images-acr
service_environment: itblognote
```

### Delete mode

`delete.lock` Delete all docker images
`delete.lock.tag` Delete with images and tag

## Helm

### Shortened Name

| Name | chartmuseum | azure | aws |
| --- | --- | --- | --- |
| service_provider | chartmuseum | azure | aws |
| service_type | http | acr | s3 |

### Path

*  environments/<company-name>/<cloud>/<name-service>

service_provider: <chartmuseum>/<azure>/<aws>
service_type: <http>/<acr>/<s3>
service_identifier: <docker-registry-name>/<acr-name>/<s3-bucket-name>
service_environment: <company-name>

- Example: environments/dev/aws/s3-bucket/charts
- Example: environments/itblognote/azure/itblognote-images-acr/charts

With Helm we will have folder charts to easy control with docker

### Metadata.conf

Example:

```
service_provider: aws
service_type: s3
service_identifier: itblognote-s3
service_environment: itblognote
```

## Helm Release

- Use character dash `-` between words, not using character underscore `_` between words.

```
aia-app-abc => VALID
```

```
aia_app_abc => NOT VALID
```

## Kubernetes

### Shortened Name

| Name | docker | azure | aws | digital ocean | google cloud |
| --- | --- | --- | --- | --- | --- |
| service_provider | docker | azure | aws | doc | gcp |
| service_type | docker | acr | ecr | doks | gcr |

service_identifier = context cluster


## Config

### Shortened Name

| Name | azure | aws | digital ocean |
| --- | --- | --- | --- | --- |
| service_provider | azure | aws | doc |
| service_type | aks, fa | eks | doks |
| service_identifier | name cluster, resource group |

Name folder = release name
## Version