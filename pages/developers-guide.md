---
layout: page
subheadline:  "The organization of the project"
title:  "Developer's guide"
teaser: 
categories:
tags:
header: no
permalink: "/developers-guide/"
---

## Configuration Management

### Source Code

Public repository on Github [github.com/cedesk/data-exchange](https://github.com/cedesk/data-exchange)

### Branching

The `master` branch keeps the stable, released versions.

There is a `development` branch, where some global improvements were done. Feature development is done in branches. Mature features are merged back to the `development` branch.

### Releasing

Making a release is made in several steps.

1) First eventually added/remove OSS libraries are reflected in the file `about.html`.

2) The `development` branch is merged on to the `master` branch, and the new version number is modified in the build file (`pom.xml`). If the data entities have changed the schema version needs to be modifed as well (also in the `pom.xml`).

3) Set a tag on the last commit on the master branch with the version number in the format `v##.##`, e.g. `v1.25`.

4) Push commits and tags to the central repository.

## Build System

For managing the dependencies of the software on third-party libraries and defining the build process, the project uses Maven 3, see `pom.xml`.

### Client installer packages

Packaging native installers (win: _.exe_, mac: _.dmg_, linux: _.deb_),
using a [javafx-maven-plugin](http://javafx-maven-plugin.github.io/), which is a wrapper of the [JavaFX packaging utility](http://docs.oracle.com/javafx/2/deployment/self-contained-packaging.htm).

The build phase `package` produces the installer for the platform on which the build is running.
The build phase `deploy` copies the package to an output directory, depending on the environment:

* by default the directory is `${user.home}/development/cedesk-builds`

* if the environment variable `buildserver` is set, then directory is `c:/data/cedesk-builds`

***Requirements***

* for Windows: Inno Setup 5 or later from [http://www.jrsoftware.org](http://www.jrsoftware.org)

* for MacOS: Xcode

* for Linux: RPMBuild or Debian packaging tools


## Automated Tests

JUnit4 is used for defining and running tests.

There are different kinds of tests.

- most of the tests are real unit tests;
- others were written as proof of concept code for developing certain functionality, in particular for the use of certain libraries. These often use a static void main method as entry point.
