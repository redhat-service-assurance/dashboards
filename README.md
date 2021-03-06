# Service Telemetry Dashboards

Dashboards for use with Service Telemetry Framework. These dashboards can be
loaded into a Grafana instance connected to backend data sources exposed by the
Service Telemetry Framework.

## Installation

Deploying a Grafana instance requires the deployment of the Grafana Operator
from the Community Operators catalog source.

```bash
oc create -f deploy/subscription.yaml
```

Edit your STF object to enable graphing by adding the following to the CustomResource:
```yaml
...
  graphing:
    enabled: true
    grafana:
      ingress_enabled: true
...
```

Create dashboards according to STF version
```bash
# stf-1.2 dashboards
oc create -f deploy/rhos-dashboard.yaml \
        -f deploy/rhos-cloud-dashboard.yaml

# stf-1.3 dashboards
oc create -f deploy/stf-1.3/rhos-dashboard.yaml \
        -f deploy/stf-1.3/rhos-cloud-dashboard.yaml

# vm dashboard [WIP]
oc create -f contrib/vm-view.yaml
```
