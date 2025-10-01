Steps I did to use k8s with docker:

1. Cloned my git repo in local and cd into that repo. manjiri@Abhis-MacBook-Pro docker % git clone https://github.com/Manjiri-here/Docker-demo 

2. Build the docker image as below- manjiri@Abhis-MacBook-Pro docker % cd Docker-demo manjiri@Abhis-MacBook-Pro Docker-demo % ls demo-result.md		docker-commands		docker-volume		Dockerfile		Dockerfile_multistage	manage.py		my_profile		profile_site		README.md		requirements.txt manjiri@Abhis-MacBook-Pro Docker-demo % docker build -t myprofile:v1
 
3. To start docker in Mac  - manjiri@Abhis-MacBook-Pro Docker-demo % open -a Docker 

4. Now we push the image to docker hub  -

manjiri@Abhis-MacBook-Pro Docker-demo % docker login 

manjiri@Abhis-MacBook-Pro Docker-demo % docker tag myprofile:v1 manjirinaik/docker-image-1:latest      — tag the image to docker hub repo by creating a repo in docker hub 

5. manjiri@Abhis-MacBook-Pro Docker-demo % docker push manjirinaik/docker-image-1:latest.   
The push refers to repository [docker.io/manjirinaik/docker-image-1]
76249c7cd503: Pushed
d8e6783dcc3a: Pushed
d216633d146c: Pushed
fbd7f6e96468: Pushed
af34b583c4dc: Pushed
43564ffbf5fa: Pushed
75b7e7154a30: Pushed
latest: digest: sha256:cd113a555f0257864e77e96f9a253f218ed412d72aee2f0d32ec620e020fd18f size: 856

6. Now we write deployment.yaml and service.yaml file. (These files are present in the k8s repo in github) 

7. Make sure k8s cluster is running (If testing on Minikube then check with minikube start and Minikube status and 'kubectl cluster-info') 

8. Now execute deployment.yaml and service.yaml file as below-  

kubectl apply -f deployment.yaml 
kubectl apply -f service.yaml 

9. Now we see the 3 containers running as we have kept replica set=3,  

10) manjiri@Abhis-MacBook-Pro Docker-demo % kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   86d   v1.33.1
manjiri@Abhis-MacBook-Pro Docker-demo % kubectl get po
NAME                                READY   STATUS    RESTARTS      AGE
myapp-profile-6f848c4cf7-gxjhm      1/1     Running   0             109s
myapp-profile-6f848c4cf7-v97pd      1/1     Running   0             109s
myapp-profile-6f848c4cf7-z9kgl      1/1     Running   0             109s
nginx-deployment-647677fc66-nts6q   1/1     Running   1 (85d ago)   86d
redis-master-85fd4bc5f-m7qn8        1/1     Running   1 (85d ago)   85d  

11) manjiri@Abhis-MacBook-Pro Docker-demo % minikube service docker-demo-service
|-----------|---------------------|-------------|---------------------------|
| NAMESPACE |        NAME         | TARGET PORT |            URL            |
|-----------|---------------------|-------------|---------------------------|
| default   | docker-demo-service |          80 | http://192.168.49.2:32315 |
|-----------|---------------------|-------------|---------------------------|
🏃  Starting tunnel for service docker-demo-service.
|-----------|---------------------|-------------|------------------------|
| NAMESPACE |        NAME         | TARGET PORT |          URL           |
|-----------|---------------------|-------------|------------------------|
| default   | docker-demo-service |             | http://127.0.0.1:51126 |
|-----------|---------------------|-------------|------------------------|
🎉  Opening service default/docker-demo-service in default browser...
❗  Because you are using a Docker driver on darwin, the terminal needs to be open to run it.

12)  Remember that if you make any changes to app and create a new image then you will need to restart the pods as it does not automatically take the updated image from docker hub. And after restart we can apply deployment and yaml files.  

13) Output: App runs with command: 

% minikube service docker-demo-service and the app opens in your default browser automatically-

<img width="1792" height="634" alt="Screenshot 2025-09-10 at 9 35 12 PM" src="https://github.com/user-attachments/assets/816a1653-40f1-4580-b161-8c671e7adceb" />

<img width="566" height="166" alt="Screenshot 2025-09-11 at 4 28 39 PM" src="https://github.com/user-attachments/assets/8b6a31a7-5c2e-4c0e-9bde-f5eac76bf137" />


