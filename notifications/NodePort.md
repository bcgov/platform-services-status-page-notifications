**What is happening?**

On DATE new quotas will be added to all namespaces to prevent the use of unsupported ServiceTypes.

```console
$ oc describe quota services-quota
Name:                   services-quota
Resource                Used  Hard
--------                ----  ----
services.loadbalancers  0     0
services.nodeports      0     0
```

Kubernetes allows several types to be set in a service definition <https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types> but the Private Cloud OpenShift clusters only supports the ClusterIP type. The `NodePort` type causes a port to be exposed on all the nodes in the cluster. But since the cluster is behind a NAT that port can’t be connected to, so this provides no useful functionality. The `LoadBalancer` type is designed for use in Public Clouds that have Load Balancers that can be provisioned. In OpenShift we can use Routes to accomplish the same thing. The primary source of these service definitions are from Helm charts or other pre-made templates.

**Do I need to do anything?**

The Platform Ops team has already worked with teams that had these unsupported ServiceTypes in use and cleaned them up. This information is shared as FYI to let the product teams on the Private Cloud Openshift Platform know about the measure that are going to put in place that will prevent the product teams from accidentally using an unsupported ServiceType in their service definitions.

Love, Platform Services Team, xo
