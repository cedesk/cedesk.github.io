# CEDESK - Concurrent Engineering Data Exchange Skoltech #

This is a collaboration tool for parametric system modeling in [Concurrent Engineering Design Lab](http://crei.skoltech.ru/space/research/labs/concurrent-engineering-design-laboratory/).

## General Concept

CEDESK was conceived as a data exchange tool for concurrent engineering design studies. It is meant to support the collaboration between engineers working together through a common model of the system. Each engineer uses specific tools to elaborate on aspects or parts of the system. These domain specific models can be arbitrary complex and use different specialized tools to work with them, whereas the common system model most and for all contains those design parameters through which the parts are interconnected/interdependent.

A goal in the development of the data exchange is not to duplicate functionality of engineering tools, but rather interconnect existing ones in a way to provide fast and easy-to-use integration.

## Quick summary

* Architecture: 2 tier (Client application + Database)
* Rich Client based on JavaFX
* Serice Layer with Spring Context
* Persistence Layer with Spring JPA and Hibernate
* Server part is an SQL database
* Current State: Development

## List of used OSS Libraries

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
