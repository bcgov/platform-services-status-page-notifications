
**What is happening?**

Enable per-namespace alerting in Silver and Emerald

Gold and Gold DR have been setup since last August to monitor all applications for common issues and send emails to the product owner and tech leads when they are detected. This functionality is now being expanded to the Silver and Emerald clusters.

**When?**

Tuesday March 19th

**Will there be an impact on the Platform apps?**

No impact to applications. Product owners and Tech leads may start getting emails about their applications hosted on Silver and Emerald.

- Product Owner will get emails for Critical alerts in Prod namespace
- Tech Leads will get emails for ALL alerts in ALL namespaces
- Critical alerts will repeat every 48 hours
- Warnings and Info will repeat every 5 days

**Do I need to do anything?**

Please make sure your contacts are up to date in the [Product Registry](https://registry.developer.gov.bc.ca/)

If you get an email about the health of an application you should work to address it.

[Read more](https://developer.gov.bc.ca/docs/default/component/platform-developer-docs/docs/platform-automation/alertmanager/) about the AlertManager setup and what kinds of alerts it will send.

**Check the #devops-alert channel for the announcement of when the change is complete and check the health of your app.**

**Where do I get help if my app doesn't work after the change is complete?**

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in RocketChat as per these [RocketChat Channel Use Guidelines](https://docs.developer.gov.bc.ca/rocketchat-channel-descriptions/).
