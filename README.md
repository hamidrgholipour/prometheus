## deploying kubernetes and docker  monitoring with prometheus and grafana
helm -n monitor upgrade prometheus prometheus-community/kube-prometheus-stack --version 56.6.2  --values value-storage-etcd.yaml
