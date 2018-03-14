---
layout: unformatted
subheadline:  ""
title:  "Download and Install CEDESK"
teaser: 
categories:
tags:
header: no
permalink: "/releases/"
---

{% for package_version in site.data.releases %}
<p>version <code>{{ package_version.version_name }}</code>, released <code>{{ package_version.release_date }}</code><br/>note: {{ package_version.release_note }}</p>
<ul>
    {% for item in package_version.files %}
    <li>{{ item.platform }},  <a href="{{ item.url }}">{{ item.name }}</a> </li>
    {% endfor %}
</ul>
{% endfor %}
