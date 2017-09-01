---
title: CEDESK developer's guide
---

Author: Dominik Knoll, [d.knoll@skoltech.ru](mailto:d.knoll@skoltech.ru)

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

For managing the dependencies of the software on libraries and defining the build process, the project uses Maven 3, see `pom.xml`.

### Client installer packages ###

Packaging native installers (win: _.exe_, mac: _.dmg_, linux: _.deb_),

Using a maven plugin for JavaFX applications [http://javafx-maven-plugin.github.io/](http://javafx-maven-plugin.github.io/)

***Requirements***

for Windows: Inno Setup 5 or later from [http://www.jrsoftware.org](http://www.jrsoftware.org)

for MacOS: Xcode

for Linux: ?

## Automated Tests ##

JUnit4 is used for defining and running tests.

There are different kinds of tests.

- most of the tests are real unit tests;
- others were written as proof of concept code for developing certain functionality, in particular for the use of certain libraries. These often use a static void main method as entry point.

## Issue Management

Bugs and missing features are documented and tracked in Bitbucket as well:

[https://bitbucket.org/cedesk/data-exchange/issues](https://bitbucket.org/cedesk/data-exchange/issues)

## Graphical User Interface

The application's GUI is based on JavaFX framework, and additional libraries on top. Following the JavaFX framework, the application's entry point is the class **ClientApplication** (terms in bold mean classnames).

The structure follows the Model View Controller (MVC) pattern:

- _MODEL_ - objects containing the information to display, or to operate on;
- _VIEWS_ - the description of the elements of the GUI, which in JavaFX can be done in FXML files;
- _CONTROLLERS_ - classes that contain methods to deal with user inputs or changes on the data.

The _MODEL_ is primarily contained in the **Project** class, which holds members of type **Study**, **User**, **UserManagement**, **UnitManagement** and **Repository**. The project class holds the state of the application and implements some business logics.

According to JavaFX, _VIEWS_ are encoded in FXML files and _CONTROLLERS_ are java classes.

The application's main window uses the view defined in `main-window.fxml` and the corresponding controller is **MainController**.

**MainController** - manages the application menu, and handles the primary user actions to create a new, load an existing, save a project. Moreover it allows to open dialogue for the application and project settings, as well as the user and user role management.

The part for editing the system model is delegated to a specific view `model-editing.fxml` and the corresponding controller is **ModelEditingController**.

**ModelEditingController** - manages the modifications to the system model structure (node tree), and the nodes' parameter list.

## Data Storage

The application uses an Object to Relational Database mapping framework called Hibernate ORM, which implements the Java Persistence Architecture (JPA 2).

The classes which represents objects to be stored in the database, are annotated accordingly. Classes are mapped to tables, properties (with getter and setter methods) are mapped to table columns if they are primitive types, or foreign-key relationships for complex types.

The default database credentials are username `cedesk`, password `cedesk`, but can be overwritten in the application settings.

## Data Model

![1-model.png](/img/1-model.png)
![2-project.png](/img/2-project.png)

**Project** - a singleton class, handling a lot of business logics. Members: `local study`, `remote study`, `user management`, `unit management`;

**Study** (persisted) - class representing a project. Members: `system model`, `user role management`, `study settings`;

**ModelNode** - abstract class representing a node. Members: `name`, list of `parameters`, list of `external models`;

**CompositeModelNode** - abstract subclass of **ModelNode**, Members: list of `submodes`;

**SystemModel** - subclass of **CompositeModelNode**, subnodes of type _Subsystem_;

**SubsystemModel** - subclass of **CompositeModelNode**, subnodes of type _Instrument_; 

**InstrumentModel** - subclass of **CompositeModelNode**, subnodes of type _Element_;

**ElementModel** - subclass of **ModelNode**;

**ParameterModel** - class to represent model parameters. Members: `nature`, `unit`, `value`, `value source`, `exported`; optional: `value link` (another parameter model), `export reference` (a target within an external model).

## Services ##

![3-services.png](/img/3-services.png)

Application middleware backbone predominantly based on Spring application context, which is container for features of 3 types:

1. Services of various kinds for handling common application operations;
2. Data Access Objects (DAO) layer which provides low-level database operations. It is based on Spring Data framework and uses container-based JPA EntityManager, defined also via Spring application context;
3. JavaFX GUI Controllers. Their dependencies are also defined in the application context;
4. Additional model features, briefly described bellow.

**ApplicationSettings**

For launching the Application context it is necessary to provide some properties for it. There are 2 kind of them:

1. Application-specific properties stored in a `cedesk.properties` file within the _.jar_ file. These properties can be overwritten by system properties of the same name. They include:
    - the build version of the application;
    - the version of the database schema;
    - the url of the distribution server where new versions are published;
    - the default server hostname, schema name, user name and password of the database / model repository;
    - Hibernate and JDBC properties;
    - other application properties.

2. User-specific properties. By default they are stored in a `application.settings` file in a subdirectory of the user's home directory called `.cedesk`, but it's path and filename can be configured via `cedesk.app.dir` and `cedesk.app.file` application-specific properties. User of application a free to change user-specific properties in this file. User-specific properties include:
    - database connection (server hostname, schema name and credentials);
    - the name of the last open project;
    - whether to automatically load the last open project;
    - whether to use the username logged on to the operating system;
    - the username to use for the project;
    - whether to check periodically for changes in the model repository;
    - the number of levels a new study should be created with.

There is a special class inside the application context which is aimed to provide access to both of those 2 kinds of properties. But it is required to perform the special static `ApplicationSettingsInitializer.initialize()` method to initialize (and locate in case of its absence) user-specific properties.

Below is description of additional model features, also defined via application context.
 
**RepositoryWatcher**

This service based on the Spring scheduling in the application context performs a periodical checks (10 sec) on the repository, to check whether there is a newer version of the system model currently in use on the client. This check is paused when a new system model is created.

**Synchronization of two applications**

![4-synch.png](/img/4-synch.png)

**ExternalModelFileWatcher, SimpleDirectoryWatchService, DirectoryWatchService**

This classes encapsulate a service to oversee the external model files which are kept in a cache on the client's local disc. In case such a file changes, the parameters referring to the file are updated.

This functionality is uses services offered by the standard Java API to receive notifications on changes on the file system from the OS.

Parts of the code were recycled from an internet resource.

### Infrastructure for Logging ###

**StatusLogger** - a class which outputs information in the statusbar of the user interface, limited to contain the last 10 entries.

**ActionLogger** - a class which logs to the database the principal user actions on the client (load/save project, add/modify/remove model node, add/modify/remove parameter).

Log4j library is used for logging of information for debugging and error tracing, it's configured to write a logfile into the `application.log` in a subdirectory of the user's home directory called `.cedesk`.

### UpdateChecker ###

This class is used to check the distribution server, whether there is a newer version of the application available (distinguishing packages _.exe_, _.deb_, _.dmg_ for the various OS).

## Nota Bene

The naming of elements (files, classes and UI items) has a few inconsistencies. These are to be removed, by agreeing on a uniform terminology and refactoring the code!