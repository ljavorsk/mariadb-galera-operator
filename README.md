# MariaDB Galera OpenShift operator
Bachelor thesis for the Faculty of Information Technology in Brno University of Technology.

## Author: 
xjavor20@stud.fit.vutbr.cz  

## Abstract
Ansible-based Kubernetes/OpenShift operator, designed to deploy and watch the user-defined MariaDB Server and Galera Arbitrator Pods.
Users can define the number of Pods in the CRD manifest ``config/samples/_v1alpha1_mariadbgalera.yaml``.

The operator handles the correct Galera cluster connections between the deployed Pods using the Services to make it more Kubernetes and elegant way.

## Application
### How to run it?
#### Starting the operator ####
You need to have an OpenShift/Kubernetes cluster running and connected. For example, in a local environment, you can create a cluster using the ``minikube`` tool.

When the cluster is ready and connected, just execute ``make deploy`` which deploys the operator to the cluster.
The last step is to create the CRD, which the operator watches and uses as a reference when it comes to managing resources in the cluster. This can be done by executing ``oc apply -f config/samples/_v1alpha1_mariadbgalera.yaml`` in the root directory of this repository.

The operator can be running locally as well. This can be achieved by executing ``make install run`` command. The operator then uses the ``~/.kube/config`` configuration file to communicate with the cluster, so it has to be configured before.

#### Defining the desired state of the application ####
The desired state of the application is defined in the watched CRD. This CRD can be created from the sample located in ``config/samples/_v1alpha1_mariadbgalera.yaml`` file.  
The administrator can edit the number of desired nodes in the cluster by editing the **size** variable.  
Also, the number of Galera Arbitrator instances can be defined in the CRD editing the **garbdsize** variable.

Immediately after something change in the CRD, the operator picks up the changes and manage the resources in the cluster until the cluster matches the desired state.

#### Stopping the operator ####
To stop and delete the operator from the cluster, execute the ``make undeploy`` command.

### Used applications versions
The operator was tested and ran with these versions of used applications:

**Kubernetes** 

- Client version: version.Info{Major:"1", Minor:"10+", GitVersion:"v1.10.0+b3b92b2", GitCommit:"b3b92b2", GitTreeState:"clean", BuildDate:"2021-01-27T21:38:11Z", GoVersion:"go1.16beta1", Compiler:"gc", Platform:"linux/amd64"}

- Server version: version.Info{Major:"1", Minor:"23", GitVersion:"v1.23.3", GitCommit:"816c97ab8cff8a1c72eccca1026f7820e93e0d25", GitTreeState:"clean", BuildDate:"2022-01-25T21:19:12Z", GoVersion:"go1.17.6", Compiler:"gc", Platform:"linux/amd64"}

**Minikube**

Version: v1.25.2

## Licensing:
This code is licensed under MIT license.  
License information can be found in the LICENSE file. 

