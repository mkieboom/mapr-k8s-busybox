# mapr-k8s-busybox

##### Pre-requisite
Make sure to have the MapR Volume Driver for Kubernetes installed and running on your Kubernetes environment.

##### Clone this repo
```
git clone https://github.com/mkieboom/mapr-k8s-busybox
cd mapr-k8s-busybox
```

##### Launch the dynamic MapR volume creation on Kubernetes
```
# Change the MapR specific parameters in the yaml file to reflect your MapR cluster configuration
  
kubectl create -f mapr-k8s-busybox-secure-part1-volumedriver.yaml
```

##### Launch container leveraging the dynamicly created volume
```
# Change the MapR and Postgres specific parameters in the yaml file to reflect your MapR & Postgres configuration

kubectl create -f mapr-k8s-busybox-secure-part2-container.yaml
```
##### Logon into docker
```
kubectl exec -it mapr-k8s-busybox -n mapr-apps -- sh
```

##### Check access to MapR
```
ls -al /dynvolume
echo "hello world" >> /dynvolume/myfile.txt
ls -al /dynvolume
```