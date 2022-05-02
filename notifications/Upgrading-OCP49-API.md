# API Versioning Issues to Note Before We Upgrade from Openshift 4.8 to 4.9

## Introduction - Openshift Upgrades and Kubernetes

Red Hat vendor link: <https://docs.openshift.com/container-platform/4.9/release_notes/ocp-4-9-release-notes.html#ocp-4-9-removed-kube-1-22-apis><br>
Kubernetes vendor link: <https://kubernetes.io/docs/reference/using-api/deprecation-guide/#v1-22>

Red Hat Openshift bases itself off of Kubernetes and then adds additional technologies to create the product we all use today. This means that for each version of Openshift, it is matched against a specific version of Kubernetes.

For example, The version of Kubernetes that is used when we upgraded to Openshift 4.8 is Kubernetes version 1.21. We know this in advance since Red Hat in their release notes will put this version change details in the notes, since many technologies out there might not necessarily have compatibility details regarding Openshift versions, but do have this information for Kubernetes versions. Click [here](https://docs.openshift.com/container-platform/4.8/release_notes/ocp-4-8-release-notes.html#ocp-4-8-about-this-release) to see this for Openshift 4.8, which runs with Kubernetes version 1.21.

## API Versioning

<https://kubernetes.io/docs/concepts/overview/kubernetes-api/#api-groups-and-versioning>

When we create or update Kubernetes resources (ie: Deployments, Routes, RoleBindings) inside Openshift, these resources will be defined with various pieces of information, including an API version. This information is processed and handled by the API Server accordingly.

As an API resource matures over time in terms of how it is implemented and maintained, the API maintainers will choose to update the API version to match its level of maturity. For the current wave of API upgrades that will take place when we upgrade Openshift from 4.8 to 4.9 (thus upgrade from Kubernetes 1.21 to 1.22), the affected API resources will be all easily identifiable as being an API resource with version `v1beta1` and that version in Openshift 4.9 will need to be just `v1`.

At present Openshift 4.8 will respond to the affected API resources both with API versions `v1beta1` and `v1`, but when we upgrade our Openshift clusters to 4.9, then using API version `v1beta1` for some specific API resources will no longer work and not be created or updated depending on the requests involved.


## Which API Resources are Affected

<https://kubernetes.io/docs/reference/using-api/deprecation-guide/#v1-22>

There are a number of Kubernetes resources affected by this upcoming upgrade, but most of them do not apply to people performing development work for applications hosted inside Openshift. The applicable resources can be broken down into three specific Kubernetes resources.


### Ingress
<https://kubernetes.io/docs/reference/using-api/deprecation-guide/#ingress-v122>

- API groups `networking.k8s.io` and `extensions` are to be replaced with just `networking.k8s.io`.
- API version changes from `v1beta1` to `v1`.
- Above link details changes regarding how the Ingress contents are defined.

### Role and RoleBinding
<https://kubernetes.io/docs/reference/using-api/deprecation-guide/#rbac-resources-v122>

- API version changes from `v1beta1` to `v1`.
- no other changes to note.

## How to Check Your Application for API Compatibility Issues

### Audit existing Manifest content
If any of your application's manifest is stored as YAML or JSON, then you can search your manifest files yourself to first look for matches against Kubernetes resource types of `Ingress`, `Role` or `Rolebinding` and an API version of `v1beta1`.

### Check to Ensure Application Image is Latest or Close to it

If your application image interacts with the API either through the `oc` binary, or a kube/openshift library it may be out of date and not support the API changes. This will most likely be found in parts of your CI/CD flow, or in an app like Patroni that interacts with resources to maintain state. This method is somewhat spotty since Changelogs for images are not likely to specify this, but well-maintained images are more likely going to not make use of deprecated API versions compared to older images.

### Request API Audit Assistance

Via an internal solutions document, Red Hat has given us (Platform Ops) command line audit tools that allow us to check for API calls involving deprecated versions and inform us both of the "user" involved (actual user or service account) and the type of API resource involved, as well as the number of times this particular call was noted in both the last hour as well as the last 24 hours. This time limit means that for this method to trigger, that the involved parties need to re-upload their application manifest within the maximum period of a 24 hour period, and thus we recommend that interested parties first secure the attention of a Platform Ops via [#devops-operations](https://chat.developer.gov.bc.ca/channel/devops-operations) first before re-applying their application.

This method of auditing will also generate false positives, since we may see LIST requests involving a deprecated API, but that's more due to the API server just picking the first API version available to it. The bigger concern during this audit is identifying deprecated API calls that create or change the specific resources we want to watch out for. When we upgrade to Openshift 4.9, those deprecated API versions will no longer exist, and LIST requests and similar methods will just use the v1 API version.

### Request Test Environment in a LAB cluster

For important applications needing full assurance that nothing will break before we move forward to upgrade our PROD Openshift clusters, the best solution if you are not certain that 100% of the issues are addressed is to request via regular channels for requesting a new namespace and specify that LAB is required and why (Openshift 4.9 compatibility tests). We do upgrade our LAB clusters to the new version of Openshift first for both internal testing as well as for scenarios like this.

## Frequently Asked Questions

### Q: Why Can't We Just Look At Existing Kubernetes Resources for v1beta1 Versions?
The answer to this question regarding why we need to do an audit versus a simple query of "give me all v1beta1 Kubernetes resources" is because the API Server and associated internal mutating hooks, helpfully re-writes API resource requests as needed if the newer API version needs changes. This can be helpful for cases like with the Ingress resource where formatting changes need to be made between v1beta1 and v1, and you're not sure what that should look like. You can look at the existing resource's YAML contents to see what the API server did to the resource, and back-port those changes back to offline manifest files as appropriate.

### Q: What happens when the Openshift clusters are upgraded to version 4.9 and needed manifest changes didn't take place?
Once the Openshift upgrade is completed to version 4.9, then any attempts to make API requests involving the involved resources and API version v1beta1 will no longer work, and return an error instead. Changes will then  need to be made to fix this in the manfifest file, upgrade image versions, and so on to fix it.


### Q: Is there any way of knowing in advance when we might have similar API deprecation issues to deal with?
The Kubernetes web site is quite helpful in letting us know well in advance when future planned API changes will be happening and to which Kubernetes version this change will be tied to. According to [this](https://kubernetes.io/docs/reference/using-api/deprecation-guide/) link, the next Kubernetes version that will stop supporting additional legacy API versions is Kubernetes v1.25. If Red Hat stays true to its policy of upgrading Kubernetes version for each Openshift release, then this will likely be Openshift version 4.12. Which based on current release schedules and upgrade paths, means we won't be doing this again until well in 2023 (perhaps 2024).

