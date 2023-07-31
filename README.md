These contents help you make and push easily the components for CloudHub to the docker hub repo.

# How to use
Refer to the following examples(easy to use).
```
cd cloudhub
docker build -t snetsystems/cloudhub:1.4.5 --build-arg VERSION=1.4.5 --build-arg COMMIT=3c27290 --build-arg ARCH=amd64 .
docker login
docker push snetsystems/cloudhub:1.4.5
```
```
cd telegraf
docker build -t snetsystems/telegraf:1.23.4-snet-2 --build-arg VERSION=1.23.4-snet-2 .
docker login
docker push snetsystems/telegraf:1.23.4-snet-2
```
