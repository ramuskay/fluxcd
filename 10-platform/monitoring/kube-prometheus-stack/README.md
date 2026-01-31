TODO : 
- Alerter external not working (discord)
    - Putting the current conf makes not alerter pods (reosurces more generally) pop
    - Removing the config section about alertmanager make it pop
    - Remvoing the secret alertmanager-kube-prometheus-stack-alertmanager (which has the right info) makes it instanelly pop
- Grafana password not working
    - Using `grafana-cli admin reset-admin-password NEW_PASSWORD` to set the value of the secret
    - Have to fix it but we should connect to SSO at some point, so well...