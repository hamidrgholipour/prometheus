## install offline

use helmchart - kuber-prometheus-stach => `helm install prometheus-local .  --debug  --namespace demo`

## install online
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
use online repo => `prometheus-community/kube-prometheus-stack`

*get grafana pass
`kubectl get secret grafana -o jsonpath={.data.admin-password} | base64 --decode ; echo`

*create cofigmap from exported json
`kubectl create configmap hamid-dash-configmap-automate  -n "nameSpace" --from-file=kuber-hamid-dashboard.json`

*apply label that makes it Grafana target
`kubectl label configmap hamid-dash-configmap-automate -n "nameSpace"  grafana_dashboard=1`


Install prometheus stack `helm -n monitor install prometheus prometheus-community/kube-prometheus-stack --version 56.6.2  --values value-storage-etcd.yaml`
Install prometheus  `helm -n monitor upgrade prometheus prometheus-community/prometheus --version 25.13.0 --values prometheus-vales-storage.yaml `

 
** note : hard code the accessModes to ReadWriteOnce because no two Prometheus servers should ever be sharing their storage
** note : for service monitor its important that use portname and namespace selector
