
{% if page.meta.works_with %}
## {{ page.meta.slug }} also works with
{% for app in page.meta.works_with %}
* [x] [{{ app }}][{{ app | lower }}]
{% endfor %}
{% endif %}

## How do I get support for {{ page.meta.slug }}?

1. For general use of {{ page.meta.slug }}, refer to the [official site]({{ page.meta.upstream }}) or to one of the links [below](#useful-links).
2. For specific support re your ElfHosted configuration / account, see the [ElfHosted support options](/get-help/)!

{% if page.meta.sponsorship %}
## Sponsor {{ page.meta.slug }} ❤️

You can contribute directly to the development of {{ page.meta.slug }} using the following:
{% for link in page.meta.sponsorship %}
* [{{ link.name }}]({{ link.uri }})
{% endfor %}
{% endif %}

## {{ page.meta.slug }} resources

* [{{ page.meta.slug }} (official site)]({{ page.meta.upstream }})
{% if page.meta.links %}
{% for link in page.meta.links %}
* [{{ page.meta.slug }} {{ link.name }}]({{ link.uri }})
{% endfor %}
{% endif %}

{% include 'testimonials.md' %}

--8<-- "common-links.md"