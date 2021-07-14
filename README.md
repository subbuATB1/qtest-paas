# K8s cluster in a box!

This is a quickstart to deploy qTest on your local dev K8s multi-node cluster.

## Prerequisites

* PostgreSQL (local)
* Docker Desktop
* Git Bash (or WSL2)
* kubectl 
* Helm
* Kind

## Clone this repo
<code>git clone git@github.com:QAS-Labs/qtest-paas</code>

## Set up cluster
<code>./kindup.sh</code>

## Build qTest and Liquibase
Please refer to qTest build instructions; but, in a nutshell:

<code>mvn clean install -DskipTests && \
docker build . -f ./docker/qtest/Dockerfile -t localhost:5000/qtestmgr && docker push localhost:5000/qtestmgr \
docker build . -f ./docker/liquibase/Dockerfile -t localhost:5000/liquibase && docker push localhost:5000/liquibase
</code>

## Deploy qTest via Helm
<code>
</code>

## Sanity Tests
<code>./sanity.sh</code>

## Tear down cluster
<code>kind delete cluster</code>