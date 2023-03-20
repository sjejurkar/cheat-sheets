# Kuberenetes Cheat Sheet

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
sudo kubectl describe deployment inteligen-deployment
sudo kubectl rollout history deployment inteligen-deployment
sudo kubectl rollout restart deployment/inteligen-deployment
sudo kubectl rollout status -w deployment/inteligen-deployment
```

### List the environment variables defined on all pods
```
kubectl set env pods --all --list
```

### push/inject environment variables to pod (will restart pod)
```
kubectl set env deployment/user-mgmt DEMO_MODE=0 UM_EXPIRY=2022-12-31
```

### connect to PostgreSQL database on Kubernetes pod
### get IP address of the Pod
```
kubectl get pods -o wide
```

### connect to Postgres
```
psql -h 192.168.227.140  -U postgres --password
```
### run SQL script in Postgres
```
psql -h 192.168.227.140  -U postgres --password -f ./alien_vault_pulse.sql 
```

#### NOTE: install psql if it is not available 
```
sudo apt install postgresql-client-common
sudo apt-get install postgresql-client
```