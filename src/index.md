---
layout: home
exclude_from_search: true
---

Welcome to my site!

I write about topics that I care about and believe are important. I try to bring my authentic voice every time I set out to type, and I strive to share a viewpoint that gets you thinking and inspired to dig deeper.

----
{: .my-6}

# Latest Articles
{: .mb-5 .title .has-text-centered}

{% assign posts = collections.posts.resources | slice: 0, 6 %}
{% render "bulmatown/collection", collection: posts, metadata: site.metadata %}

{% if collections.posts.resources.size > 6 %}
  <a href="/posts/" class="button is-primary is-outlined is-small"><span>Previous Articles</span> <span class="icon"><i class="fa fa-arrow-right"></i></span></a>
  {: .mt-6 .has-text-centered}
{% endif %}
