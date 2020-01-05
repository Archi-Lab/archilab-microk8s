# ArchiLab MicroK8s

## MicroK8s installation

Install MicroK8s on master and all nodes:

```
sudo snap install microk8s --classic --channel=1.17/stable
```

Add user to group:

```
sudo usermod --append --groups microk8s $USER
```

Relog for the group update:

```
su --login $USER
```

Wait for Microk8s to be ready:

```
microk8s.status --wait-ready
```

## Cluster setup

Repeat the following steps for each node.

Execute on the master:

```
microk8s.add-node
```

Copy the printed command and execute it on node:

```
microk8s.join <master>:<port>/<token>
```

## Addon activation

Execute on the master:

```
microk8s.enable dashboard dns ingress istio metallb storage
```

## Kubectl alias

Create alias for microk8s.kubectl:

```
sudo snap alias microk8s.kubectl kubectl
```

## Namespace creation

Copy `namespaces` folder to the master and execute:

```
kubectl create -f ./namespaces
```
