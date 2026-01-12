Hi @all, your attention is needed!

**What is happening?**

CHG0069444 Standard Change 049 - Hosting - Shutdown server for Decommission

Migrating 3 SILVER INFRA nodes from Virtual to Physical

**When?**

Starting Tuesday May 27th @ 9:00AM and running until 4:30PM.

**Will there be an impact on the Platform apps?**

SILVER pods will be drained from the impacted servers and re-scheduled. The old nodes will be removed from the cluster and replaced by newly built nodes. This will be completed on one node at a time. The HAProxy routers are hosted on these servers so connections will drop as it fails over. Otherwise it is not expected to be particularly disruptive as applications are not hosted on these servers.

Impacted nodes are:
mcs-silver-infra-04.dmz
mcs-silver-infra-05.dmz
mcs-silver-infra-06.dmz

**Do I need to do anything?**

No action required.

**Check the #devops-alert channel for the announcement of when the change is complete and check the health of your app.**

**Where do I get help if my app doesn't work after the change is complete?**

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in RocketChat as per these [RocketChat Channel Use Guidelines](https://developer.gov.bc.ca/docs/default/component/bc-developer-guide/rocketchat/rocketchat-channel-descriptions/).
