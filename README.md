# K8s Deployment Lab
In this tutorial, we will study different types of K8s deployment (Replication Controller, ReplicaSet, deployment) in order to horizontally scale applications and efficiently handle more loads.
## Replication Controller
ReplicationController is used to manage application scaling. It ensures that a speciﬁed number of pod replicas are running at any point of time. So we make sure that a set of pods is always up and available.
## ReplicaSet
ReplicaSet is enhanced version of ReplicationController. The main difference between a ReplicaSet and a ReplicationController right now is the selector support that identifies a set of objects in K8s. In fact, ReplicaSets allow us to use “set-based” label selector such as In, NotIn, Exists, ... 
```
selector:
    matchExpressions:
      - {key: tier, operator: In, values: [frontend]}
```
ReplicaSet is not limited to owning Pods speciﬁed by its template: It can acquire other Pods which have matching Labels.
## Deployment
Deployment is one step higher than ReplicaSet. It means the desired state of ReplicaSet. we can control both ReplicaSets and Pods in a declarative manner.
#### Deployment Use Cases
- Create Deployment: Deploy Application Pods.
- Update Deployment: Push new version of Application in Controlled Manner.
- Rolling Upgrade: Upgrade Application in Zero Downtime.
- Rollback: Rollback the Upgrade in case of unstable Upgrade. Revise the Deployment State.
- Pause/Resume Deployment: Rollout a certain percentage.
## Instructions
1. Clone the project 
```
git clone https://github.com/mehdijebali/K8s_Deployment_Lab.git
```
2. Apply manifest using **kubectl**
```
kubectl apply -f /path/to/manifest.yml
```
3. You can check the status of pod/service with the following command
```
kubecl get pods | grep <pod_name>
```
```
kubectl get deployments | grep <deployment_name>
```
4. You can also list additional information of pod (service) for any debugging issue
```
kubectl describe pod <pod_name>
```
```
kubectl describe deployment <deployment_name>
```
The **<pod_name> (<deployment_name>)** is the value of the key `metadata.name` in each k8s manifest yaml file.