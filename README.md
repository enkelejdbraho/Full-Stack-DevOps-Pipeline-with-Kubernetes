DOCKER

Create a file named Dockerfile in the same directory where app.js and package.json is founded
create Dockerfile
Build the image #docker build -t node-app .

create a container with the bulded image #docker run -it -d -p 3000:3000 node-app
test the app #curl http://localhost:3000 
response: {"message":"Hello, DevOps World!"}

tag the image and push to my private registry
docker image tag node-app  enkelejd/node-app:v1
docker push enkelejd/node-app:v1

v1: digest: sha256:a0142ff487c7175186f993dd141c730cbf91c692f232815bb35a2847dc89b48e size: 2836
----------------------------------------------------


KUBERNETES

create a deployment using the created image and create a service for the app

deploy the resources

check the pod if it is ready 
check the service node port number
test the app

$ curl http://localhost:31329
{"message":"Hello, DevOps World!"}



----
ARGOCD

In order to access the server UI you have the following options:

1. nohup kubectl port-forward service/my-argo-cd-argocd-server -n default 8080:443 > port-forward.log 2>&1 &

    and then open the browser on http://localhost:8080 and accept the certificate

2. enable ingress in the values file `server.ingress.enabled` and either
      - Add the annotation for ssl passthrough: https://github.com/argoproj/argo-cd/blob/master/docs/operator-manual/ingress.md#option-1-ssl-passthrough
      - Add the `--insecure` flag to `server.extraArgs` in the values file and terminate SSL at your ingress: https://github.com/argoproj/argo-cd/blob/master/docs/operator-manual/ingress.md#option-2-multiple-ingress-objects-and-hosts


After reaching the UI the first time you can login with username: admin and the random password generated during the installation. You can find the password by running:

kubectl -n default get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

(You should delete the initial secret afterwards as suggested by the Getting Started Guide: https://github.com/argoproj/argo-cd/blob/master/docs/getting_started.md#4-login-using-the-cli)

