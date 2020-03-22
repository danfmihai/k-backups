# k-backups
ETCD backup 

```
git clone git@github.com:florinen/k-backups.git
cd k-backups
kubectl create -f etcd_backup.yaml
kubectl create -f etcd_cleanup.yaml
```
Veiw details abouth the jobs:
```
kubectl get cronjobs -n kube-system
kubectl describe cronjobs -n kube-system backup
kubectl describe cronjobs -n kube-system etcd-cleanup
or
kubectl get pods -n kube-system
kubectl describe pod -n kube-system backup
kubestl describe pod -n kube-system etcd-cleanup
```

To change configuration do edit the cronjob or make changes to definiton files and apply it.
```
kubectl edit cronjob -n kube-system etcd-cleanup
kubectl edit cronjob -n kube-system backup
or
kubectl apply -f etcd_backup.yaml
kubectl apply -f etcd_cleanup.yaml
```
To delete the cronjob:
```
kubectl delete -f etcd_backup.yaml
kubectl delete -f etcd_cleanup.yaml
or
kubectl delete cronjob backup -n kube-system
kubectl delete cronjob etcd-cleanup -n kube-system
```


Reference links:

https://labs.consol.de/kubernetes/2018/05/25/kubeadm-backup.html

https://crontab.guru/