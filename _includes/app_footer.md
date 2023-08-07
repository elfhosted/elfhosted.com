
{% if page.meta.works_with %}
## {{ page.meta.slug }} also works with
{% for app in page.meta.works_with %}
* [x] [{{ app }}][{{ app | lower }}]
{% endfor %}
{% endif %}

## How do I get support for {{ page.meta.slug }}?

1. For general use of {{ page.meta.slug }}, refer to the [official site]({{ page.meta.upstream }}) or to one of the links [below](#useful-links).
2. For specific support re your ElfHosted configuration / account, either post a topic in the [#elf-forum](https://discord.com/channels/396055506072109067/1119489053927145472) channel, or call for 1:1 [#elf-help](https://discord.com/channels/396055506072109067/1119478614287712337).

## {{ page.meta.slug }} resources

* [{{ page.meta.slug }} (official site)]({{ page.meta.upstream }})
{% if page.meta.links %}
{% for link in page.meta.links %}
* [{{ page.meta.slug }} {{ link.name }}]({{ link.uri }})
{% endfor %}
{% endif %}
--8<-- "common-links.md"