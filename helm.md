```
[kogentix_ops@cdhdn25 ~]$ curl https://raw.githubusercontent.com/helm/helm/master/scripts/get | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  6639  100  6639    0     0   324k      0 --:--:-- --:--:-- --:--:--  324k
Downloading https://get.helm.sh/helm-v2.17.0-linux-amd64.tar.gz
Preparing to install helm and tiller into /usr/local/bin
helm installed into /usr/local/bin/helm
tiller installed into /usr/local/bin/tiller
Run 'helm init' to configure helm.
[kogentix_ops@cdhdn25 ~]$ ls -ltrh
total 112M
drwxrwxr-x 3 kogentix_ops kogentix_ops 4.0K Apr  5  2019 firminiq
drwxr-xr-x 3 kogentix_ops kogentix_ops 4.0K Apr  5  2019 tls
-rw-rw-r-- 1 kogentix_ops kogentix_ops 1.9K Mar 21  2020 24
-rw-rw-r-- 1 kogentix_ops kogentix_ops  45M Aug 31 08:52 kubectl
-rw-rw-r-- 1 kogentix_ops kogentix_ops  67M Aug 31 09:26 minikube-linux-amd64
-rw-rw-r-- 1 kogentix_ops kogentix_ops  474 Sep  1 09:27 loadbalancer-example.yaml
-rw-rw-r-- 1 kogentix_ops kogentix_ops 198K Sep  3 07:17 logs.out
[kogentix_ops@cdhdn25 ~]$ hel
helm  help
[kogentix_ops@cdhdn25 ~]$ helm init
Creating /home/kogentix_ops/.helm
Creating /home/kogentix_ops/.helm/repository
Creating /home/kogentix_ops/.helm/repository/cache
Creating /home/kogentix_ops/.helm/repository/local
Creating /home/kogentix_ops/.helm/plugins
Creating /home/kogentix_ops/.helm/starters
Creating /home/kogentix_ops/.helm/cache/archive
Creating /home/kogentix_ops/.helm/repository/repositories.yaml
Adding stable repo with URL: https://charts.helm.sh/stable
Adding local repo with URL: http://127.0.0.1:8879/charts
$HELM_HOME has been configured at /home/kogentix_ops/.helm.

Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.

Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.
To prevent this, run `helm init` with the --tiller-tls-verify flag.
For more information on securing your installation see: https://v2.helm.sh/docs/securing_installation/
[kogentix_ops@cdhdn25 ~]$
[kogentix_ops@cdhdn25 ~]$ helm version
Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}
Server: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}
[kogentix_ops@cdhdn25 ~]$ kubectl --help |less
[kogentix_ops@cdhdn25 ~]$ kubectl -n kube-system get pod
NAME                               READY   STATUS    RESTARTS   AGE
coredns-558bd4d5db-f4kfk           1/1     Running   2          2d20h
etcd-minikube                      1/1     Running   2          2d20h
kube-apiserver-minikube            1/1     Running   2          2d20h
kube-controller-manager-minikube   1/1     Running   2          2d20h
kube-proxy-qvnk2                   1/1     Running   2          2d20h
kube-scheduler-minikube            1/1     Running   2          2d20h
storage-provisioner                1/1     Running   5          2d20h
tiller-deploy-7b9cbd46c9-9kkwj     1/1     Running   0          2m48s
[kogentix_ops@cdhdn25 ~]$ kubectl get pod
No resources found in default namespace.
[kogentix_ops@cdhdn25 ~]$
[kogentix_ops@cdhdn25 ~]$ helm repo add pingcap https://charts.pingcap.org/
"pingcap" has been added to your repositories
[kogentix_ops@cdhdn25 ~]$ helm repo list
NAME    URL
stable  https://charts.helm.sh/stable
local   http://127.0.0.1:8879/charts
pingcap https://charts.pingcap.org/
[kogentix_ops@cdhdn25 ~]$

[kogentix_ops@cdhdn25 ~]$ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Skip local chart repository
...Successfully got an update from the "pingcap" chart repository
...Successfully got an update from the "stable" chart repository
Update Complete.
[kogentix_ops@cdhdn25 ~]$ helm search tidb-cluster -l
NAME                    CHART VERSION   APP VERSION     DESCRIPTION
pingcap/tidb-cluster    v1.2.2                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.2.1                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.2.0                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.13                         A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.12                         A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.11                         A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.10                         A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.9                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.8                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.7                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.6                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.5                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.4                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.3                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.2                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.1                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.1.0                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.0.7                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.0.6                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.0.5                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.0.4                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.0.3                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.0.2                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.0.1                          A Helm chart for TiDB Cluster
pingcap/tidb-cluster    v1.0.0                          A Helm chart for TiDB Cluster
[kogentix_ops@cdhdn25 ~]$ helm search tidb-operator -l
NAME                    CHART VERSION   APP VERSION     DESCRIPTION
pingcap/tidb-operator   v1.2.2          v1.2.2          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.2.1          v1.2.1          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.2.0          v1.2.0          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.13         v1.1.13         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.12         v1.1.12         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.11         v1.1.11         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.10         v1.1.10         tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.9          v1.1.9          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.8          v1.1.8          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.7          v1.1.7          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.6          v1.1.6          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.5          v1.1.5          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.4          v1.1.4          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.3                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.2                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.1                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.1.0                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.7                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.6                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.5                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.4                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.3                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.2                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.1                          tidb-operator Helm chart for Kubernetes
pingcap/tidb-operator   v1.0.0                          tidb-operator Helm chart for Kubernetes
[kogentix_ops@cdhdn25 ~]$
