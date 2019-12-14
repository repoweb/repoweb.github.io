---
layout: page
title: Packages List
subtitle: Lista de Pacotes
target: _blank
latest_posts: true
link_ref: packagesList
---

## Lista de Pacotes

{% for repo in site.data.repos %}
* [{{ repo.name }}]({{repo.url}}){:target="_blank"}
{% endfor %}

{% include post_footer.html %}
