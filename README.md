# istio

## pods and k8s

### What is a pod?
Containers that share network namespace and resources (cgroup settings). Example of pod and shared namespaces from host after `kubectl apply -f pod.yaml`
```
$ sudo su
# PIDS="self $(pidof nginx|cut -d' ' -f 1) $(pidof sleep)"; 
for ns in /proc/self/ns/*; do name=$(basename $ns); echo $name; 
  for pid in $PIDS; do readlink /proc/$pid/ns/$name; done; 
done

cgroup
cgroup:[4026531835]
cgroup:[4026531835]
cgroup:[4026531835]
ipc
ipc:[4026532453]
ipc:[4026532576]
ipc:[4026532576]
mnt
mnt:[4026532451]
mnt:[4026532732]
mnt:[4026532735]
net
net:[4026532457]
net:[4026532656]
net:[4026532656]
pid
pid:[4026532455]
pid:[4026532734]
pid:[4026532737]
pid_for_children
pid:[4026532455]
pid:[4026532734]
pid:[4026532737]
user
user:[4026531837]
user:[4026531837]
user:[4026531837]
uts
uts:[4026532452]
uts:[4026532733]
uts:[4026532736]
```
