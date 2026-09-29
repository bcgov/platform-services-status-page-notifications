Hi @channel, your attention is needed!

## What is happening?

CHG0081871 - CSBC MCS GOLDDR - NetApp Storage Node Reboots
CHG0081874 - CSBC MCS GOLD - NetApp Storage Node Reboots
CHG0081875 - CSBC MCS SILVER - NetApp Storage Node Reboots

The vendor has identified an issue where NetApp devices may crash after too long of an uptime. They recommend rebooting them after 140 days of uptime until a patch can be released and applied.

## When?

Gold DR - Friday Oct 2nd at 18:00
Gold - Saturday Oct 3rd at 06:00
Silver - Sunday Oct 4th at 06:00

## Will there be an impact on the Platform apps?

During the failover / failback volume operations may be stalled for a few minutes. Pods may take longer to start.

Running pods will be unaffected.

## Do I need to do anything?

No action required.

*Check the MS Teams Openshift-alerts channel for the announcement of when the change is complete and check the health of your app.*

## Where do I get help if my app doesn't work after the change is complete?

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in MS Teams.
