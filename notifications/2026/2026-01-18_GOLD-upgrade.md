Hi @all, your attention is needed!

**What is happening?**

CHG0074840 - CITZ - MCS GOLD - Pre-upgrade prep work
CHG0074841 - CITZ - PROD - MCS GOLD - Upgrade to 4.16.51

These changes represent the work involved to upgrade the GOLD cluster to Openshift 4.16.51 .

**When?**

- Prep will be Sunday January 18th 6am-9am
- Upgrade will be January 19th through 23rd 9am to 5pm each day

**Will there be an impact on the Platform apps?**

Prep changes will involve orphaned image data cleanup, and defragmenting the ETCD database. Defragmenting ETCD could cause some latency and slowness of the API but isn't expected to cause any breakage as each pod will be done individually with time to recover between operations. The hard prune will put the registry in read-only mode briefly while the pruner removes any orphaned images.

Upgrade changes will involve both an upgrade of the core of the cluster as well as draining/reboots of all nodes which will require pods to be drained onto other nodes. There may be some slowness for new pods coming up if it happens that a lot of new pods attempt to start on an empty node (just patched). We will announce daily when work for this will resume and be suspended at the end of each work day.

**Do I need to do anything?**

Monitor your applications for disruptions. Well designed applications should be able to tolerate the pod restarts without issue.

**Check the #devops-alert channel for the announcement of when the change is complete and check the health of your app.**

**Where do I get help if my app doesn't work after the change is complete?**

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in RocketChat as per these [RocketChat Channel Use Guidelines](https://developer.gov.bc.ca/docs/default/component/bc-developer-guide/rocketchat/rocketchat-channel-descriptions/).
