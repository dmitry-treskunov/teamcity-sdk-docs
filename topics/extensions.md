[//]: # (title: Extensions)
[//]: # (auxiliary-id: Extensions.html)



Extension in TeamCity is a point where standard TeamCity behavior can be changed. There are three marker interfaces for TeamCity extensions:

* [`jetbrains.buildServer.serverSide.ServerExtension`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/ServerExtension.html)
* [`jetbrains.buildServer.agent.AgentExtension`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/agent/AgentExtension.html)
* [`jetbrains.buildServer.TeamCityExtension`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/TeamCityExtension.html)

Extension interface implements one of these marker interfaces. __ServerExtension__ and __AgentExtension__ are used to mark server and agent side extensions correspondingly. __TeamCityExtension__ is the base interface for __ServerExtension__ and __AgentExtension__. Thus you can take a list of all available extensions in TeamCity by taking a look at interfaces which extend these marker interfaces.

### Registering custom extension

There are two ways to register custom extension:

1. define a bean in the Spring context which implements extension interface, in this case your extension will be loaded automatically
2. register your extension at runtime in the [`jetbrains.buildServer.ExtensionHolder`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/ExtensionHolder.html) service (can be obtained by Spring autowiring feature)
## Available extensions

__Server\-side extensions__

<table><tr>

<td>

Extension


</td>

<td>

Since


</td>

<td>

Description


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.TextStatusBuilder`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/TextStatusBuilder.html)

</td>

<td>

3.0


</td>

<td>

Allows customizing text status line of the build, i.e. the build description which usually contains text like "Tests passed: 234, failed: 4 (2 new)".


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.TriggeredByProcessor`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/TriggeredByProcessor.html)

</td>

<td>

4.0


</td>

<td>

Similar to __TextStatusBuilder__ but affects "Triggered by" value shown in the UI.


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.FailedTestOutputFormatter`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/FailedTestOutputFormatter.html)

</td>

<td>

4.0


</td>

<td>

This extension allows applying custom formatting to test stacktrace to be shown in the UI.


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.buildDistribution.StartBuildPrecondition`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/buildDistribution/StartBuildPrecondition.html)

</td>

<td>

4.5


</td>

<td>

Allows defining preconditions for starting a build on an agent, that is, you can instruct TeamCity to delay a build till some condition is met.


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.GeneralDataCleaner`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/GeneralDataCleaner.html)

</td>

<td>

2.0


</td>

<td>

This extension is called when the cleanup process is going to finish, plugins can clean their data with the help of this extension.


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.DataCleaner`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/DataCleaner.html)

</td>

<td>

2.0


</td>

<td>

This extension is called when the cleanup process is going to clean up data of a build, plugins can remove their data associated with this build with help of this extension.


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.ParametersPreprocessor`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/ParametersPreprocessor.html)

</td>

<td>

3.0


</td>

<td>

Allows modifying build parameters right before they are sent to an agent.


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.parameters.BuildParametersProvider`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/parameters/BuildParametersProvider.html)

</td>

<td>

5.0


</td>

<td>

Allows adding additional parameters available for a build. It differs from __ParametersPreprocessor__ in the way that the parameters added by __BuildParametersProvider__ will be available in a popup showing available parameters, and will be considered when requirements are calculated.


</td></tr><tr>

<td>

[`jetbrains.buildServer.serverSide.parameters.ParameterDescriptionProvider`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/serverSide/parameters/ParameterDescriptionProvider.html)

</td>

<td>

5.0


</td>

<td>

Provides a human\-readable description for a parameter, see also __BuildParametersProvider__.


</td></tr><tr>

<td>

[`jetbrains.buildServer.messages.serviceMessages.ServiceMessageTranslator`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/messages/serviceMessages/ServiceMessageTranslator.html)

</td>

<td>

4.0


</td>

<td>

Translator for specific type of service messages.


</td></tr><tr>

<td>

[`jetbrains.buildServer.usageStatistics.UsageStatisticsProvider`](http://javadoc.jetbrains.net/teamcity/openapi/current/jetbrains/buildServer/usageStatistics/UsageStatisticsProvider.html)

</td>

<td>

6.0


</td>

<td>

Provides a custom usage statistics.


</td></tr></table>

  __See also:__

__Extending TeamCity__: [Developing TeamCity Plugins](https://confluence.jetbrains.com/display/TCD18/Developing+TeamCity+Plugins) | [Web UI Extensions](web-ui-extensions.md)
