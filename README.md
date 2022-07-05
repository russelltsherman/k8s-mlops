# k8s-mlops

create kind cluster
`make cluster`

verify olm pods started
`watch kubectl get pods -n olm`

```sh
NAME                               READY   STATUS    RESTARTS   AGE
catalog-operator-b6545d6c9-bbl5f   1/1     Running   0          90m
olm-operator-6b86d4548-tm8hh       1/1     Running   0          90m
operatorhubio-catalog-8cgzv        1/1     Running   0          84m
packageserver-5c779b46fd-xzbkn     1/1     Running   0          84m
packageserver-5c779b46fd-z7kj4     1/1     Running   0          84m
```

verify that catalogsource is available
`kubectl get catalogsource -n olm`

```sh
NAMESPACE   NAME                    DISPLAY               TYPE   PUBLISHER        AGE
olm         operatorhubio-catalog   Community Operators   grpc   OperatorHub.io   90m
```
