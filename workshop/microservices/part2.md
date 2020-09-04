# Part 2

2. Update YAML deployment manifests to point at correct images - five files.

3. Run database schema job.
```
    cd data_model
    oc apply -f job.yaml
```

Output: 
```
theia@theiadocker-koyfman1:/home/project/example-bank/data_model$ oc get pods
NAME                                   READY   STATUS              RESTARTS   AGE
cc-schema-load-9tz6f                   0/1     ContainerCreating   0          5s
creditdb-77c6b6785d-vnxtv              1/1     Running             1          98m
postgresql-operator-58cb79c899-69qpn   1/1     Running             0          98m
theia@theiadocker-koyfman1:/home/project/example-bank/data_model$ oc get pods
NAME                                   READY   STATUS      RESTARTS   AGE
cc-schema-load-9tz6f                   0/1     Completed   0          42s
creditdb-77c6b6785d-vnxtv              1/1     Running     1          99m
postgresql-operator-58cb79c899-69qpn   1/1     Running     0          99m
theia@theiadocker-koyfman1:/home/project/example-bank/data_model$ oc logs cc-schema-load-9tz6f
CREATE EXTENSION
CREATE DATABASE
You are now connected to database "example" as user "postgres".
CREATE SCHEMA
SET
CREATE TABLE
CREATE TABLE
CREATE TABLE
CREATE TABLE
```
```
 oc apply -f deployment.yaml -f bank-app-backend/user-service/deployment.yaml -f bank-app-backend/transaction-service/deployment.yaml 
```

Find route to access simulator:

```
theia@theiadocker-koyfman1:/home/project/example-bank$ oc get routes
NAME                       HOST/PORT                                                                                                                          PATH   SERVICES                   PORT    TERMINATION   WILDCARD
mobile-simulator-service   mobile-simulator-service-example-bank.koyfman-os44-aug5-f2c6cdc6801be85fd188b09d006f13e3-0000.us-east.containers.appdomain.cloud 
```

## Summary

