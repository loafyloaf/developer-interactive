# Deploying to OpenShift

## Verify deployment file

Open **deployment.yaml** file in the root folder

```yaml
containers:
  - image: <YOUR_DOCKER_HUB>/workshop-mobile-simulator:1.0
```

## Deploy to OpenShift

```bash
$ oc apply -f deployment.yaml
```

## Check status

```bash
$ oc get pods

NAME                                           READY   STATUS    RESTARTS   AGE
mobile-simulator-deployment-5b7bb5f56f-qvrj7   1/1     Running   0          15s
```