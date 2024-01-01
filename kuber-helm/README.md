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
By default, Prometheus discovers PodMonitors and ServiceMonitors within its namespace, that are labeled with the same release tag as the prometheus-operator release. Sometimes, you may need to discover custom PodMonitors/ServiceMonitors, for example used to scrape data from third-party applications. An easy way of doing this, without compromising the default PodMonitors/ServiceMonitors discovery, is allowing Prometheus to discover all PodMonitors/ServiceMonitors within its namespace, without applying label filtering. To do so, you can set prometheus.prometheusSpec.podMonitorSelectorNilUsesHelmValues and prometheus.prometheusSpec.serviceMonitorSelectorNilUsesHelmValues to false.
