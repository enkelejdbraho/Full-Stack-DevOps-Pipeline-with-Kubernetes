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

