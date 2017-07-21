## General Concept

CEDESK is a tool to facilitate co-located collaborative model based conceptual design for space missions and complex systems. Multidisciplinary teams of engineers and scientists can use it for working together with a shared parametric model of any type of system. 
Features:
* _conceptual design_ - supports the team in iterative design by exchanging data between various disciplines and types of models, and guiding the * iterative process until a the design is consolidated.
* _shared repository_ - storage of system model including it’s history.
* _concurrent work_ - facilitate synchronization of simultaneous work.
* _interactive analytics_ (Design Structure Matrix, Multi-Attribute Tradespaces) to support the decision making.
Each discipline expert uses specific tools to elaborate on aspects or parts of the system. These domain specific models can be arbitrary complex and use different specialized tools to work with them, whereas the common system model contains those design parameters through which the parts are interconnected/interdependent.
A goal in the development of the data exchange is not to duplicate functionality of engineering tools, but rather interconnect existing ones in a way to provide fast and easy-to-use integration.


## Quick summary

* Architecture: 2 tier (Client application + Database)
* Rich client based on JavaFX
* Service layer with Spring Context
* Persistence layer with Spring JPA and Hibernate
* Server part is an SQL database

## Used OSS Libraries

* jUnit, 4.12, Eclipse Public License 1.0
* Mockito-Core, 2.8.47, MIT license
* spring-context, 4.3.9, Apache 2.0
* spring-data-jpa, 1.11.4, Apache 2.0
* hibernate-core, 5.2.10, LGPL 2.1
* mysql-connector-java, 6.0.6, GPL 2.0
* hibernate-jpa, 1.0.0, EDL 1.0, EPL 1.0
* hibernate-envers, 5.2.10, LGPL 2.1
* slf4j-log4j12, 1.7.21, MIT license
* hsqldb, 2.3.4, BSD
* apache-poi, 3.16, Apache 2.0
* apache-poi-ooxml, 3.16, Apache 2.0
* controlsfx, 8.40.12, EPL 1.0
* jfxtras-labs, 8.0-r5, BSD 2-clause
* apache-commons-math3, 3.5, Apache 2.0
* apache-commons-lang3, 3.5, Apache 2.0
* commons-beanutils, 1.9.3, Apache 2.0
* jgrapht-core, 1.0.1, EPL 1.0, LGPL 2.1
* jsoup, 1.10.2, MIT license

## Release History

* 2017-07-24 - Version 1.28 -- first public release as Open Source Software

## License
