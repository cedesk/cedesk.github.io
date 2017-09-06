---
layout: page
title: Developer's guide
subtitle: The organization of the project.
---

## Configuration Management

### Source Code ###

Public repository on Github [https://github.com/cedesk/data-exchange](https://github.com/cedesk/data-exchange)

### Branching ###

The `master` branch keeps the stable, released versions.

There is a `development` branch, where some global improvements were done. Feature development is done in branches. Mature features are merged back to the `development` branch.

### Releasing ###

Making a release is made in several steps.

1) First eventually added/remove OSS libraries are reflected in the file `about.html`.

2) The `development` branch is merged on to the `master` branch, and the new version number is modified in the build file (`pom.xml`). If the data entities have changed the schema version needs to be modifed as well (also in the `pom.xml`).

3) Set a tag on the last commit on the master branch with the version number in the format `v##.##`, e.g. `v1.25`.

4) Push commits and tags to the central repository.

### Source Code Structure ###

Application resides in sub directory `\client`.

The source code is organized following the maven standard:

`\src`

  * `\main` contains the source code files

    * `\deploy` contains files for the packaging (icons)

    * `\java` contains the java source code, organized in packages

    * `\resources` contains non-java files, which are required at runtime (images, configuration files)

    * `\sql` contains sql files for the setup of the database backend

  * `\test` contains the java source code files used for testing only

`\target` contains the results of builds

### Java Packages ###

Base Package: `ru.skoltech.cedl.dataexchange`

  * `.db`  classes for database handling (schema versioning)
  
  * `.entity`  classes which define domain objects, principally stored the database

  * `.external` classes for handling external models, such as excel files

  * `.file`  classes for listening to file changes on the filesystem
  
  * `.init`  classes which define operations, essential for application launching

  * `.logging` classes for action logging in the backend

  * `.repository` classes for handling the storage backend (Data Access Objects)
  
  * `.service` classes for handling service layer operations

  * `.structure` classes which define the Product Breakdown Structure of a System Model

  * `.units`  classes representing the units of measures

  * `.users`  classes representing the application users

  * `.ui`  classes related to UI (controllers, controls, paths to _*.fxml_ views)

## Build System ##

For managing the dependencies of the software on third-party libraries and defining the build process, the project uses Maven 3, see `pom.xml`.

### Client installer packages ###

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


## Automated Tests ##

JUnit4 is used for defining and running tests.

There are different kinds of tests.

- most of the tests are real unit tests;
- others were written as proof of concept code for developing certain functionality, in particular for the use of certain libraries. These often use a static void main method as entry point.

## Issue Management

Bugs and missing features are documented and tracked in Bitbucket as well:

[https://bitbucket.org/cedesk/data-exchange/issues](https://bitbucket.org/cedesk/data-exchange/issues)
