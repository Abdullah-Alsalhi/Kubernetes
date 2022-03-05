# kubernetes

### ***creating pod using imperative command***

```bash

kubectl run webapp \
--image=amigoscode/kubernetes:hello-world \
--port=80

```

### ***port-forwading***
```bash

kubectl port-forward pod/hello-world 8080:80

```

### ***exec into container ***

->>> In case there is only one container inside the pod;

```bash

kubectl exec -it hello-world -- bash

```

->>> In case there are many containers inside the pod;

```bash

kubectl exec -it hello-world -c hello-world -- /bin/bash

```

->>> In case you don't want to interact with the container ;

```bash

kubectl exec hello-world -- ps aux

# Notice that ps aux is a command to show the process are running inside the container;

```

### ***List all the resources***

```bash

kubectl api-resources

```


### ***When you rolling update a new version add this annotation for knowledge***

```yaml

annotations: 
  kubernetes.io/change-cause: "change to amigoscode/kubernetes:hello-world"

```

# Notice

***When you rolled update the previous replicaset remains as it is***

```bash

kubectl get rs

```

### ***To rollback you can use the replicaset for this purpose***

```bash

$ kubectl rollout history deployment hello-world
$ kubectl rollout undo deployment hello-world --to-revision=1

```
### ***To see information about specifice version***

```bash

kubectl rollout history deployment hello-world --revision=2

```
