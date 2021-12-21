[//]: # (title: TeamCity 2021.12 Release Notes)
[//]: # (auxiliary-id: TeamCity 2021.12 Release Notes)

__Build: 107109__  
__22 December 2021__

### Feature

[**TW-48449**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-48449) — Support Cloud profiles in Kotlin DSL project  
[**TW-73796**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73796) — Allow to create a build problem for every match found with &quot;Fail Build on Specific Text&quot; failure condition  
[**TW-73101**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73101) — Publish a build status to the Merge request in JetBrains Space  
[**TW-70296**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-70296) — Add support for Space merge requests to Pull requests build feature  
[**TW-73161**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73161) — UI to manage agent pool projects  
[**TW-66588**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-66588) — Provide a way to automatically choose some parent project as scope when assigning an investigation or muting tests  
[**TW-73967**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73967) — Report the build status in the head commit of the Space Merge request  
[**TW-73167**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73167) — Single change page. No &quot;Show projects hierarchy&quot; option on Builds tab  
[**TW-73691**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73691) — Disallow adding more builds in the build queue using REST requests if the build queue is too large

### Usability Problem

[**TW-69011**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-69011) — UI to edit agent pools  
[**TW-29414**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-29414) — Include name of the deleted object into &quot;Are you sure you want to delete this project&quot; confirmation  
[**TW-61639**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-61639) — Improve Build overview tabs placement on expanded build area  
[**TW-74090**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74090) — Need to make more visible that there are several builds behind this configuration  
[**TW-74056**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74056) — Impossible to navigate back from Server Health page  
[**TW-59968**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-59968) — No need to change projects list in sidebar if the search field is selected and empty. Only after typing the letters  
[**TW-68390**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-68390) — Build log search: make Next button search for new results starting from the place user has clicked  
[**TW-69949**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-69949) — Show duration for currently running stages on Build log  
[**TW-68366**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-68366) — Build log search: Next result button is disabled when the last result is reached  
[**TW-73875**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73875) — Assign agents/projects dialog is reloaded every time when any pool is changed.

### Bug

[**TW-72962**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-72962) — Deadlock found when trying to get lock (FailedTestsStorageImpl.markTestFailed)  
[**TW-74253**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74253) — Agent pool agents tab: remove redundant headers  
[**TW-73852**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73852) — Wrong code coverage for kotlin files  
[**TW-73989**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73989) — Update sbt launcher to 1.5.5  
[**TW-74161**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74161) — Allow to disable/enable integration with Space merge requests without restart of server  
[**TW-63121**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-63121) — Max Agents parameter is not displayed in the agents pool page  
[**TW-74287**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74287) — Perforce Shelve Trigger&#39;s vcsRoot.\&lt;ID\&gt;.shelvedChangelist parameter is not passed to snapshot dependencies  
[**TW-73874**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73874) — GraphQL API: make ids globally unique  
[**TW-71862**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-71862) — Display the number of projects that cannot be seen by user due to lack of permissions on GraphQL agent pool projects tab.  
[**TW-73772**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73772) — Favorite builds are sometimes not returned even though they are inside lookupLimit  
[**TW-73984**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73984) — Agent pool projects page: it should not be possible to remove a project, assigned only with the default pool, and the project pool, from the default pool  
[**TW-71874**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-71874) — Renaming/moving/archiving of projects should be reflected in GraphQL agent pool projects tab  
[**TW-73766**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73766) — Provide the limit for number of symbols in Agent Pool name in Experimental UI.  
[**TW-74088**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74088) — Build may be canceled when the server is temporarily unavailable  
[**TW-73973**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73973) — GraphQL API: add the `excludedCount` prop to the `AgentPoolProjectsConnection` type  
[**TW-73911**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73911) — Deadlock on attempt to store a new metadata storage key id  
[**TW-73138**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73138) — Agents parameters subtabs links leads to old UI  
[**TW-74040**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74040) — Investigations auto assigner should not automatically assign investigations on setUp/tearDown methods  
[**TW-73217**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73217) — Missing DSL for coverage parameters in IntelliJ IDEA Project runner  
[**TW-73939**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73939) — Agent pools. Images without running instances should be displayed on Agent Pool page in Experimental UI.  
[**TW-73965**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73965) — TeamCity unexpectedly closes the test with suite, so test names lose suite names  
[**TW-66332**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-66332) — Rendering SGR parameters in ANSI sequences in build log in new UI  
[**TW-73912**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73912) — Absence of an index on test\_metadata(key\_id) slows down startup and can cause failure to start if connection timeout is configured  
[**TW-73917**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73917) — IDEA&#39;s remote run fails to determine related run configurations  
[**TW-73211**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73211) — Missing DSL for some parameters in .Net runner  
[**TW-73773**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73773) — Linux TeamCity agent running under WSL on windows detects .NET SDKs and runtimes installed on the windows host  
[**TW-73218**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73218) — Missing DSL for Script Argument parameter in PowerShell runner  
[**TW-73213**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73213) — Missing DSL for some parameters in Docker runner  
[**TW-73215**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73215) — Missing DSL for Distinguish fields parameter in Duplicates finder (Java) runner  
[**TW-72760**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-72760) — Password/access token is not extracted in case when separate VCS root is created using the Azure DevOps OAuth connection  
[**TW-72763**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-72763) — Azure DevOps OAuth Connection: Handle errors that happened during project creation  
[**TW-72876**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-72876) — Do not display Perforce personal build section in Custom Run dialog for user without &quot;Change build source code with a custom patch&quot; permission.

### Cosmetics

[**TW-71876**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-71876) — Display zero counter if Agents pool contains no agents in Experimental UI.  
[**TW-72526**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-72526) — Agents pools. Provide correct tooltip on assigned projects tab.  
[**TW-73006**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73006) — Scrollbars always show on agents page in new UI

### Performance Problem

[**TW-74229**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74229) — Drop Edge 18 support  
[**TW-74050**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74050) — Interlocking between UI threads and a thread which is applying changes from the versioned settings  
[**TW-56119**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-56119) — Improve Git getCurrentState operation in case when several threads attempt to perform ls-remote against the same repository  
[**TW-73732**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73732) — Build agents messages processing delay because of global synchronization in TestMetadataStorage

### Task

[**TW-74357**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74357) — Remove log4j classes from webapps/ROOT/WEB-INF/plugins/jps-tool/agent/jps.zip!lib/scala-plugin/incremental-compiler.jar  
[**TW-73228**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73228) — Bundle IntelliJ IDEA 2021.2.3 with TeamCity 2021.2  
[**TW-74333**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74333) — Update Kotlin DSL to version 2021.12  
[**TW-74153**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74153) — Remove version from TeamCity Cloud servers footer  
[**TW-74160**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-74160) — Enable integration with Space merge requests by default  
[**TW-73659**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73659) — VCS updater: handle the case when update settings from VCS takes too much time  
[**TW-73980**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73980) — Build log controller: allow searching from the end  
[**TW-74007**](https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FTW-73980) — Consider replacing usages of `ServletResponse#getWriter` with getOutputStream in controllers which can generate a lot of data