# canal-k8s


### 1. build canal image, [Canal](https://github.com/alibaba/canal)
> `docker build . -t canal:1.1.3`

### 2. Deploy zookeeper in kubernetes cluster
> `kubectl apply -f zookeeper-statefulset.yaml`

### 3. Deploy canal to kubernetes
> `kubectl apply -f canal-statefulset.yaml`
