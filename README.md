## deploying kubernetes and docker  monitoring with prometheus and grafana
helm -n monitor upgrade prometheus prometheus-community/kube-prometheus-stack --version 56.6.2  --values value-storage-etcd.yaml

* if edit the image repo edit it in other charts like grafana