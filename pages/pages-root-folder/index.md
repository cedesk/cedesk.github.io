---
layout: frontpage
header:
  image_fullwidth: header_unsplash_cedl-02.jpg
widget1:
  title: "General Concept"
  url: '/about/'
  image:
  text: 'CEDESK is a tool to facilitate co-located collaborative model-based conceptual design for complex engineering systems. This type of tool is also known as data exchange for concurrent engineering studies.<br/>
  More complete <a href="/documents/CEDESK-documentation.pdf">documentation can be found here</a>.<br/>
  Multidisciplinary design teams can use CEDESK to facilitate their work together by building shared parametric models of their system of interest.'
widget3:
  title: "Features"
  url: '/tool/'
  text: '<ul><li>Conceptual Design</li>
             <li>Shared Repository</li>
             <li>Concurrent work</li>
             <li>Interactive Analytics</li>
         </ul>
         CEDESK does not duplicate the functionality of existing engineering tools, but rather interconnects existing tools to provide fast and easy-to-use integration among engineering disciplines.
         See <a href="/comparison/">tool comparison</a>.'
  image:
widget2:
  title: "Use &amp; Contribute"
  url: '/setup/'
  image:
  text: 'Installation packages of the tool are available for Windows, MacOS and Linux <a href="/setup/">here</a>.
            <br/><br/>
            Read the intoductory guide to <a href="/getting-started">get started</a>.
            <br/><br/>
            Check out the source code on <a href="https://github.com/cedesk/data-exchange">GitHub</a> and the
            <a href="/developers-guide/">developers guide</a>, report
            <a href="https://github.com/cedesk/data-exchange/issues">issues</a> or adopt it your needs and join
            the developers community.'
#callforaction:
#  url: '/development/'
#  text: Get started and contribute to the development ›
#  style: secondary
permalink: /index.html
homepage: true
---

{% assign packages = site.data.releases | first %}
{% assign package_version = packages %}
<p>
  Latest version <code>{{ package_version.version_name }}</code> ({{ package_version.release_date }}),
  download packages for
  {% for item in package_version.files %}
    <a href="{{ item.url }}" title="{{ item.name }}">{{ item.platform }}</a>, 
  {% endfor %}
</p>


## Release History

<ul>
{% for package_version in site.data.releases %}
  <li>{{ package_version.release_date }} - Version: {{ package_version.version_name }} - {{ package_version.release_note }}</li>
{% endfor %}
</ul>

## License
Copyright 2017 Skolkovo Institute of Science and Technology

Licensed under the Apache License, Version 2.0 (the "License");
you may not use CEDESK source code except in compliance with the License.
You may obtain a copy of the License at
[www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and limitations under the License.
