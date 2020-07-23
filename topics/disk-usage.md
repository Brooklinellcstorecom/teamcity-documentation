[//]: # (title: Disk Usage)
[//]: # (auxiliary-id: Disk Usage)
TeamCity analyses disk space occupied by builds on the server machine and provides the __Disk Usage__ report. To see the report, open __Administration| Disk Usage__.

<img src="DiskUsage.png" width="527" alt="Disk usage"/>

The report contains information on the total free disk space and the amount of space taken by build artifacts and build logs. The default location for this directories is \<[TeamCity Data Directory](teamcity-data-directory.md)\>/system. If build logs and artifacts directories are [located on different disks](teamcity-data-directory.md#Recommendations+as+to+choosing+Data+Directory+Location), free space is reported for each of the disks. The report also displays [pinned builds](pinned-build.md) if available, and the space taken by their logs and artifacts.

By default, the report displays data on the builds run from build configurations grouped by projects. You can choose to view the ungrouped list of build configurations or to show archived projects if required using the corresponding checkboxes. You can sort the information by clicking the column name.

The report allows you to see which projects consume most of disk space and configure the [clean-up rules](clean-up.md); the link to the report is also available from the build history clean\-up page. This page also displays disk usage information for the selected project or build configuration when managing [clean-up rules](clean-up.md) in the __Configure Clean\-up__ section.

You can also see which configurations produce [large build logs](server-health.md#Configurations+with+Large+Build+Logs) and adjust the settings accordingly.

The report is automatically updated when a new build is run or removed: only the data pertaining to this build is analyzed and the corresponding information is reflected in the report. The report is completely updated when TeamCity performs a full disk scan: by default, after a build history clean\-up is run. You can force TeamCity to scan the disk on demand using the __Rescan now__ button, but it may be time\-consuming.

The Disk Usage report allows going deeper in the build history of a specific build configuration and showing some additional statistics for the builds of this configuration. The [clean-up](clean-up.md) rules for this build configuration are also listed allowing you to adjust the settings based on the data displayed:

<img src="DiskUsageDetails.png" width="431" alt="Disk usage in details"/>
