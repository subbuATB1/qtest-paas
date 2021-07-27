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

<code>mvn clean install -DskipTests -Pminify-js</code><p>
<code>Make sure to run dos2unix.exe docker/qtest/entry.sh  (In windows environment)<code>
<code>docker build . -f ./docker/qtest/Dockerfile -t localhost:5000/qtestmgr && docker push localhost:5000/qtestmgr</code><p>
<code>docker build . -f ./docker/liquibase/Dockerfile -t localhost:5000/liquibase && docker push localhost:5000/liquibase</code>

## Deploy qTest via local Helm
<code>export QCHART="location of your qtest_chart Helm repo"</code><p>
<code>helm install qtest -f values-local.yaml $QCHART/Charts/qtest-chart</code>

## Sanity Tests
<code>./sanity.sh</code>

## Tear down cluster
<code>kind delete cluster</code>

## Add the below to host file
127.0.0.1       nephele.qtest.local
127.0.0.1       qtestdev1.qtest.local
127.0.0.1       nginx.local
127.0.0.1       jira.local
127.0.0.1       scenario.local
127.0.0.1       qtest.local
127.0.0.1       notification.qtest.local