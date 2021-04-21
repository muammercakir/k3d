# k3d Setup

## Create Cluster with Calico Backend and Nginx Ingress Controller

```k3d cluster create ckad-k8s --port 8080:80@loadbalancer --port 8443:443@loadbalancer --api-port 6443 --k3s-server-arg '--flannel-backend=none' --k3s-server-arg '--no-deploy=traefik' --volume "$(pwd)/calico.yaml:/var/lib/rancher/k3s/server/manifests/calico.yaml" --volume "$(pwd)/helm-ingress-nginx.yaml:/var/lib/rancher/k3s/server/manifests/helm-ingress-nginx.yaml" --servers 1 --agents 2```

## Create Cluster with Flannel Backend and Nginx Ingress Controller

```k3d cluster create ckad-k8s --port 8080:80@loadbalancer --port 8443:443@loadbalancer --api-port 6443 --k3s-server-arg '--no-deploy=traefik' --volume "$(pwd)/helm-ingress-nginx.yaml:/var/lib/rancher/k3s/server/manifests/helm-ingress-nginx.yaml" --servers 1 --agents 2```

## Create Cluster with Flannel Backend and Traefik 2 Ingress Controller

```k3d cluster create ckad-k8s --port 8080:80@loadbalancer --port 8443:443@loadbalancer --api-port 6443 --k3s-server-arg '--no-deploy=traefik' --volume "$(pwd)/helm-ingress-traefik.yaml:/var/lib/rancher/k3s/server/manifests/helm-ingress-traefik.yaml" --servers 1 --agents 2```

## Start Cluster

```k3d cluster start ckad-k8s```

## Stop Cluster

```k3d cluster stop ckad-k8s```



