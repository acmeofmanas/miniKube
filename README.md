# miniKube

1.**install docker**</br>
_start docker as  a service_</br>
2.**install kubectl**</br>
3.**install minikube**</br>
_start minikube__</br>
4.**minikube start**</br>
```
😄  minikube v1.22.0 on Centos 7.6.1810
✨  Automatically selected the docker driver. Other choices: none, ssh
💨  For improved Docker performance, Upgrade Docker to a newer version (Minimum recommended version is 18.09.0)
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
💾  Downloading Kubernetes v1.21.2 preload ...
    > preloaded-images-k8s-v11-v1...: 502.14 MiB / 502.14 MiB  100.00% 66.72 Mi
    > gcr.io/k8s-minikube/kicbase...: 361.08 MiB / 361.09 MiB  100.00% 35.95 Mi
🔥  Creating docker container (CPUs=2, Memory=64300MB) ...
🐳  Preparing Kubernetes v1.21.2 on Docker 20.10.7 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

** minikubrt dtsrted and downloaded few images and started cluster
> kubectl cluster-info
> kubectl cluster-info dump

```
[kogentix_ops@cdhdn25 ~]$ docker images
REPOSITORY                                TAG                 IMAGE ID            CREATED             SIZE
k8s.gcr.io/kube-apiserver                 v1.21.2             106ff58d4308        2 months ago        126 MB
k8s.gcr.io/kube-scheduler                 v1.21.2             f917b8c8f55b        2 months ago        50.6 MB
k8s.gcr.io/kube-controller-manager        v1.21.2             ae24db9aa2cc        2 months ago        120 MB
k8s.gcr.io/kube-proxy                     v1.21.2             a6ebd1c1ad98        2 months ago        131 MB
gcr.io/k8s-minikube/storage-provisioner   v5                  6e38f40d628d        5 months ago        31.5 MB
k8s.gcr.io/pause                          3.4.1               0f8457a4c2ec        7 months ago        683 kB
kubernetesui/dashboard                    v2.1.0              9a07b5b4bfac        8 months ago        226 MB
k8s.gcr.io/coredns/coredns                v1.8.0              296a6d5035e2        10 months ago       42.5 MB
k8s.gcr.io/etcd                           3.4.13-0            0369cf4303ff        12 months ago       253 MB
kubernetesui/metrics-scraper              v1.0.4              86262685d9ab        17 months ago       36.9 MB
[kogentix_ops@cdhdn25 ~]$ docker ps
CONTAINER ID        IMAGE                    COMMAND                  CREATED             STATUS              PORTS               NAMES
5ff36c9bf1b1        6e38f40d628d             "/storage-provisioner"   24 minutes ago      Up 24 minutes                           k8s_storage-provisioner_storage-provisioner_kube-system_85d03571-7675-49f3-8be1-449ecf5b1610_0
58d66aa79e86        k8s.gcr.io/pause:3.4.1   "/pause"                 24 minutes ago      Up 24 minutes                           k8s_POD_storage-provisioner_kube-system_85d03571-7675-49f3-8be1-449ecf5b1610_0
04f0a98aeead        296a6d5035e2             "/coredns -conf /e..."   24 minutes ago      Up 24 minutes                           k8s_coredns_coredns-558bd4d5db-dvldq_kube-system_fe1f3aca-eb25-4c47-88c6-e375e3f2d73d_0
59350c8ffb8b        a6ebd1c1ad98             "/usr/local/bin/ku..."   24 minutes ago      Up 24 minutes                           k8s_kube-proxy_kube-proxy-6lgj5_kube-system_b9511770-fcf6-4529-a881-9995bf0dc1cd_0
b8102f8b49e9        k8s.gcr.io/pause:3.4.1   "/pause"                 24 minutes ago      Up 24 minutes                           k8s_POD_coredns-558bd4d5db-dvldq_kube-system_fe1f3aca-eb25-4c47-88c6-e375e3f2d73d_0
62c3782a6ab4        k8s.gcr.io/pause:3.4.1   "/pause"                 24 minutes ago      Up 24 minutes                           k8s_POD_kube-proxy-6lgj5_kube-system_b9511770-fcf6-4529-a881-9995bf0dc1cd_0
dbf61b4f126a        f917b8c8f55b             "kube-scheduler --..."   24 minutes ago      Up 24 minutes                           k8s_kube-scheduler_kube-scheduler-minikube_kube-system_a2acd1bccd50fd7790183537181f658e_0
77e3b886a294        106ff58d4308             "kube-apiserver --..."   24 minutes ago      Up 24 minutes                           k8s_kube-apiserver_kube-apiserver-minikube_kube-system_cefbe66f503bf010430ec3521cf31be8_0
17253a344087        0369cf4303ff             "etcd --advertise-..."   24 minutes ago      Up 24 minutes                           k8s_etcd_etcd-minikube_kube-system_be5cbc7ffcadbd4ffc776526843ee514_0
1640df24929c        ae24db9aa2cc             "kube-controller-m..."   24 minutes ago      Up 24 minutes                           k8s_kube-controller-manager_kube-controller-manager-minikube_kube-system_a5754fbaabd2854e0e0cdce8400679ea_0
1b76ce6605cd        k8s.gcr.io/pause:3.4.1   "/pause"                 25 minutes ago      Up 24 minutes                           k8s_POD_kube-apiserver-minikube_kube-system_cefbe66f503bf010430ec3521cf31be8_0
3c655ffdcfeb        k8s.gcr.io/pause:3.4.1   "/pause"                 25 minutes ago      Up 24 minutes                           k8s_POD_etcd-minikube_kube-system_be5cbc7ffcadbd4ffc776526843ee514_0
8e3e6310b22b        k8s.gcr.io/pause:3.4.1   "/pause"                 25 minutes ago      Up 24 minutes                           k8s_POD_kube-scheduler-minikube_kube-system_a2acd1bccd50fd7790183537181f658e_0
112ca6809023        k8s.gcr.io/pause:3.4.1   "/pause"                 25 minutes ago      Up 24 minutes                           k8s_POD_kube-controller-manager-minikube_kube-system_a5754fbaabd2854e0e0cdce8400679ea_0
[kogentix_ops@cdhdn25 ~]$
```
