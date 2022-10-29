# Nots and quotas
Possible dangerous deployment of POSTGRES with ReadWriteOnce PVC
Hello,

I checked that the GKE documentation (https://cloud.google.com/kubernetes-engine/docs/concepts/persistent-volumes) on PVCs says it's dangerous to use deployments with one replica and ReadWriteOnce. They say the following:

Even Deployments with one replica using a ReadWriteOnce volume are not recommended. This is because the default Deployment strategy will create a second Pod before bringing down the first pod on a recreate. The Deployment may fail in deadlock as the second Pod can't start because the ReadWriteOnce volume is already in use, and the first Pod won't be removed because the second Pod has not yet started. Instead, use a StatefulSet with ReadWriteOnce volumes.

Maybe it's worth to add a note about this, since we are creating the postgres deployments with one replica with this dangerous config.



DaemonSets?
replicasets?
ConfigMap? 

secret types:
generic - arbitrary number of key value pairs
docker-registry - private local registry
tls - https setup

Docs:

https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/

Some SO posts about when a StatefulSet would be useful:

https://stackoverflow.com/questions/41583672/kubernetes-deployments-vs-statefulsets

https://stackoverflow.com/questions/41732819/why-statefulsets-cant-a-stateless-pod-use-persistent-volumes



k create secret generic <secret_name> --from-literal key=value
k create secret generic <secret_name> --from <file>

ingress-nginx:
https://www.joyfulbikeshedding.com/blog/2018-03-26-studying-the-kubernetes-ingress-system.html

https://kubernetes.io/docs/concepts/services-networking/ingress/



You could have used a VM like VMWare to create a Linux installation.  Installed a load balancer like HAProxy and K8 cluster and showed it working on bare metal.  It is useful to see it deployed to a cloud provider but avoids the issues involved in self hosting.

