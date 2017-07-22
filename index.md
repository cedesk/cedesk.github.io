## General Concept

CEDESK is a tool to facilitate co-located collaborative model based conceptual design for space missions and complex systems. Multidisciplinary teams of engineers and scientists can use it for working together with a shared parametric model of any type of system.
Features:

* **conceptual design** - supports the team in iterative design by exchanging data between various disciplines and types of models, and guiding the * iterative process until a the design is consolidated.
* **shared repository** - storage of system model including it’s history.
* **concurrent work** - facilitate synchronization of simultaneous work.
* **interactive analytics** (Design Structure Matrix, Multi-Attribute Tradespaces) to support the decision making.

Each discipline expert uses specific tools to elaborate on aspects or parts of the system. These domain specific models can be arbitrary complex and use different specialized tools to work with them, whereas the common system model contains those design parameters through which the parts are interconnected/interdependent.
A goal in the development of the data exchange is not to duplicate functionality of engineering tools, but rather interconnect existing ones in a way to provide fast and easy-to-use integration.

The software is developed at the [Concurrent Engineering Design Laboratory](http://crei.skoltech.ru/space/research/labs/concurrent-engineering-design-laboratory/), which is part of Space Center of [Skolkovo Institute of Science and Technology](https://www.skoltech.ru).

## Team
* Dominik Knoll - Main Author - PhD student - [webpage](http://crei.skoltech.ru/space/people/dominikknoll)
* Nikolay Groshkov - Co-Author - Software Developer
* Alessandro Golkar, PhD - Academic Advisor - Associate Professor - [webpage](http://faculty.skoltech.ru/people/alessandrogolkar)

## Contact
Dominik Knoll, [email](mailto:d.knoll@skoltech.ru)
Skolkovo Institute of Science and Technology, [web](https://www.skoltech.ru)
3 Nobel Street, 143026, Moscow, Russia

## Quick summary

* Architecture: 2 tier (Client application + Database)
* Rich client based on JavaFX
* Service layer with Spring Context
* Persistence layer with Spring JPA and Hibernate
* Server part is a MySQL database

## Used OSS Libraries

* apache-commons-lang3, 3.5, Apache 2.0
* apache-commons-math3, 3.5, Apache 2.0
* apache-poi, 3.16, Apache 2.0
* apache-poi-ooxml, 3.16, Apache 2.0
* commons-beanutils, 1.9.3, Apache 2.0
* controlsfx, 8.40.12, EPL 1.0
* hibernate-core, 5.2.10, LGPL 2.1
* hibernate-envers, 5.2.10, LGPL 2.1
* hibernate-jpa, 1.0.0, EDL 1.0, EPL 1.0
* hsqldb, 2.3.4, BSD
* jboss-transaction-spi, 7.6.0, Public
* jfxtras-labs, 8.0-r5, BSD 2-clause
* jgrapht-core, 1.0.1, EPL 1.0, LGPL 2.1
* jsoup, 1.10.2, MIT license
* jUnit, 4.12, EPL 1.0
* Mockito-Core, 2.8.47, MIT license
* mysql-connector-java, 6.0.6, GPL 2.0
* narayana-jta, 5.6.2, CC0, LGPL 2.1
* slf4j-log4j12, 1.7.21, MIT license
* spring-boot-autoconfigure, 1.5.4, Apache 2.0
* spring-context, 4.3.9, Apache 2.0
* spring-data-jpa, 1.11.4, Apache 2.0

## Source Code Repository
[github.com/cedesk/data-exchange](https://github.com/cedesk/data-exchange)

## Release History

* 2017-07-24 - Version 1.28 -- first public release as Open Source Software

## MIT License
Copyright 2017 Dominik Knoll and Nikolay Groshkov

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.