Hi @all, your attention is needed! 

**What is happening?**

Upgrade OpenShift Pipelines to 1.18

Upgrading the Pipelines operator (Tekton) from 1.16 to 1.18

**When?**

Tues July 8th at 10am Silver and Emerald
Wed July 9th at 10am Gold
Thur July 10th at 10am Gold DR

**Will there be an impact on the Platform apps?**

No impact to running apps. Breaking changes to Pipelines.

**Do I need to do anything?**

ClusterTasks are removed in 1.17 and your Pipeline will need to be updated to instead use the Tasks from the `openshift-pipeline` namespace. The version of the tasks is also newer and may need some changes. One notable example is that the `git-clone` param names have changed from lowercase to uppercase.

Old

```yaml
    - name: fetch-repo
      displayName: "Fetch GitHub Repo"
      params:
        - name: url
          value: "$(params.git-repo-url)"
        - name: revision
          value: "$(params.pullreq-sha)"
      taskRef:
        kind: ClusterTask
        name: git-clone
      workspaces:
        - name: output
          workspace: source-code
```

New

```yaml
    - name: fetch-repo
      displayName: "Fetch GitHub Repo"
      params:
        - name: URL
          value: "$(params.git-repo-url)"
        - name: REVISION
          value: "$(params.pullreq-sha)"
      taskRef:
        resolver: cluster
        params:
          - name: kind
            value: task
          - name: name
            value: git-clone
          - name: namespace
            value: openshift-pipelines
      workspaces:
        - name: output
          workspace: source-code
```

**Check the #devops-alert channel for the announcement of when the change is complete and check the health of your app.**

**Where do I get help if my app doesn't work after the change is complete?**

Each Platform application has an assigned DevOps Specialist within the Ministry so contact them first. If you don't know who your assigned DevOps Specialist, check with the app's Product Owner.

The DevOps Specialist will troubleshoot the issue with the app and if they need help, they will reach out to the Platform Services Team and the Developer Community in RocketChat as per these [RocketChat Channel Use Guidelines](https://developer.gov.bc.ca/docs/default/component/bc-developer-guide/rocketchat/rocketchat-channel-descriptions/).
