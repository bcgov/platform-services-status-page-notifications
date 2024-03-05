**What is happening?**

CHG0057394 - CITZ - SILVER - Replace cluster certificates
CHG0057465 - CITZ - GOLD - Replace cluster certificates
CHG0057469 - CITZ - GOLDDR - Replace cluster certificates

These three changes represent the work involved to replace the two cluster certificates on each production Openshift cluster prior to their April 1st 2024 expiry date. 

The EMERALD cluster has already received its certificate upgrades during a recent Openshift upgrade RFC.

**When?**

Each RFC is scheduled for 6am on the respective dates mentioned. This is to reduce impact to users since the certificate replacement will involve a restart for the pods responsible for providing web console services to each cluster.

SILVER (CHG0057394) will be implemented on March 12th 2024.
GOLD (CHG0057465) will be implemented on March 13th 2024.
GOLDDR (CHG0057469) will be implemented on March 14th 2024.

**Will there be an impact on the Platform apps?**

During the change window users might notice a temporary disruption to the web console, but a web browser refresh should address that. No other impacts should be noticed otherwise.

**Do I need to do anything?**

Monitor your applications to ensure they continue working as expected.

**Check the #devops-alert channel for the announcement of when the change is complete and check the health of your app.**

**Where do I get help if my app doesn't work after the change is complete?**

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in Rocket.Chat as per these [RocketChat Channel Use Guidelines](
https://developer.gov.bc.ca/Getting-human-support-for-issues-not-covered-by-devops-requests).
