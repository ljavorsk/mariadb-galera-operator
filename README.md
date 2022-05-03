# MariaDB Galera OpenShift operator
Bachelor thesis in the BUT FIT.

## Authors: 
xjavor20@stud.fit.vutbr.cz  

## Abstract
Ansible-based Kubernetes/OpenShift operator, designed to deploy and watch the user-defined number of MariaDB Server Pods.
User can define number of Pods in the CRD manifest ``config/samples/_v1alpha1_mariadbgalera.yaml``.

The operator handles the correct Galera cluster connections between the deployed Pods using the Services to make it more Kubernetes and elegant way.

## Application
### How to run it?
You need to have an OpenShift/Kubernetes cluster running and connected. For example, in a local enviroment, you can create a cluster using the ``minikube`` tool.

When the cluster is ready and connected, just execute ``make deploy`` which deploys the operator to the cluster.
The last step is to create the CRD which the operator uses. Thiscan be done by ``oc apply -f config/samples/_v1alpha1_mariadbgalera.yaml`` in the root directory of this repository.
