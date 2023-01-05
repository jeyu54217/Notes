
- [Setting Up (Local)](#setting-up-local)
  - [Minikube](#minikube)
  - [kubectl (k8s CLI)](#kubectl-k8s-cli)
    - [Commands](#commands)
  - [K8s YAML](#k8s-yaml)
  - [Namespaces - Organizing components](#namespaces---organizing-components)
  - [Node \& Pod](#node--pod)
  - [Service \& Ingress](#service--ingress)
    - [Ingress](#ingress)
    - [Service](#service)
  - [ConfigMap \& Secret](#configmap--secret)
  - [Volumes](#volumes)
  - [Deployment \& StatefulSet](#deployment--statefulset)
- [Architecture](#architecture)
- [Helm (Package Manager)](#helm-package-manager)

# Setting Up (Local)
## Minikube
## kubectl (k8s CLI)
### Commands
►  Get status of different components
►  create a pod/deployment
►  layers of abstraction
►  change the pod/deployment
►  debugging pods
►  delete pod/deployment
►  CRUD by applying configuration file
## K8s YAML
## Namespaces - Organizing components
►  What is a Namespace?
►  4 Default Namespaces
►  Create a Namespace
►  Why to use Namespaces? 4 Use Cases
►  Characteristics of Namespaces
►  Create Components in Namespaces
►  Change Active Namespace
## Node & Pod
## Service & Ingress
### Ingress
►  What is Ingress? External Service vs. Ingress
►  Example YAML Config Files for External Service and Ingress
►  Internal Service Configuration for Ingress
►  How to configure Ingress in your cluster?
►  What is Ingress Controller?
►  Environment on which your cluster is running (Cloud provider or bare metal)
►  Demo: Configure Ingress in Minikube
►  Ingress Default Backend
►  Routing Use Cases
►  Configuring TLS Certificate
### Service
►   What is a Service in K8s and when we need it?
►  ClusterIP Services
►  Service Communication
►  Multi-Port Services
►  Headless Services
►  NodePort Services
►  LoadBalancer Services
## ConfigMap & Secret
## Volumes
►  The need for persistent storage & storage requirements
►  Persistent Volume (PV)
►  Local vs Remote Volume Types
►  Who creates the PV and when?
►  Persistent Volume Claim (PVC)
►  Levels of volume abstractions
►  ConfigMap and Secret as volume types
►  Storage Class (SC)
## Deployment & StatefulSet
►  What is StatefulSet? Difference of stateless and stateful applications
►  Deployment of stateful and stateless apps
►  Deployment vs StatefulSet
►  Pod Identity
►  Scaling database applications: Master and Worker Pods
►  Pod state, Pod Identifier
►  2 Pod endpoints

# Architecture
►  Worker Nodes
►  Master Nodes
►  Api Server
►  Scheduler
►  Controller Manager
►  etcd - the cluster brain
#  Helm (Package Manager)