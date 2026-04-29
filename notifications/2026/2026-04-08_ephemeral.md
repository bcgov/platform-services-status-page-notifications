Hi @all, your attention is needed!

**What is happening?**

To prevent issues caused by nodes running out of storage, we are implementing a quota on ephemeral storage. This is not a limit on PVC usage. It only applies to storage used without a PVC. We will set a default limit of 1 Gi for all new pods, along with a namespace-wide quota of 100 Gi for ephemeral storage.

This change may affect teams that use a large amount of ephemeral storage. You may need to adjust the default limits if your workloads require more than the 1 Gi per pod allowed in your namespace.

You can check your usage by inspecting how much data your pods are writing to directories that are not backed by a mounted PVC. Examples include emptyDir volumes which could include /tmp, /var/lib, or application data directories. If you notice you are using an unusually high amount of ephemeral storage, consider using PVCs instead of writing to an emptyDir.

If you are using a large amount of ephemeral storage you may need to increase your default pod allowances. An example of this can be found if you edit a pod (potentially a statefulset or deployment):

[...]
    Limits:
      cpu:                500m
      ephemeral-storage:  1Gi
      memory:             512Mi
[...]

In this instance you may need to increase the ephemeral-storage limit on this pod if you require more than the 1Gi provided.

**When?**

SILVER, EMERALD, GOLD and GOLDDR will have these new limits updated on April 29th between 9 AM and 4 PM.

**Will there be an impact on the Platform apps?**

There will be no immediate impact unless you are using a large amount of ephemeral storage.

**Do I need to do anything?**

Ephemeral storage is temporary storage that is not a PVC. Currently it is unlimited per pod but this could potentially cause issues if all the ephemeral storage on a node is exhausted. You will need to check your emptyDir mount points for usage with the 'du' command. We don't anticipate that this change will impact most teams, but we have noted a few namespaces that are using ephemeral storage for dev/test databases without assigning a PVC.

If you are using more than 1Gi of ephemeral storage per pod, you will need to monitor your pods and increase the amount available to the pod as needed.

**Check the #devops-alert channel for the announcement of when the change is complete and check the health of your app.**

**Where do I get help if my app doesn't work after the change is complete?**

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in RocketChat as per these [RocketChat Channel Use Guidelines](https://developer.gov.bc.ca/docs/default/component/bc-developer-guide/rocketchat/rocketchat-channel-descriptions/).
