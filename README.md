# Install the OpenShift GitOps operator

To install the OpenShift GitOps operator, run:

```
oc apply -k resources

clusterrolebinding.rbac.authorization.k8s.io/argocd-rbac-ca created
subscription.operators.coreos.com/openshift-gitops-operator created
```

Wait until all resources are running.
```
$ oc get pods -n openshift-gitops
NAME                                                       READY  STATUS   RESTARTS  AGE
cluster-977d46b6d-mf8qs                                    1/1    Running  0         67s
kam-5c87945c98-bkn82                                       1/1    Running  0         67s
openshift-gitops-application-controller-0                  1/1    Running  0         32s
openshift-gitops-applicationset-controller-c5f76984-7gdz4  1/1    Running  0         34s
openshift-gitops-dex-server-857dc8b577-gdd5k               1/1    Running  0         35s
openshift-gitops-redis-87698688c-jqd4b                     1/1    Running  0         65s
openshift-gitops-repo-server-6b8dbb9b5d-wbn7v              1/1    Running  0         37s
openshift-gitops-server-776c8cd579-2gcnk                   1/1    Running  0         36s
openshift-gitops-server-7789547fb5-f8vpw                   0/1    Running  0         37s
```

Check that the Argo CD console is accessible and the pods are in Running status:

```
$ oc get route openshift-gitops-server -n openshift-gitops --template='https://{{.spec.host}}'

https://openshift-gitops-server-openshift-gitops.apps.cluster-57lgk.57lgk.sandbox2634.opentlc.com
```

![image](https://github.com/Everything-is-Code/openshift-gitops/assets/10425803/2b074d59-1c74-49ed-950f-435ece5ed322)

Log in to the Argo CD console with your OpenShift credentials.

![image](https://github.com/Everything-is-Code/openshift-gitops/assets/10425803/8aee4c36-f602-4e53-8822-d4c5fa7f056a)



