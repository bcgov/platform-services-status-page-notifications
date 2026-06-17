In order to move to a newer and better supported version of OpenShift Pipelines, an upgrade of the operator is required on all of our managed OpenShift clusters. This is also required to address a bug in how Pipelines information is presented in the OpenShift web console after upgrading to OpenShift 4.18.

Before we apply this upgrade, all users of OpenShift pipelines should investigate their Pipeline configurations and remove ClusterTask references and replace with a Cluster Resolver reference instead.

An example YAML snippet showing what needs to be replaced and the equivalent using the same task (openshift-client).

Replace the following:

```
      taskRef:​
        kind: ClusterTask​
        name: openshift-client​
```

with this:

```
      taskRef:​
        resolver: cluster​
        params:​
          - name: kind​
            value: task​
          - name: name​
            value: openshift-client​
          - name: namespace​
            value: openshift-pipelines
```

Once this migration has been verified by Platform Services or Platform Operations, we will then proceed with scheduling the Pipelines migration to a newer version (from v1.18 to v1.20).
