pr-dash
----
`pr-dash` is a command line tool which allows you to monitor the status
of all Azure Dev Ops pull requests you are assigned a reviewer of, right
at home in your terminal.

pr-dash is currently tested on Windows and Linux.

Note: This tool is not created by, affiliated with, or supported by Microsoft/Azure DevOps.

[![Build Status](https://travis-ci.org/bgianfo/pr-dash.svg?branch=master)](https://travis-ci.org/bgianfo/pr-dash)
[![GitHub license](https://img.shields.io/github/license/bgianfo/pr-dash.svg)]()
[![Dependabot Status](https://api.dependabot.com/badges/status?host=github&repo=bgianfo/pr-dash)](https://dependabot.com)
[![Total alerts](https://img.shields.io/lgtm/alerts/g/bgianfo/pr-dash.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/bgianfo/pr-dash/alerts/)


### Configuration

To configure pr-dash you simply need to setup a yaml file with one or more
projects/repo's to monitor for reviews.

The location of the yaml file differs based on the OS:
- Linux: ~/.pr-dash.yml
- Windows: C:\Users\USER-NAME\AppData\Roaming\pr-dash.yml (%APPDATA%\pr-dash.yml)

Example pr-dash.yml:

```
accounts:
  - project_name: sample-project1
    repo_name: sample-git-repo1
    org_url: https://dev.azure.com/example1
    pat: <your-personal-authentication-token>

  - project_name: sample-project2
    repo_name: sample-git-repo2
    org_url: https://example2.visualstudio.com
    pat: <your-personal-authentication-token>

  # Would only work on windows
  - project_name: sample-project3
    repo_name: sample-git-repo3
    org_url: https://example3.visualstudio.com

```

Notes:
- *repo_name* is optional, if it's omitted the project name will be used for the repo name as well.
- *pat* is optional when running on windows, if it's omitted the code will attempt to use AAD authentication.
- You can read how to create an Azure DevOps PAT token [here](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops).

Now you can run pr-dash and try it out.

### Key Bindings

    Action Keys:
     r - Force refresh the current PR view.
     a - Switch the current view to actionable PRs.
     w - Switch the current view to waiting PRs.
     d - Switch the current view to draft PRs.
     h - Display this help dialog.
     q - Quit the program.
     Enter - Open the currently selected PR.

    Movement Keys:
     ↑ - Select one pull request up.
     ↓ - Select one pull request down.
     k - Select one pull request up.
     j - Select one pull request down.

### Building

`pr-dash` is written in C#, targeting dotnet core so you'll need to grab a
[dotnet core 3.0 installation](https://dotnet.microsoft.com/download/dotnet-core/3.0) in order to compile it.
Building is easy:

```
$ git clone https://github.com/bgianfo/pr-dash
$ cd pr-dash\src
$ dotnet run
```

### Running Tests

To run the [xunit](https://xunit.net/) based test suite, use:

```
$ cd pr-dash
$ dotnet test
```

