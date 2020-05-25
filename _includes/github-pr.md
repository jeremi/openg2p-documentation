{% comment %}
  Generates a Github PR URL from three parameters

  Usage:
    {% include github-pr.md org=openg2p repo=openg2p pr=12345 %}

    If you omit the org or repo, they default to openg2p.
    If you omit the pr, it defaults to NULL.

{% endcomment %}{% assign org = include.org | default: "openg2p" %}{% assign repo = include.repo | default: "openg2p" %}{% assign pr = include.pr | default: NULL %}{% assign github-url="https://github.com" %}{% capture pr-link %}[#{{ pr }}]({{ github-url }}/{{ org }}/{{ repo }}/pull/{{ pr }}){% endcapture %}{{ pr-link | strip_newlines }}
