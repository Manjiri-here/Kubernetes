# Kubernetes commands

$ kubectl get no     - to get the nodes running on the cluster

$ kubectl describe node <nodename>    - used to get details about the node

# POD is the smallest deployable unit in kubernetes

$ kubectl get po       ...to get the number of pods running on k8s, you also see number of pods running under READY column

<img width="593" height="150" alt="Screenshot 2025-08-29 at 8 42 23 AM" src="https://github.com/user-attachments/assets/e9f88837-c5ac-44d2-b7b7-61e59fcadf63" />

You can see errors in pod in 'events' section of describe po command-

<img width="1013" height="376" alt="Screenshot 2025-08-29 at 8 45 32 AM" src="https://github.com/user-attachments/assets/5595f5d2-e9b6-4bd5-9488-31b8927872fd" />

To create a pod use below command-

$ kubect run <podname> --image=<imagename>

$ kubectl describe po <podname>   ... you can check many details like how many containers are running inside pod, image from which pod is built, etc using this command.

$ kubectl delete po <podname>

# kubectl explain-

$ kubectl explain <resource name like pod, node, service, deployment>    # used to list more information about the resource
For ex: $ kubectl explain pod                                            # gives you information about what pod is as below. It is documentation in short!

<img width="1253" height="761" alt="Image" src="https://github.com/user-attachments/assets/e46a41bf-1dd7-437b-98a6-1e1a303f5c54" />

# Kubectl aliases-

These can be added to your ~/.bashrc or ~/.zshrc so they’re always available in your terminal session. Reload your shell (source ~/.bashrc) and your muscle memory will start kicking in, cutting command execution time dramatically.

<img width="786" height="936" alt="Image" src="https://github.com/user-attachments/assets/48e85285-fb99-447e-92b2-c396a2334fb5" />


# Scale Deployment to Zero: 

This stops all pods by scaling deployment replicas to zero:

kubectl scale deployment <deployment-name> --replicas=0

Example:
kubectl scale deployment myapp-profile --replicas=0

This keeps the deployment resource but no pods run, so your app stops working.

# Restarting pods/deployment-

kubectl rollout restart deployment webapp-mysql -n delta  -- here -n delta is namespace and webapp-mysql is deployment name

When you run kubectl rollout restart deployment webapp-mysql -n delta:

-n delta is the namespace, and webapp-mysql is the deployment name.

Kubernetes triggers a rolling restart of the deployment, meaning:

New pods are started one at a time.

Once a new pod is healthy and ready, an old pod is terminated.

This repeats until all pods are replaced with fresh instances.

Containers inside the pods are fully restarted—new processes start from scratch.

The application inside the container is restarted as the new pod/container launches, running its entrypoint/command just like during initial deployment.
