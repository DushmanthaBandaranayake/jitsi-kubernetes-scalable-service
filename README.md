# jitsi-kubernetes-scalable-service

kubernetes deployment for scalable video bridges

1. Build JVB docker image using [Dockerfile](https://github.com/DushmanthaBandaranayake/jitsi-kubernetes-scalable-service/blob/master/docker/Dockerfile) ``/docker/Dockerfile``

    ``docker build . -t jitsi/jvb:1.0.0``

2. Create kubernetes namespace

   `kubectl create namespace jitsi`

3. Update value for `XMPP_SERVER` & `DOCKER_HOST_ADDRESS` variable in `jvb-statefullset.yaml` file.
then deploy jitsi video bridges as statefullset by executing following command.

   `kubectl apply -f jvb-statefullset.yaml`

4. create kubernetes service to expose jitsi web & jvb UDP ports. This will expose jitsi web on kubernetes nodeport 30443 (make sure this port is available on your cluster, otherwise you have to change this by updating service.yaml).

   `kubectl apply -f service.yaml`

5. deploy jitsi web, jicofo & prosody 

   `kubectl apply -f web-jicofo-prosody.yaml`
---

After executing  above sucessfully,
jitsi web can be accesed via nodeport ``{any ip of a cluster node}:30443``

Eg - `192.168.12.57:30443`