
# Gemini documentation

Start at the [UK GEMINI introduction](https://agiorguk.github.io/gemini/1037-uk-gemini-introduction.html), or go straight to the element guidance:

* [Services](https://agiorguk.github.io/gemini/1063-gemini-services.html)
* [Datasets](https://agiorguk.github.io/gemini/1062-gemini-datasets-and-data-series.html)

Other pages:

* [1037-uk-gemini-standard-and-inspire-implementing-rules](https://agiorguk.github.io/gemini/1037-uk-gemini-standard-and-inspire-implementing-rules.html)
* [1040-checklist-for-conformity](https://agiorguk.github.io/gemini/1040-checklist-for-conformity.html)
* [1046-xml-element-order](https://agiorguk.github.io/gemini/1046-xml-element-order.html)
* [1047-metadata-guidelines-for-geospatial-data-resources-part-3](https://agiorguk.github.io/gemini/1047-metadata-guidelines-for-geospatial-data-resources-part-3.html)
* [1048-uk-gemini-encoding-guidance](https://agiorguk.github.io/gemini/1048-uk-gemini-encoding-guidance.html)
* [1049-metadata-guidelines-for-geospatial-data-resources-part-2](https://agiorguk.github.io/gemini/1049-metadata-guidelines-for-geospatial-data-resources-part-2.html)
* [1050-inspire-metadata-requirements](https://agiorguk.github.io/gemini/1050-inspire-metadata-requirements.html)
* [1051-uk-gemini-v2-2-specification-for-discovery-metadata-for-geospatial-resources](https://agiorguk.github.io/gemini/1051-uk-gemini-v2-2-specification-for-discovery-metadata-for-geospatial-resources.html)
* [1052-metadata-guidelines-for-geospatial-data-resources-part-1](https://agiorguk.github.io/gemini/1052-metadata-guidelines-for-geospatial-data-resources-part-1.html)
* [1053-common-metadata-errors-uk-location-discovery-metadata-service](https://agiorguk.github.io/gemini/1053-common-metadata-errors-uk-location-discovery-metadata-service.html)
* [1055-uk-gemini-major-changes-since-1-0](https://agiorguk.github.io/gemini/1055-uk-gemini-major-changes-since-1-0.html)
* [1056-glossary](https://agiorguk.github.io/gemini/1056-glossary.html)
* [1250-element-summary](https://agiorguk.github.io/gemini/1250-element-summary.html)

Links above this are to the GitHub pages published in https://agiorguk.github.io/gemini/

## Services and Datasets workflow

* These files are generated from [include files](https://docs.asciidoctor.org/asciidoc/latest/directives/include/), one per element, in the [docs/partials](https://github.com/agiorguk/gemini/tree/main/docs/partials) folder.
* The xml snippets are in the docs/snippets folder.
* The naming convention for the element files is {element name in lower case without spaces}.asciidoc
* The naming convention for the xml snippets is {optional dataset, service or series prefix}-{element name in lower case without spaces}-{optional specific example}.xml

Where content differs between datasets and services, the element file marks it with [tagged regions](https://docs.asciidoctor.org/asciidoc/latest/directives/include-tagged-regions/), `tag::dataset[]` … `end::dataset[]` and `tag::service[]` … `end::service[]`. The datasets page includes each element with `tag=!service` and the services page with `tag=!dataset`, so one build produces both pages.

To build every page with the Asciidoctor Docker container, run this from the docs folder:

```
docker run --rm -v "$(pwd):/documents/" asciidoctor/docker-asciidoctor asciidoctor -a docinfo1 -T templates -E slim '*.asciidoc' '*.adoc'
```

See the [repository README](https://github.com/agiorguk/gemini#readme) for how the pages are published and how to make changes.

## Styling

All files share a common attributes file, which indicates the basic attributes to be used when processing. This includes a linked reference to the asciidoc html stylesheet rather than the default embedding. Work has begun to integrate the styling from the old website's [Gemini.css](https://github.com/agiorguk/gemini/blob/main/pending/june2021/Gemini.css) into the site's stylesheets ([gemini.css](https://github.com/agiorguk/gemini/blob/main/docs/assets/gemini.css), which builds on [asciidoctor.css](https://github.com/agiorguk/gemini/blob/main/docs/assets/asciidoctor.css)) but this is far from complete.
