# Kubernetes commands

$ kubectl get no     - to get the nodes running on the cluster

$ kubectl describe node <nodename>    - used to get details about the node

# POD is the smallest deployable unit in kubernetes

$ kubectl get po  - to get the number of pods running on k8s, you also see number of pods running under READY column

<img width="593" height="150" alt="Screenshot 2025-08-29 at 8 42 23 AM" src="https://github.com/user-attachments/assets/e9f88837-c5ac-44d2-b7b7-61e59fcadf63" />

You can see errors in pod in 'events' section of describe po command-

<img width="1013" height="376" alt="Screenshot 2025-08-29 at 8 45 32 AM" src="https://github.com/user-attachments/assets/5595f5d2-e9b6-4bd5-9488-31b8927872fd" />


$ kubectl run <pod-name> --image=<name-of-image>    -- To create pod from an image

$ kubectl describe po <podname>   ... you can check many details like how many containers are running inside pod, image from which pod is built, etc using this command.

# kubectl explain-

$ kubectl explain <resource name like pod, node, service, deployment>    # used to list more information about the resource
For ex: $ kubectl explain pod                                            # gives you information about what pod is as below. It is documentation in short!

<img width="1253" height="761" alt="Image" src="https://github.com/user-attachments/assets/e46a41bf-1dd7-437b-98a6-1e1a303f5c54" />

# Kubectl aliases-

These can be added to your ~/.bashrc or ~/.zshrc so they’re always available in your terminal session. Reload your shell (source ~/.bashrc) and your muscle memory will start kicking in, cutting command execution time dramatically.

<img width="786" height="936" alt="Image" src="https://github.com/user-attachments/assets/48e85285-fb99-447e-92b2-c396a2334fb5" />
