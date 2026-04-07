Hi @all, your attention is needed!

**What is happening?**

CHG0077435 STMS NET - Switch refresh MCS (Open Shift) Calgary Gold-DR
CHG0077437 STMS NET - Switch refresh MCS (Open Shift) Kamloops Silver
CHG0077439 STMS NET - Switch refresh MCS (Open Shift) Kamloops Gold

Network traffic for the production and storage interfaces of the OpenShift clusters will be migrated to new switches.

**When?**

CHG0077435 Starting at Tuesday, May 12 at 6PM and finishing before 11PM

CHG0077437 Starting at Tuesday, June 9 at 6PM and finishing before 11PM

CHG0077439 Starting at Tuesday, June 23 at 6PM and finishing before 11PM

**Will there be an impact on the Platform apps?**

No impact is expected.

There are two redundant connections for each traffic type from each server and they will be moved one at a time.

The switches in CHG0077439 for Gold also includes some Silver hosts.

**Do I need to do anything?**

No action required.

**Check the #devops-alert channel for the announcement of when the change is complete and check the health of your app.**

**Where do I get help if my app doesn't work after the change is complete?**

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in RocketChat as per these [RocketChat Channel Use Guidelines](https://developer.gov.bc.ca/docs/default/component/bc-developer-guide/rocketchat/rocketchat-channel-descriptions/).
