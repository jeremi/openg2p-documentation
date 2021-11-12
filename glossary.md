---
---
title: "Glossary"
description: "Glossary of terms used around OpenG2P"
keywords: "glossary, openg2p, terms, definitions"
notoc: true
noratings: true
skip_read_time: true
---
<!--
To edit/add/remove glossary entries, visit the YAML file at:
https://github.com/openg2p/openg2p.github.io/blob/master/_data/glossary.yaml

To get a specific entry while writing a page in the docs, enter Liquid text
like so:
{{ site.data.glossary["aufs"] }}
-->
<span id="glossaryMatch" />
<span id="topicMatch" />

<table border="1">
  {% for entry in site.data.glossary %}
    <tr>
      <td>{{ entry[0] }}</td>
      <td>{{ entry[1] | markdownify }}</td>
    </tr>
  {% endfor %}
</table>
