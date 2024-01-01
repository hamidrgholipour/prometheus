## install offline

use helmchart - kuber-prometheus-stach => `helm install prometheus-local .  --debug  --namespace demo`

use online repo => `prometheus-community/kube-prometheus-stack`

*get grafana pass
`kubectl get secret grafana -o jsonpath={.data.admin-password} | base64 --decode ; echo`

*create cofigmap from exported json
`kubectl create configmap hamid-dash-configmap-automate  -n "nameSpace" --from-file=kuber-hamid-dashboard.json`

*apply label that makes it Grafana target
`kubectl label configmap hamid-dash-configmap-automate -n "nameSpace"  grafana_dashboard=1`



** note : hard code the accessModes to ReadWriteOnce because no two Prometheus servers should ever be sharing their storage
** note : for service monitor its important that use portname and namespace selector
