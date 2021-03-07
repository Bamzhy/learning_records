### an example
```
// One yaml file, represent an API Object
apiVersion: apps/v1
// the type of the API Object : Deployment
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: nginx
  name: nginx-deployment
spec:
  replicas: 2
  // Deployment will manage the pods, spec.selector.matchLabels
  selector:
    matchLabels:
      app: nginx
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: nginx
    spec:
      // this pod can tolerate all "foo-bar" taint
      tolerations:
      - key: "foo"
        operator: "Equal"
        value: "bar"
        effect: "NoSchedule"
      containers:
      - image: nginx:1.7.9
        name: nginx
        resources: {}
status: {}
```

### how to get an example yaml file
- kubectl create deployment my-dep --image=nginx:1.7.9 -o yaml --dry-run > abc.yaml

### check status
- kubectl get pods -l app=nginx
- kubectl get deployment -l app=nginx
- 