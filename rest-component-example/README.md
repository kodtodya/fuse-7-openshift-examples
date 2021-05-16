# Spring-Boot Camel QuickStart [rest-dsl-servlet-component]

This example demonstrates how you can use Apache Camel, Spring Boot along for writing rest service.

### Building

The example can be built with

    mvn clean package -DskipTests

    OR

    mvn clean package


## Deploy to openshift-4.x


    mvn oc:resource oc:deploy


## Check Hawtio

All the resource utilization can be monitored using Hawtio:

http://localhost:8080/actuator/hawtio

If you have changed config in properties file for Hawtio, all the resource utilization can be monitored using Hawtio:

http://localhost:8080/hawtio


### Check Web-service

If you are running in local, please invoke: 

    http://localhost:8080/checkprime/11

if you are on openshfit, test it using below url:

    http://rest-component-example-test-123.apps-crc.testing/checkprime/11

if you pod fails to start in first attempt, pls use below config in `rest-component-example-deploymentconfig.yml` or simply copy-paste `rest-component-example-deploymentconfig.yml` file from resources in target:
```
livenessProbe:
    tcpSocket:
        port: 80
    initialDelaySeconds: 5
    periodSeconds: 5
readinessProbe:
    httpGet:
        path: /
        port: 80
    initialDelaySeconds: 5
    periodSeconds: 3
```