```
[kogentix_ops@cdhdn25 tidb-operator]$ helm install pingcap/tidb-operator --name tidb-operator --namespace tidb-admin --version=v1.2.2
NAME:   tidb-operator
LAST DEPLOYED: Fri Sep  3 08:01:02 2021
NAMESPACE: tidb-admin
STATUS: DEPLOYED

RESOURCES:
==> v1/ClusterRole
NAME                                   CREATED AT
tidb-operator:tidb-controller-manager  2021-09-03T13:01:06Z
tidb-operator:tidb-scheduler           2021-09-03T13:01:06Z

==> v1/ClusterRoleBinding
NAME                                   ROLE                                               AGE
tidb-operator:kube-scheduler           ClusterRole/system:kube-scheduler                  0s
tidb-operator:tidb-controller-manager  ClusterRole/tidb-operator:tidb-controller-manager  0s
tidb-operator:tidb-scheduler           ClusterRole/tidb-operator:tidb-scheduler           0s
tidb-operator:volume-scheduler         ClusterRole/system:volume-scheduler                0s

==> v1/ConfigMap
NAME                   DATA  AGE
tidb-scheduler-policy  1     1s

==> v1/Deployment
NAME                     READY  UP-TO-DATE  AVAILABLE  AGE
tidb-controller-manager  0/1    1           0          0s
tidb-scheduler           0/1    1           0          0s

==> v1/Pod(related)
NAME                                      READY  STATUS             RESTARTS  AGE
tidb-controller-manager-796b4cc89f-2c6vm  0/1    ContainerCreating  0         0s
tidb-scheduler-7fd6976f95-p6d7v           0/2    ContainerCreating  0         0s

==> v1/ServiceAccount
NAME                     SECRETS  AGE
tidb-controller-manager  1        0s
tidb-scheduler           1        0s


NOTES:
Make sure tidb-operator components are running:

    kubectl get pods --namespace tidb-admin -l app.kubernetes.io/instance=tidb-operator

[kogentix_ops@cdhdn25 tidb-operator]$
