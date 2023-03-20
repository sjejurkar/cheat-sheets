# Kuberenetes Cheat Sheet

## Commands to get information about supported features

### get list of resources the cluster supports
```
kubectl api-resources
```

### get list of api versions the cluster supports
```
kubectl api-versions
```

### get all the keys each **kind** supports (e.g. name **_services_** means get keys for kind **_Service_**)
```
kubectl explain services --recursive
```

### get sub-keys for key **_spec_** in **_Service_** kind (drill down into YAML file)
```
kubectl explain services.spec
```

### get sub-keys for sub-key **_type_** of key **_spec_** in **_Service_** kind (drill down into YAML file)
```
kubectl explain services.spec.type
```

## Operational commands for you cluster
### get all resources
```
kubectl get all
```

### apply
```
kubectl apply -f <filename>
```

### describe pod
```
kubectl describe pod <podname> -o wide
```

### describe service
```
kubectl describe svc <servicename> -o wide
```

### get all pods
```
kubectl get po
```

### get all pods and their labels
```
kubectl get po --show-labels
```

### deployments
```
sudo kubectl get deployments
sudo kubectl describe deployment <deployment-name>
sudo kubectl rollout history deployment <deployment-name>
sudo kubectl rollout restart deployment/<deployment-name>
sudo kubectl rollout status -w deployment/<deployment-name>
```

### List the environment variables defined on all pods
```
kubectl set env pods --all --list
```

### push/inject environment variables to pod (will restart pod)
```
kubectl set env deployment/<deployment-name> VAR_ONE=value1 VAR_TWO=value2
```

### connect to PostgreSQL database on Kubernetes pod
### get IP address of the Pod
```
kubectl get pods -o wide
```

### connect to Postgres
```
psql -h <ip-address>  -U postgres --password
```
### run SQL script in Postgres
```
psql -h <ip-address>  -U postgres --password -f <sql-script-name>
```

#### NOTE: install psql if it is not available 
```
sudo apt install postgresql-client-common
sudo apt-get install postgresql-client
```