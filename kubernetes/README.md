## Kubernetes

<p align="center">
 <img src="images/kubernetes_logo.png?raw=true" alt="Logo" width="27%" height="27%" />
</p>

## Kubernetes Architecture

_Building a Kubernetes Home Lab environment from scratch might seem like a daunting task. However, it is actually pretty straightforward with the right tools in place. We are going to use Minikube to initialize a Kubernetes cluster from scratch in our home lab environment_

### What is Kubernetes?
Kubernetes is an open-source platform used for maintaining and deploying a group of containers e.g docker.Kubernetes can expose a container using DNS or its IP address. If traffic load is high, it balances load and distributes the network for deployment to be stable.

### Benefits of Kubernetes
1. _Portable and 100% open source_ - Kubernetes is compatible across several platforms . It is 100% open source project thus provides greater flexibility.
2. _Workload sclability_ - Kubernetes is known to be efficient. New servers are added and removed easily,it automatically changes the number of cunning containers and it scales many containers manuallly
3. _High availability_ - Kubernetes is designed to tackle the availability of both containers and infrastructure. It is highly reliable and can be made available in any physical environment
4. _Designed for deployment_ - One of the main  benefits of containerization is the ability to speed up testing, deploying and managing phases. Kubernetes is designed fro deployment and gives access to many of its features
5. _Service discovery and load balancing_ - Kubernetes can expose a container using DNS or its IP address. If traffic load is high, it balances load and distributes the network for deployment to be stable.
6. _Storage orchestration_ - Kubernetes automatically mounts storage systems like local storages and public cloud providers
7. _Self healing_ - Kubernetes restarts containers if failed, replaces containers, kills containers that dont respond to timely checks
8. _Automated rollouts and rollbacks_ - desired state of containers canbe describes using Kubernetes. The actual state of a container changes to the desired state of a controlled state
9. _Automatic bin packing_ - Kubernetes specifies how much CPU and RAM each container needs. Once resources are defined, managing the resurces and making decisions for them becomes easy 

## Installing Kubernetes on Ubuntu 22.04|20.04|18.04
## Kubernetes  Set Up with Oracle VirtualBox
  Remove/Purge completely any existing modules already downloaded 
 
 ```sudo apt-get purge kubeadm kubectl kubelet kubernetes-cni kube*```
  
<p align="left">
 <img src="images/purge.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

  Update Your System

   ```sudo apt update```

  Install Minikube

   ```wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64```

<p align="left">
 <img src="images/wget.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

   ```chmod +x minikube-linux-amd64```

   ```sudo mv minikube-linux-amd64 /usr/local/bin/minikube```
   
  Confirm Your Minikube Version Installed

   ```minikube version```

<p align="left">
 <img src="images/minikube.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

  Install kubectl on Ubuntu
  We need kubectl which is a command line tool used to deploy and manage applications on Kubernetes:

   ```curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl```

<p align="left">
 <img src="images/kubectl_install.jpg?raw=true" alt="Logo" width="80%" height="80%" />
</p>

  Make the kubectl binary executable

   ```chmod +x ./kubectl```

  Move the binary in to your PATH

   ```sudo mv ./kubectl /usr/local/bin/kubectl```

  Check version

   ```kubectl version -o json  --client```

<p align="left">
 <img src="images/kubectl_version.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

  Start Minikube on Your Ubuntu

   ```minikube start```

<p align="left">
 <img src="images/minikube_start.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

  To avoid this error:

<p align="left">
 <img src="images/minikube error.jpg?raw=true" alt="Logo" width="80%" height="80%" />
</p>

i. Install docker if you do not have in your machine 


```sudo apt install docker.io -y```

<p align="left">
 <img src="images/docker_install.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

ii. Create the docker group if not exist 


```sudo groupadd docker```

iii. Add user to the docker group


```sudo usermod -aG docker [user]```

<p align="left">
 <img src="images/docker_group.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

iv.Activate changes to the group


```newgrp docker```

v. Start minikube cluster


```minikube start```

<p align="left">
 <img src="images/minikube_start.jpg?raw=true" alt="Logo" width="80%" height="80%" />
</p>


  Minikube Basic operations
  To check cluster status, run:

   ```kubectl cluster-info```

<p align="left">
 <img src="images/kubectl_cluster.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

  Note that Minikube configuration file is located under ~/.minikube/machines/minikube/config.json
 
  To View Config, use:

   ```kubectl config view```

<p align="left">
 <img src="images/kubectl_config.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>

  To check running nodes:

   ```kubectl get nodes```

<p align="left">
 <img src="images/kubectl_nodes.jpg?raw=true" alt="Logo" width="50%" height="50%" />
</p>



  Enable Kubernetes Dashboard

   ```minikube addons list```


  To enable a module use command:


   ```minikube addons enable <module>```
eg

   ```minikube addons enable portainer```


  To open directly on your default browser, use:


   ```minikube dashboard```


 To get the URL of the dashboard


   ```minikube dashboard --url```


