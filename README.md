# kubernetes_percona_psql
## Installing Percona Postgresql in Kubernetes
### Option 1
Login to docker hub
```sh
$ docker login
```
Build docker image from https://github.com/tixsalvador/patroni/tree/master/kubernetes
```sh
$ git clone https://github.com/tixsalvador/patroni.git
$ cd patroni/kubernetes
$ docker build -t patroni .
$ docker tag patroni:<version> <docker_hub_user>/<image_name>
$ docker push <docker_hub_user>/<image_name>
```
