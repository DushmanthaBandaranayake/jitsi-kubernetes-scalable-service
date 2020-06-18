# jitsi-kubernetes-scalable-service

kubernetes deployment for scalable video bridges

`1. build docker image`

``docker build . -t jitsi/jvb:1.0.0``

`2 kubectl create namespace jitsi`

`3. kubectl apply -f jvb-statefullset.yaml`

`4. kubectl apply -f service.yaml`

`5. kubectl apply -f web-jicofo-prosody.yaml`