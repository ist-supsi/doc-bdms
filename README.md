# Swissforages 

Swissforages, the Borehole Data Management System (bdms).

## Installation with docker

All the necessary swissforages docker images are published on [Docker Hub](https://hub.docker.com/search?q=swisstopo%2Fservice-bdms&type=image).

To install the latest version of swissforages, you can use the following docker-compose file:

```yaml
version: '3'

services:

    swissforages-service-nginx:
        image: swisstopo/service-bdms-nginx:1.0.4
        depends_on:
            - swissforages-service-bdms
        container_name: swissforages-service-nginx
        ports:
            - 80:80
        restart: always

    swissforages-service-minio:
        image: minio/minio:RELEASE.2021-12-09T06-19-41Z
        container_name: swissforages-service-minio
        restart: always
        environment:
            MINIO_ROOT_USER: EXAMPLE
            MINIO_ROOT_PASSWORD: EXAMPLEKEY
        volumes:
            - ${PWD}/data/minio:/data
        command:
            server /data -console-address ":9002"

    swissforages-service-db:
        image: swisstopo/service-bdms:1.0.4-db
        container_name: swissforages-service-db
        restart: always
        volumes:
            ${PWD}/data/db:/var/lib/postgresql/data

    swissforages-service-bdms:
        image: swisstopo/service-bdms:1.0.4
        depends_on:
            - swissforages-service-db
        container_name: swissforages-service-bdms
        restart: always
        environment:
            FILE_STORAGE: s3
            S3_ENDPOINT: swissforages-service-minio:9000
            S3_SECURE: 0
            S3_BUCKET: swissforages
            S3_CREDENTIALS_ACCESS_KEY: EXAMPLE
            S3_CREDENTIALS_SECRET_KEY: EXAMPLEKEY
```

Save the docker-compose file in the current directory and run the following command to start the swissforages service:

```bash
docker-compose up -d
```
