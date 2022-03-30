# PSChristmasTree

<img src="logo.svg" width="180">

Table of Contents
=================

<!-- toc -->

- [Introduction](#introduction)
- [Usage](#usage)
- [Installation](#installation)
    + [From PowerShell Gallery](#from-powershell-gallery)
      - [Supported PowerShell Versions and Platforms](#supported-powerShell-versions-and-platforms)
    + [From Source](#from-source)
      - [Requirements](#requirements)
      - [Steps](#steps)
      - [Tests](#tests)
- [Contributions are welcome](#contributions-are-welcome)
- [Creating a Release](#creating-a-release)
- [Code of Conduct](#code-of-conduct)

<!-- tocstop -->

Introduction
============
PSChristmasTree is a animated Christmas tree on Powershell. 

PSChristmasTree displays a christmas tree with decorations that lights up in all colors (by default).

![preview](./docs/img/preview.gif?raw=true)

PSChristmasTree has many parameters to customize it including "We Wish You a Merry Christmas" carol that can be played during the display

[Back to ToC](#table-of-contents)

Usage
======================
### Basic

```powershell
Show-PSChristmasTree
```
### Advanced

```powershell
Show-PSChristmasTree [[-AnimationLoopNumber] <Int32>] [[-AnimationSpeed] <Int32>] [[-Colors] <Array>]
[[-Decorations] <Hashtable>] [[-PlayCarol] <Int32>] [[-UICulture] <String>] [<CommonParameters>]
```

[Back to ToC](#table-of-contents)

Installation
============

### From PowerShell Gallery
```powershell
Install-Module -Name PSChristmasTree
```

#### Supported PowerShell Versions and Platforms

- Windows PowerShell 5.0 or greater
- PowerShell Core 7.0.3 or greater on Windows/Linux/macOS

### From Source

#### Steps
* Obtain the source
    - Download the [latest release](https://github.com/Sofiane-77/PSChristmasTree/releases/latest) OR
    - Clone the repository (needs git)
    ```powershell
    git clone https://github.com/Sofiane-77/PSChristmasTree
    ```
    
* Navigate to the source directory
    ```powershell
    cd path/to/PSChristmasTree
    ```
    
* Import the module

    ```powershell
    Import-Module ./PSChristmasTree/PSChristmasTree.psd1
    ```
    
* Building

    You will need `PowerShell Core 7.0 or greater on Windows/Linux/macOS` to build the module:
    * The default build is for the currently used version of PowerShell
    ```powershell
    Invoke-Build Build
    ```
    
* Rebuild documentation since it gets built automatically only the first time
    ```powershell
    .\build.ps1 -Documentation
    ```
    
* Build all versions (PowerShell v3, v4, v5, and v6) and documentation
    ```powershell
    .\build.ps1 -All
    ```
    
* Import the module
    ```powershell
    Import-Module (Get-ChildItem -Path .\Build\* -Recurse -Include PSChristmasTree.psd1)
    ```

To confirm installation: run `Get-Help Show-PSChristmasTree -Full` in the PowerShell console to get the list of all parameters.

#### Tests
Pester Tests are located in `path/to/PSChristmasTree/Tests` folder.

* In the root folder of your local repository, run:

```powershell
Invoke-Build Init, Test
```

[Back to ToC](#table-of-contents)

Contributions are welcome
==============================

There are many ways to contribute:

1. Open a new bug report, feature request or just ask a question by opening a new issue [here]( https://github.com/Sofiane-77/PSChristmasTree/issues/new/choose).
2. Participate in the discussions of [issues](https://github.com/Sofiane-77/PSChristmasTree/issues), [pull requests](https://github.com/Sofiane-77/PSChristmasTree/pulls) and verify/test fixes or new features.
3. Submit your own fixes or features as a pull request but please discuss it beforehand in an issue if the change is substantial.
4. Submit test cases.

Read through our [contributing guidelines](https://github.com/Sofiane-77/PSChristmasTree/blob/main/.github/CONTRIBUTING.md) to learn about our submission process, coding rules and more.

[Back to ToC](#table-of-contents)

Creating a Release
================

- Update changelog (`changelog.md`) with the new version number and change set. When updating the changelog please follow the same pattern as that of previous change sets (otherwise this may break the next step).
- Import the ReleaseMaker module and execute `New-Release` cmdlet to perform the following actions.
  - Update module manifest (engine/PSScriptAnalyzer.psd1) with the new version number and change set
  - Update the version number in `Engine/Engine.csproj` and `Rules/Rules.csproj`
  - Create a release build in `out/`

```powershell
    PS> Import-Module .\Utils\ReleaseMaker.psm1
    PS> New-Release
```

- Sign the binaries and PowerShell files in the release build and publish the module to [PowerShell Gallery](www.powershellgallery.com).
- Draft a new release on github and tag `main` with the new version number.

[Back to ToC](#table-of-contents)

Code of Conduct
===============
Help us keep PSChristmasTree open and inclusive. Please read and follow our [Code of Conduct](https://github.com/Sofiane-77/PSChristmasTree/blob/main/.github/CODE_OF_CONDUCT.md). For more information, contact [PSChristmasTree@caramail.com](mailto:PSChristmasTree@caramail.com) with any additional questions or comments.

[Back to ToC](#table-of-contents)



#### Requirements

* [InvokeBuild module, available on PowerShell Gallery](https://github.com/nightroman/Invoke-Build)
* PowerShell Core 7.0 or greater on Windows/Linux/macOS
