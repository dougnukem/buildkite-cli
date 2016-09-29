# bk

[![Build Status](https://travis-ci.org/wolfeidau/buildkite-cli.svg?branch=master)](https://travis-ci.org/wolfeidau/buildkite-cli)

A simple command line interface to the [buildkite](http://buildkite.com) service.

![ScreenShot](/docs/buildkite-cli-builds.gif)

# install

At the moment installation is done just using the go get command.

```
go get github.com/wolfeidau/buildkite-cli/cmds/bk
```

# usage

```
usage: bk <command> [<flags>] [<args> ...]

A command-line interface for buildkite.com.

Flags:
  --help  Show help.

Commands:
  help [<command>]
    Show help for a command.

  projects
    List projects under an orginization.

  builds
    List latest builds for the current project.

  logs [<number>]
    Retrieve the logs for the current projects last build.

  open
    Open builds list in your browser for the current project.

  setup
    Configure the buildkite cli with a new token.

```

Navigate to a project hosted in build box and run:

* `bk builds` - This will show you a list of the recent builds for this project.
* `bk logs` - This will show you the logs for the last build/job which ran against this project.

# TODO

* Truncate commit message text.
* Fix usage output as it is confusing.
* Help the user create the correct type of token using the changes which enable defaulting stuff in the new token page with the various scopes.
* Deal with https://github.com vs git@github.com: remotes.

# buildkite API notes

* Would be nice to have access to the orginization slug in the project(s) results as it is critical for building URLs relating to associated content.
* Would be nice to have notable website URLs in the project/build content, or some base resource which defines then in the REST API. The rationale for this is if you wanted to use bk for a test or onsite instance of buildkite the sources would currently need to be modified.
* The API is a little slow for an interactive application, can take up to 9 seconds to pull down the builds for a project as I am not currently caching these results. At the moment I do a call to orgs, then projects, then builds to retrieve the details.

# license

Released under MIT license.
