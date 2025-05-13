Hi @all, your attention is needed!

**What is happening?**

CHG0069351 Standard Change 049 - Hosting - Shutdown servers for Decommission

Migrating 7 SILVER app nodes from Virtual to Physical

**When?**

Starting Wednesday May 21st @ 9:00AM and possibly running as late as 4:00PM on May 22nd.

**Will there be an impact on the Platform apps?**

SILVER pods will be drained from the impacted servers and re-scheduled to new nodes. Once the new node is drained and cordoned, the new replacement physical node will be brought online and put into service. Finally the old node will be removed from the cluster. This will be completed on one node at a time.

Impacted nodes are:
mcs-silver-app-59.dmz
mcs-silver-app-60.dmz
mcs-silver-app-61.dmz
mcs-silver-app-62.dmz
mcs-silver-app-63.dmz
mcs-silver-app-64.dmz

**Do I need to do anything?**

No action required.

**Check the #devops-alert channel for the announcement of when the change is complete and check the health of your app.**

**Where do I get help if my app doesn't work after the change is complete?**

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in RocketChat as per these [RocketChat Channel Use Guidelines](https://developer.gov.bc.ca/docs/default/component/bc-developer-guide/rocketchat/rocketchat-channel-descriptions/).
