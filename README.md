# VerneMQ On Kubernetes

[VerneMQ](https://github.com/erlio/vernemq) cluster with auto-discovery using the unmodified image of vernemq and kubernetes 1.5 new StatefulSets resource

#### Prerequisites
* A running [kubernetes cluster](http://kubernetes.io/gettingstarted/)

#### How to Use
1. Create vernemq namespace
* ``` kubectl create namespace vernemq ```
2. Create the service and statefulset
* ``` kubectl create -f vernemq-ss.yaml ```

#### Checking cluster status
```
kubectl get pods --namespace vernemq
```
```
NAME        READY     STATUS    RESTARTS   AGE
vernemq-0   1/1       Running   0          11h
vernemq-1   1/1       Running   0          11h
vernemq-2   1/1       Running   0          11h
```
```
kubectl exec -it vernemq-0 --namespace vernemq vmq-admin cluster status
```
```
+--------------------+-------+
|        Node        |Running|
+--------------------+-------+
|VerneMQ@100.96.6.84 | true  |
|VerneMQ@100.96.2.180| true  |
|VerneMQ@100.96.5.236| true  |
+--------------------+-------+
```
