# kubernetes_percona_psql
## Installing Percona Postgresql in Kubernetes
### Option 1
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
