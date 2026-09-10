Hi @Openshift-alerts, your attention is needed!

## What is happening?

CHG0081401 - MCS - NetApp Storage Cluster CDOT OS Upgrade - SILVER
CHG0081403 - MCS - NetApp Storage Cluster CDOT OS Upgrade - GOLD
CHG0081404 - MCS - NetApp Storage Cluster CDOT OS Upgrade - GOLDDR

The DXC Advanced Solution (DXCAS) Storage team will be upgrading the NetApp storage appliances responsible for providing persistent storage services to all OpenShift production clusters. This maintenance will ensure the fix for the upcoming daylight saving time change will be applied as well as apply relevant security fixes.

## When?

CHG0081233 (SILVER) will start after 07:00 on Sunday September 27th and finish before 22:00 the same day.
CHG0081234 will start after 06:00 on Sunday October 18th and finished before 22:00 the same day.
CHG0081235 will start after 06:00 on Sunday October 25th and finish before 22:00 the same day.

## Will there be an impact on the Platform apps?

There will be no impact to running pods during this maintenance. Storage operations involving block storage might be delayed for a short period of time while this maintenance is underway.

## Do I need to do anything?

No, monitor your applications as usual.

*Check the MS Teams Openshift-alerts channel for the announcement of when the change is complete and check the health of your app.*

## Where do I get help if my app doesn't work after the change is complete?

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in MS Teams.
