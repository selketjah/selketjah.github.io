---
layout: post
title: Adding a project to a solution file manually
tags:
- Visual Studio
---

To add a project to your solution manually, you need to do two things:
* add the project itself
* add the project to the ProjectConfigurationPlatforms

# Adding a project to a solution 

1. Add the project itself

```
Project("{project type GUID}") = "<Project name>", "<project file location>", 
    "{<Unique project GUID>}"
EndProject
```

[Yvan Rodrigues](https://www.codeproject.com/script/Membership/View.aspx?mid=1740717) was nice enough to post the entire list in 2016 online for us!
You can find it [here](https://www.codeproject.com/Reference/720512/List-of-Visual-Studio-Project-Type-GUIDs)

2. Add the project to the ProjectConfigurationPlatforms

```
{<Unique project GUID>}.Debug|Any CPU.ActiveCfg = Debug|Any CPU
{<Unique project GUID>}.Debug|Any CPU.Build.0 = Debug|Any CPU
{<Unique project GUID>}.Release|Any CPU.ActiveCfg = Release|Any CPU
{<Unique project GUID>}.Release|Any CPU.Build.0 = Release|Any CPU
```

# Example

This is an example of a F# library project being added to the solution.
As far as I can tell, it is not required that the GUIDs are in uppercase, it is just my personal preference.

1. Project
```
Project("{F2A71F9B-5D33-465A-A702-920D77279786}") = "QuizBot", "src\QuizBot\QuizBot.fsproj", "{4A0B663D-C0C3-491F-9B07-2DACE25DB816}"
EndProject
```

2. ProjectConfigurationPlatforms
```
{4A0B663D-C0C3-491F-9B07-2DACE25DB816}.Debug|Any CPU.ActiveCfg = Debug|Any CPU
{4A0B663D-C0C3-491F-9B07-2DACE25DB816}.Debug|Any CPU.Build.0 = Debug|Any CPU
{4A0B663D-C0C3-491F-9B07-2DACE25DB816}.Release|Any CPU.ActiveCfg = Release|Any CPU
{4A0B663D-C0C3-491F-9B07-2DACE25DB816}.Release|Any CPU.Build.0 = Release|Any CPU
```