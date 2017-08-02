# cluster-autoscaler-chart
Helm chart for installing a Kubernetes cluster autoscaler

# Helm
We are using Helm along with Quay.io to host our Helm charts.  See https://github.com/app-registry/appr-helm-plugin and https://coreos.com/blog/quay-application-registry-for-kubernetes.html.

See https://docs.helm.sh for more about Helm.

# Prerequisites
* Helm 2.5.1
* Kubernetes 1.4+ with Beta APIs enabled
* [Helm Registry plugin](https://github.com/app-registry/appr-helm-plugin)

# Installing this chart
To install with release name `my-release` run:
```
helm registry install quay.io/3dsim/cluster-autoscaler --name=my-release --set env=<env>
```

# Uninstalling the Chart

To uninstall/delete the my-release deployment:
```
helm delete my-release
```
The command removes all the Kubernetes components associated with the chart and deletes the release.


# Customizing this chart
See [values.yaml](values.yaml) for configuration options.

Use `--set` syntax to set a value:
```console
helm registry install quay.io/3dsim/cluster-autoscaler --name=my-release --set resources.limits.cpu=300m
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm registry install quay.io/3dsim/cluster-autoscaler --name=my-release -f values.yaml
```

# Developers
If you make changes and want to push a new version to quay.io, do the following...

1.  Bump the version in [Chart.yaml](Chart.yaml).
2. Login to quay.io (if you haven't previously)
```
helm registry login -u <your username> quay.io
```
3. Push new version
```
helm registry push --namespace 3dsim quay.io
```

See https://github.com/app-registry/appr-helm-plugin#create-and-push-your-own-chart for more info.

4.  Commit all outstanding changes to github