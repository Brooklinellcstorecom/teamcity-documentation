[//]: # (title: TeamCity Cloud Cost Optimization)
[//]: # (auxiliary-id: TeamCity Cloud Cost Optimization)

TeamCity Cloud provides a quick way to get started with a fully managed CI solution that can be dynamically scaled as the number of builds increase or decrease. However, with this increased flexibility to scale-up comes the risk of additional costs through a higher consumption of build credits.

While TeamCity Cloud provides a number of built-in mechanisms to help you optimize the running time of your builds, there are numerous things you can do as a user of TeamCity Cloud to ensure you don&#39;t consume more resources and credits than needed.

In this article we will review a number of tips and suggestions to help you optimize your consumption of build credits, and in-turn lower your usage costs.

## Suggestions

Outlined below are a high-level summary of the suggestions, and we will delve deeper into each one further in this article.

1. Ensure each user populates their full list of VCS usernames.
2. Use the [Performance Monitor](performance-monitor.md) build feature to show statistics and spot bottlenecks.
3. Check build agent size suitability.
4. Use the Matrix view to get insights on the most intensive projects and build configurations.
5. Define [Quiet Period](configuring-vcs-triggers.md#Quiet+Period+Settings) settings on VCS Triggers.
6. Use [VCS Checkout Rules](vcs-checkout-rules.md).
7. Set time limits to prevent long running or hung builds.
8. Use [self-hosted build agents](managing-subscription-and-resources.md#Get+Self-Hosted+Build+Agents) for some of your builds.
9. Enable re-use of build results and incremental builds by using build chains.
10. Pass dependencies as artifacts to subsequent build configurations.
11. Prepay for build agents when using them extensively.
12. Review resources that are automatically renewed each month.
13. Right-sizing your subscription.

### Ensure each user populates their full list of VCS usernames

TeamCity Cloud subscriptions are based on the number of active committers. An active committer is essentially any developer that makes 10 or more VCS commits in a rolling 30-day period that end up being built by TeamCity (either via an automatic or manually triggered build). Once a user is classified as an active committer, they consume one of the committer slots in the subscription.

Active Committers are distinguished by the VCS usernames, so if an individual user has different usernames for multiple version control systems, it&#39;s important that TeamCity is aware of those usernames in order to correctly associate all of the user&#39;s VCS commits with one TeamCity user. If this isn&#39;t done, the individual user will consume one committer slot for each of their usernames.

You can make TeamCity aware of the extra VCS usernames by populating the [additional VCS usernames on the user&#39;s profile page](configuring-your-user-profile.md#Managing+Version+Control+Username+Settings). TeamCity Cloud allows you to define up to 3 different VCS usernames for each TeamCity user.

SCREENSHOT

By having each TeamCity user populate all their VCS usernames, this not only ensures you use the minimum number of committer slots, but it also enables users to correctly track their changes in the [Changes](viewing-your-changes.md) screen and see all of their personal builds on the Projects page.

### Use the Performance Monitor build feature to show statistics and spot bottlenecks

To ensure your builds are running on suitably sized hardware, you can add the [Performance Monitor](performance-monitor.md) build feature to your build configurations. Various usage statistics will then be captured while the build is running, including CPU, disk I/O, and memory consumption.

This allows you to spot potential bottlenecks by analysing the results after a build has completed. An example of this is shown below, where the build agent&#39;s memory peaks at 95% midway through the build. This could indicate a larger build agent may be required.

SCREENSHOT

If you do need to use a build agent of a higher specification, you can define specific requirements on the [Agent Requirements](agent-requirements.md) screen under the build configuration. For example, you could define a minimum amount of memory (RAM) by using the parameter `teamcity.agent.hardware.memorySizeMb`. Builds under this build configuration will only run on a build agent that has a minimum of 30GB RAM: 

SCREENSHOT

### Check build agent size suitability

It may be tempting to just assign all of your builds to run on highly performant cloud build agents (e.g. Linux Large), when in reality some of your builds may not leverage the full capabilities of the assigned cloud build agent. A good example of this is when running a process that doesn&#39;t utilize all CPU cores of a large instance. By switching that build to run on a smaller instance with a lower number of CPU cores, you can help lower your build credit consumption.

If the build steps within a build configuration have minimal CPU and memory requirements it makes sense to run those parts of your projects and build chains on smaller build agents, and reserve larger build agents for more resource intensive build configurations. If you use a build chain, you can assign each part of your build chain to run on different sized build agents by defining _Agent Requirements_ on each build configuration (as descried above).

To help verify the right size of cloud build agent to use, the _Performance Monitor_ build feature (discussed in the previous section) can provide you with insights into the usage of system resources throughout the entire build.

### Use the Matrix view to get insights on the most intensive projects and build configurations

The [Matrix](viewing-agents-workload.md#Load+Statistics+Matrix) in TeamCity is a tab available from the Agents screen that offers a bird&#39;s-eye view of all projects and build configurations, and shows totals of their overall build time across all build agents during a specific timeframe.

If you have many projects or build configurations, the Matrix view provides a simple way to spot the most build-intensive projects. This can help you decide which types of build agents are best to run your builds, or to perhaps consider enabling _Quiet Period_ settings on builds that run often to help limit the amount of overall build time they consume.

SCREENSHOT

### Define Quiet Period settings on VCS Triggers

If multiple commits are made to a repository in a short period of time, this can sometimes lead to separate builds being run - one build for each of those commits. Over time this can add up to an excessive consumption of build credits, when many of these commits could be combined together under a single build.

TeamCity makes this simple to accomplish by specifying [Quiet Period](configuring-vcs-triggers.md#Quiet+Period+Settings) settings on the VCS Trigger. A quiet period is a timeframe that TeamCity maintains between the moment the last VCS change is detected and a build is added into the queue. If new VCS changes are detected in the build configuration within the defined period, the quiet period starts over from the new change detection time. The build is added into the queue only if there were no new VCS changes detected within the quiet period.

In this example, a quiet period of 300 seconds (5 minutes) has been defined on the VCS Trigger: 

SCREENSHOT

One important note regarding the use of Quiet Period settings - if you have also selected the option to trigger a build on each check-in, then the quiet period settings will be ignored.

When multiple commits are combined together in one build, you are still able to see a full list of the changes in the build by going to the [Changes](working-with-build-results.md#Changes) tab in the build, even if the commits were made by several developers. In addition, if a build fails, you can cross-reference the error or failure with the list of changes to see who may have contributed to the failure.

TeamCity also features an [Investigations Auto Assigner](investigations-auto-assigner.md) build feature to automatically suggest assigning a failure to a particular committer based on a number of built-in heuristics.

### Use VCS Checkout Rules

If a build is only required when a subset of files or directories are changed in your repository, you may want to look at specifying [VCS checkout rules](vcs-checkout-rules.md) to limit unnecessary builds. If a commit does not match any of the checkout rule patterns on the VCS root, TeamCity will ignore it.

### Set time limits to prevent long running or hung builds

If a build ever hangs for some reason, perhaps because of an unhandled exception or a failed process on the cloud build agent, it could be left running until reaching the default TeamCity Cloud server timeout of 120 minutes, causing you to consume build credits for the full 120 minutes.

If you know your build normally takes 3 minutes to run, you may want to configure TeamCity to automatically fail the build if it runs longer than 5 minutes. You can do this easily through the [Failure Conditions](build-failure-conditions.md) screen within the build configuration. By default this is set to 0 minutes, which means the global server timeout of 120 minutes would apply.

By restricting the number of minutes a build can run, you can prevent hung builds from excessively consuming your build credits.

SCREENSHOT

### Use self-hosted build agents for some of your builds

In addition to the JetBrains-provided cloud build agents, you have the option to connect [self-hosted build agents](managing-subscription-and-resources.md#Get+Self-Hosted+Build+Agents) to your TeamCity Cloud server. These self-hosted agents could be machines running on your internal corporate network or private cloud environment. You could also configure TeamCity to use something like AWS Spot instances to benefit from spare EC2 capacity for less than the on-demand pricing.

As long as your self-hosted agents are able to access the internet and resolve your TeamCity Cloud domain, you don&#39;t need to open up any inbound ports as TeamCity build agents use a [unidirectional agent-to-server connection](install-and-start-teamcity-agents.md#Agent-Server+Data+Transfer) via the polling protocol, where the build agent establishes an HTTPS connection to the TeamCity Cloud server and polls the server periodically for server commands.

You are able to connect an unlimited number of self-hosted build agents to TeamCity Cloud, and redeem build credits depending on how many concurrent builds you want to run on those self-hosted build agents during each month (20,000 build credits per concurrent self-hosted build, per month). This means you could connect hundreds of self-hosted build agents, and if (for example) you redeemed 100,000 build credits for five self-hosted build agent slots in a month, this would allow you to run builds on any five of those self-hosted build agents concurrently.

There are no per-minute charges for self-hosted builds, so if you have some very long running builds or builds that require custom tools not available on our cloud build agents, you can reserve some self-hosted build agents for those more complex builds, and just use the cloud build agents for shorter or less complex builds.

### Enable re-use of build results and incremental builds by using build chains

Rather than having a single large build configuration with many build steps, the build configuration could be split into separate (smaller) build configurations, and linked together in a [build chain](build-chain.md) (also referred to as a build pipeline). For example, if a single build configuration currently contains steps for building, testing, and deploying a solution to a staging environment, you may choose to create three build configurations: Build, Test, and Deploy to Staging, and move each of the build steps into their own respective build configurations.

By defining snapshot dependencies on each of the build configurations, this establishes the build chain by linking the build configurations together.

A build chain in TeamCity enables incremental builds and re-use of build results. So if, for example, the &quot;Build&quot; and &quot;Test&quot; build configurations complete successfully, but the &quot;Deploy to Staging&quot; fails due to a temporary connection issue with the external staging environment. Rather than re-running the entire build chain from scratch (and consuming more build credits), TeamCity will re-use the results from &quot;Build&quot; and &quot;Test&quot; (assuming there are no new VCS changes), and start the build chain from &quot;Deploy to Staging&quot;. This reduces build credit consumption while also shortening the overall time it takes to deploy a project.

### Pass dependencies as artifacts to subsequent build configurations

If you have multiple build configurations in a build chain that all use the same dependencies (such as a large number of npm packages), rather than running npm install on each build agent for each of those build configurations, the npm packages folder could instead be zipped up on the very first build configuration and stored as an artifact in TeamCity, for use by future builds.

You can also configure a build configuration to have an artifact dependency on itself (specifically on the last finished build) - so you could zip the dependencies at the end of the build, upload as a build artifact, and create an artifact dependency on the previous build in the same build configuration.

This can be accomplished through [artifact dependencies](build-dependencies-setup.md#Artifact+Dependencies). Depending on the number (and size) of the packages, this can help reduce time on subsequent builds in the build chain and prevent future builds from downloading all packages from scratch.

In this example, a new artifact dependency is being added to a build configuration that will automatically transfer the zipped npm packages from a previous build in the build chain to the current build agent:

<img src="new-artifact-dependency-dialog.png" alt="Add New Artifact Dependency dialog" width="460"/>


### Prepay for build agents when using them extensively

If you have some particularly long running builds or you find yourself using a single type of cloud build agent for more than 125 hours in a month, you can prepay for one or more instances of that type of cloud build agent, and avoid any other per-minute fees. This is accomplished by redeeming a batch of credits each month.

For example:

- **Linux Small** - 75,000 credits per month, per concurrent build
- **Linux Medium** - 150,000 credits per month, per concurrent build
- **Linux Large** - 300,000 credits per month, per concurrent build
- **Windows Medium** - 300,000 credits per month, per concurrent build

So if you currently reach a maximum build concurrency of 5 Linux Small cloud build agents, and these agents run builds for a combined total of 2,500 hours over the month, using our per-minute pricing this would equate to a total of 1,500,000 build credits for a month. If you were to prepay for those 5 cloud build agents, your cost would drop down to a flat-rate fee of 375,000 credits for the same one-month period.

While this offers a big saving on build credit consumption, it is important to note this comes at the trade-off of decreased concurrency - i.e. if you prepay for those 5 Linux Small cloud build agents, only a maximum of 5 of those types of cloud build agents can be running concurrently with the prepaid rate. Any further concurrent builds on the same types of agents will revert to the per-minute pricing.

### Review resources that are automatically renewed each month

The Subscription &amp; Resources screen in TeamCity Cloud enables you to redeem credits for additional resources when needed, such as extra committer slots, data storage, pre-paid monthly agents, and concurrent builds on self-hosted agents. When you increase any of these resources, a certain number of credits are immediately deducted from your available balance for the current month.

For example, one additional concurrent build on a self-hosted agent costs 20,000 credits per month. If you redeem credits for this extra resource on the first day of the month, a deduction of 20,000 credits is made. Or if you redeem credits for the extra resource at the middle of the month, the deduction would be prorated at ~10,000 credits for the remainder of the month.

It&#39;s important to note if you don&#39;t decrease these additional resources prior to the end of the month, the same resources will be applied the following month, and the applicable credits will be deducted for those resources for an entire one-month period. So if you only require extra resources temporarily (e.g. during a busier period), and you want to avoid redeeming credits for resources that you may not use the following month, we recommend decreasing the additional resources prior to the end of the current month.

You can even decrease the additional resources right after you&#39;ve increased them (in case you forget to do it later), and the additional resources will only stay active through the remainder of the current month.

SCREENSHOT

### Right-sizing your subscription

When you commence a new TeamCity Cloud subscription, or when it&#39;s time to renew, it&#39;s a good idea to closely review how many resources (build credits) are allocated to your TeamCity Cloud instance based on the number of committers in your subscription, and in doing so check whether you have an excessive amount of resources.

If you have a team of 50 developers regularly making commits (which would equate to 50 active committers), a subscription of this size would look as follows:

**TeamCity Cloud subscription with 50 committers**

- **400,000 build credits** - provides 333 hours of build time on Linux Medium cloud agents
- **2TB storage, 10TB data transfer per month**

Based on the example above, if you know you&#39;re likely to need fewer than 333 hours of build time on Linux Medium cloud agents, you may want to consider lowering the number of committers in your subscription, and instead redeeming some of your remaining credits for additional committer slots.

For example, if you have a requirement of up to 150 hours of build time a month (instead of 333 hours), you could structure your subscription with fewer committers and reduce your subscription cost:

**TeamCity Cloud subscription with 39 committers (and redeeming credits to add 11 extra committers)**

- **312,000 build credits** - you can split these credits and redeem up to 180,000 credits for 150 hours of build time on Linux Medium cloud agents, and redeem the remaining 132,000 credits for 11 additional committer slots, which tops up the total number of committers to 50
- **1.56TB storage, 7.8TB data transfer per month**

If you know how much build time you require during a typical month, the example above shows one way you can optimize your costs.

Conversely, if you have an insufficient number of resources in your subscription, you may need to purchase additional build credits to top-up your account. This is more cost effective than artificially increasing the committers on your subscription just to gain extra build credits, as you are paying for the committer slot, data storage, and data transfer when adding committers to your subscription. Unlike the build credits included in your subscription which reset at the end of each month, additionally purchased build credits rollover month-to-month if not fully used.
