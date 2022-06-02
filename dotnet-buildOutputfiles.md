---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Copy required files to build output folder
{: #copy_files_build_output}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

You can use either the project.json tooling or MSBuild tooling to ensure that your app has all of its required files in the build output folder.
{: shortdesc}


## Use project.json tooling
{: #projectjson}

Add the following property to the `buildOptions` section of the `project.json` file.

```json
  "copyToOutput": {
    "include": [
      "wwwroot",
      "Areas/**/Views",
      "Views",
      "appsettings.json"
    ]
  }
```
{: codeblock}

In Startup.cs `Startup` method, remove the following line.

```json
  .SetBasePath(env.ContentRootPath)
```
{: codeblock}

In Program.cs `Main` method, remove the following line.

```json
  .UseContentRoot(Directory.GetCurrentDirectory())
```
{: codeblock}

These changes should allow the .NET CLI to find your app's `Views` as they will now be copied to the build output when the `dotnet run` command executes.  If your app has any other files, such as JSON configuration files, that are required at runtime, also add the files to the `include` section of `copyToOutput` in the `project.json` file for your project.

## Use MSBuild tooling
{: #msbuild}

Add a `<Content>` element to the `<ItemGroup>` element of your `.csproj` file.

```text
  <ItemGroup>
    <Content Include="wwwroot/**/*;Areas/**/Views/*;Views/*;appsettings.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      <CopyToPublishDirectory>Always</CopyToPublishDirectory>
    </Content>
  </ItemGroup>
```
{: codeblock}

In the `Startup.cs` `Startup` method, remove the following line.

```text
  .SetBasePath(env.ContentRootPath)
```
{: codeblock}

In the `Program.cs` `Main` method, remove the following line.

```text
  .UseContentRoot(Directory.GetCurrentDirectory())
```
{: codeblock}

These changes allow the .NET CLI to find your app's `Views` as they are copied to the build output when the `dotnet publish` command executes.  If your app has any other files, such as JSON configuration files, that are required at runtime, also add those to the `Include` property of the `Content` element in the `.csproj` file for your project, separated by semi-colons.


