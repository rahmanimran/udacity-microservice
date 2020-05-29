GitHub Repo: https://github.com/rahmanimran/udacity-microservice

This is the Udacity project to split the udagram application into microservice and deploy it in Kubernetes cluster in AWS.

1. After spliting the services I've used docker to build the images

2. Pushed the docker images in my DockerHub repo

3. I've used eksctl to spin up the cluster

	eksctl create cluster --name udacluster7 --version 1.14 --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --node-ami auto

4. Changed the service type of /k8s/frontend-service.yaml and /k8s/reverseproxy-service.yaml to loadbalancer

5. kubectl apply -f . in the /k8s folder to spin the application

6. kubectl get all command will show all the resources

7. The frontend and reverseproxy services are acting as LoadBalancer. Copy the EXTERNAL_IP of reverseproxy and change the configuration of the /udacity-c3-frontend/src/environments/environment.prod.ts / & /udacity-c3-frontend/src/environments/environment.ts / to use this IP as backend instead of localhost.

8. To access the feed and user service from browser, I've added CORS header in the nginx.conf file.

9. Build new image of frontend and reverseproxy.

10. Update the kubernetes deployments applying kubectl apply -f . command same as Step-5

11. To check the application, I've copied the EXTERNAL-IP of frontend service and opened it in browser with port 8100.

12. Connected my Github Repo with Travis CI. Made the changes mentioned in the .travis.yml file. Then pushed it to Repo.

13. Deleted the cluster so that I don't get overcharged.  
