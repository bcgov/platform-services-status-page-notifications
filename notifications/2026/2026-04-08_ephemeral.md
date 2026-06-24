Hi @channel, your attention is needed!

## What's happening?

To prevent issues caused by nodes running out of storage, we will be introducing limits on ephemeral storage usage.

- This change does not affect PVC usage.
- It applies only to storage that is not backed by a PVC (e.g., emptyDir, container writable layers, etc.).

We will implement:

- A default per-pod limit of 500Mi of ephemeral storage
- A namespace-wide quota of 15 Gi of ephemeral storage

These changes will be rolled out in the PROD clusters on the following dates:

CHG0079608 - SILVER Cluster - July 7th @ 10:00 AM
CHG0079607 - EMERALD Cluster - July 7th @ 10:00 AM
CHG0079609 - GOLD Cluster - July 8th @ 10:00 AM
CHG0079610 - GOLDDR Cluster - July 9th @ 10:00 AM 

## How do I know if this affects me?

Most workloads will not be impacted. However, teams that use larger amounts of ephemeral storage may need to adjust their configurations.
You may be affected if your applications:

- Write significant data to directories not backed by PVCs (e.g., /tmp, /var/lib, or application data directories)
- Use emptyDir volumes for storing large datasets (e.g., dev/test databases)

## How to Check Your Usage

You can review ephemeral storage usage by inspecting your pods and checking disk usage in non-PVC directories. For example: `du -sh /path/to/directory`
Focus on:

- emptyDir volumes
- Temporary directories like /tmp

If you find high usage, consider moving that data to a Persistent Volume Claim (PVC).

## What actions do I need to take?

If your pods currently use more than 1 Gi of ephemeral storage, you will need to:

- Monitor your usage
- Update pod resource limits where necessary

Example pod configuration:

```text
resources:
  limits:
    cpu: 500m
    memory: 512Mi
    ephemeral-storage: 1Gi
```

*Check the MS Teams Openshift-alerts channel for the announcement of when the change is complete and check the health of your app.*

## Where can I find help?

If you run into trouble with these changes, please post your troubleshooting steps in Openshift-operations channel. Please make sure you include the cluster and namespace that you’re working on, as well as details about what problem(s) you're experiencing.
