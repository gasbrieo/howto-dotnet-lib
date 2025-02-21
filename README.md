# HowTo.Net.Lib

![Sonar Quality Gate](https://img.shields.io/sonar/quality_gate/gasbrieo_howto-dotnet-lib?server=https%3A%2F%2Fsonarcloud.io&style=for-the-badge)
![Sonar Coverage](https://img.shields.io/sonar/coverage/gasbrieo_howto-dotnet-lib?server=https%3A%2F%2Fsonarcloud.io&style=for-the-badge)
![GitHub last commit](https://img.shields.io/github/last-commit/gasbrieo/howto-dotnet-lib?style=for-the-badge)
![GitHub Release](https://img.shields.io/github/v/release/gasbrieo/howto-dotnet-lib?style=for-the-badge)

## Overview

**HowTo.Net.Lib** serves as a template for creating and publishing a .NET library to NuGet, with CI/CD workflows for SonarCloud analysis and NuGet package publishing.

## Features

- GitHub Actions Workflow
  - Static analysis with SonarCloud
  - Automated publishing to NuGet

- Basic .NET Project Structure
  - Sample class library
  - Example class
  - Unit test project

## Getting Started

### Prerequisites

- A [NuGet](https://www.nuget.org) account.
- A [SonarCloud](https://sonarcloud.io/) account.

### Setup

1. Clone this repository:

`git clone https://github.com/gasbrieo/howto-dotnet-lib.git`

2. Install the template globally:

`dotnet new install ./`

3. Create a new project using the template:

`dotnet new howto-dotnet-lib -n MyLibName`

This will generate a new project with the specified name and pre-configured settings.

4. Update the following Package Info in the class library csproj:

```
<PropertyGroup Label="Package info">
	<PackageId>HowTo.Net.Lib</PackageId>
	<PackageDescription>A template repository for creating and publishing .NET libraries with GitHub Actions for SonarCloud analysis and NuGet deployment.</PackageDescription>
	<Authors>Gabriel (@gasbrieo)</Authors>
	<PackageProjectUrl>https://github.com/gasbrieo/howto-dotnet-lib</PackageProjectUrl>
	<RepositoryUrl>https://github.com/gasbrieo/howto-dotnet-lib</RepositoryUrl>
	<RepositoryType>git</RepositoryType>
	<PackageIcon>Icon.png</PackageIcon>
	<PackageReadmeFile>README.md</PackageReadmeFile>
	<PackageLicenseFile>LICENSE</PackageLicenseFile>
	<Version>$(Version)</Version>
</PropertyGroup>
```

5. Update the following SonarCloud keys in the workflow file `.github/workflows/build-and-analyze.yml`:

```
dotnet sonarscanner begin
  /k:"gasbrieo_howto-dotnet-lib"
  /n:"howto-dotnet-lib"
  /o:"gasbrieo"
```

## Workflows

### SonarCloud Analysis

The GitHub Action workflow `build-and-analyze` runs SonarCloud Analysis on each push to ensure code quality.

To enable SonarCloud:

1. Create a [SonarCloud](https://sonarcloud.io/) account and link your repository.
2. Add `SONAR_TOKEN` as a GitHub secret.
3. The workflow will automatically analyze your code on each push.

### NuGet Publishing

The GitHub Action workflow `publish` publishes the package to NuGet when a new release is created.

To enable NuGet publishing:

1. Generate an API key on [NuGet](https://www.nuget.org).
2. Add `NUGET_API_KEY` as a GitHub secret.
3. The package version is automatically determined based on the release tag in the format `vX.Y.Z`.
4. When you create a new GitHub release, the package will be published automatically.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
