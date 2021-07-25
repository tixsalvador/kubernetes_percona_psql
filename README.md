# kubernetes_percona_psql
## Installing Percona Postgresql in Kubernetes
### Option 1 - Using manifest file
Login to docker hub
```sh
$ docker login
```
Build docker image from https://github.com/tixsalvador/kubernetes_percona_psql/tree/main/patroni_image
```sh
$ git clone https://github.com/tixsalvador/kubernetes_percona_psql.git
$ docker build -t patroni patroni_image/.
$ docker tag patroni:<version> <docker_hub_user>/<image_name>
$ docker push <docker_hub_user>/<image_name>
```
Create PVC for statefuleset replicas
```sh
$ kubectl -f patroni_pvc.yaml
```
Once pvc's are created and patroni image has been uploaded to https://hub.docker.com deploy kubernetes manifest
```sh
$ kubectl create -f patroni_k8s.yaml
Added lines below for VolumeClaimTemplate use for dynamic nfs
---
volumeClaimTemplates:
- metadata:
    name: pgdata
  spec:
    accessModes: [ "ReadWriteOnce" ]
    resources:
      requests:
        storage: 1Gi
---
```
### Option 2 - Using Spilo
Build docker image and upload it to dockerhub
```sh
$ git clone https://github.com/tixsalvador/spilo.git
$ docker build -t <spilo> postgres-appliance/.
$ docker tag <spilo> tixsalvador/<spilo>
$ docker login
$ docker push tixsalvador/<spilo>
```
Optional: Build docker image and upload it to quay.io
```sh
$ git clone https://github.com/tixsalvador/spilo.git
$ docker build -t <spilo> postgres-appliance/.
$ docker tag <spilo> quay.io/tixsalvador/<spilo>
$ docker login quay.io
$ docker push quay.io/tixsalvador/<spilo>

```
Build spilo
```sh
$ kubectl create -f patroni_spilo.yaml
```

