### Create Deployment
``` bash
# kubectl create deployment <YourDepName> --image=<image>
kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1
```
> #### Dsiaplay Deployments
``` bash
kubectl get deployments
```

---

### Access Pods
``` bash
# 1. Start proxy
kubectl proxy

# 2. get pod name
kubectl get pods

# 3. Access a pod
# kubectl exec -it <podName> -- bash
kubectl exec -it kubernetes-bootcamp-9bc58d867-7r62j -- bash

# After accessing, run "ls" to see "server.js" which will reponed to requests
```

---

### Expose (Create Service) 
``` bash
# kubectl expose deployment <depName> --type=NodePort --port=<portNum>
kubectl expose deployment kubernetes-bootcamp --type=NodePort --port=8080

# Display new Service
kubectl get services
```

---

### Send Request to the Server
``` bash
# To get NodePort Number:
# kubectl describe services <depName>
kubectl describe services kubernetes-bootcamp
# curl $(minikube ip):<NodePortNum>
curl $(minikube ip):32000
```

> ![Image](https://github.com/user-attachments/assets/3c9227b8-8a9d-4df0-936e-f1a06f672c67)

---

### Scale Deployments
``` bash
# kubectl scale deployments <depName> --replicas=<Num>
kubectl scale deployments kubernetes-bootcamp --replicas=3
```

> ![Image](https://github.com/user-attachments/assets/5107bf70-25b9-4707-b639-f23167536215)

---

### Update image
``` bash
kubectl set image deployment/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2
```

> ![Image](https://github.com/user-attachments/assets/ce6ffda8-50af-4c0e-9e3e-bb7a6f7a5613)

---

### Open Kubernetes Dashboard
``` bash
minikube dashboard
```

> ![Image](https://github.com/user-attachments/assets/2b2f4324-bfc4-44f9-82b6-14d4aa720dbc)
 
---

### Remove Deployments & Services
``` bash
kubectl delete deployments --all
kubectl delete services --all
```

---

### To do this using configuation file
``` bash 
# Run the yaml file
kubectl apply -f k8s.yaml
```

> ![Image](https://github.com/user-attachments/assets/a487b5bc-2ece-407e-b99a-5bbec53c2e56)