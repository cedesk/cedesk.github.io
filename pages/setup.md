---
layout: page
subheadline:  ""
title:  "Download and Install CEDESK"
teaser: 
categories:
tags:
header: no
permalink: "/setup/"
---

## Download

### Installer Packages

{% for package_version in site.data.releases %}
<p>version <code class="highlighter-rouge">{{ package_version.version_name }}</code>, released <code class="highlighter-rouge">{{ package_version.release_date }}</code></p>
<ul>
    {% for item in package_version.files %}
    <li>{{ item.platform }},  <a href="{{ item.url }}">{{ item.name }}</a> </li>
    {% endfor %}
</ul>
{% endfor %}


### Build from Source Code
Fork on Github [github.com/cedesk/data-exchange](https://github.com/cedesk/data-exchange).

See [Developer's Guide](/developers-guide) for build instructions.

## Installation

Complete instructions for setting up CEDESK on a client are found [here](/documents/CEDESK-Setup.pdf).

## Upgrade

The repository database can undergo changes from one version to the next, and the upgrade of the repository database is not automatic. Please contact the [authors](mailto:cedeskteam@gmail.com) for assistance.

#### Prerequisit

Note that CEDESK requires a MySQL database to be installed on the local machine or on a server in the network. Installation packages are available [here](https://dev.mysql.com/downloads/mysql/).
