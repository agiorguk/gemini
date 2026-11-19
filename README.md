# UK GEMINI

UK GEMINI is the UK standard for discovery metadata about geographic datasets, dataset series and services. It is based on ISO 19115, encoded in XML using ISO 19139, and conforming to it should also ensure conformance to the INSPIRE Implementing Rules. The current version is **GEMINI 2.3**.

This repository holds the source of the published GEMINI documentation, and is where issues with GEMINI are raised and managed. GEMINI is maintained by the GEMINI Working Group for the [Association for Geographic Information (AGI)](https://www.agi.org.uk/uk-gemini/).

## Read GEMINI

| | |
| --- | --- |
| GEMINI 2.3 home page | https://agiorguk.github.io/gemini/1037-uk-gemini-introduction.html |
| GEMINI for datasets and series | https://agiorguk.github.io/gemini/1062-gemini-datasets-and-data-series.html |
| GEMINI for services | https://agiorguk.github.io/gemini/1063-gemini-services.html |
| Element summary | https://agiorguk.github.io/gemini/1250-element-summary.html |
| XML encoding guidance | https://agiorguk.github.io/gemini/1048-uk-gemini-encoding-guidance.html |

The previous home page, https://agiorguk.github.io/gemini/1037-uk-gemini-standard-and-inspire-implementing-rules.html, is still published, and https://www.agi.org.uk/gemini/1037-uk-gemini-standard-and-inspire-implementing-rules/ redirects to it.

To validate GEMINI records, use the Schematron rules in [agiorguk/gemini-schematron](https://github.com/agiorguk/gemini-schematron).

## Raise an issue

If you've found a problem with GEMINI or want to suggest a change, [open an issue](https://github.com/agiorguk/gemini/issues). You can also email [gemini@agi.org.uk](mailto:gemini@agi.org.uk). Issues with the Schematron rules belong in [agiorguk/gemini-schematron](https://github.com/agiorguk/gemini-schematron/issues).

The Working Group reviews issues at its meetings. Notes and actions from those meetings are on the [wiki](https://github.com/agiorguk/gemini/wiki).

### Labels

| Label | Meaning |
| --- | --- |
| Elements | Refers to one or more specific GEMINI elements |
| Encoding | Mainly about the XML encoding of a GEMINI record |
| services | Specific to metadata for services |
| Guidance | Affects only the informative parts of GEMINI (see below) |
| documentation | Affects the documentation around GEMINI, not the elements themselves |
| breaking | The fix would make some previously valid records invalid |
| bug | GEMINI advises people to do something invalid |
| invalid | Something is wrong, but probably isn't causing people to create invalid records |
| enhancement | A request for something new |
| discussion | The proposed solution needs more discussion |
| question / help wanted | The person raising it is asking for help, not reporting a fault |
| DD3 | Comes from a recommendation in the DD3-3 GEMINI Recommendations Report (in [`archive/`](archive)) |
| immediate | Can be made and published straight away |
| release | Should be batched into a release, for example because it needs software changes |

### Normative and informative content

The Working Group hasn't formally defined which parts of GEMINI are normative. Roughly, these parts are normative and everything else is informative guidance:

- for each element: its GEMINI id, name, definition, purpose and meaning, obligation, occurrence, data type and domain
- in the [XML encoding guidance](https://agiorguk.github.io/gemini/1048-uk-gemini-encoding-guidance.html): sections 2.2 (Common concepts), 2.3 (Metadata for datasets and dataset series) and 2.4 (Metadata for services)

## How the site is published

The pages are written in [AsciiDoc](https://docs.asciidoctor.org/asciidoc/latest/) and converted to HTML with Asciidoctor by GitHub Actions:

| Branch | Published at | Workflow |
| --- | --- | --- |
| `main` (live) | https://agiorguk.github.io/gemini/ | [`build-adocs.yml`](.github/workflows/build-adocs.yml) pushes the HTML to this repository's `gh-pages` branch |
| `dev` (preview) | https://agiorguk.github.io/gemini-dev/ | [`dev-build.yml`](.github/workflows/dev-build.yml) pushes the HTML to the `gh-pages` branch of [agiorguk/gemini-dev](https://github.com/agiorguk/gemini-dev) |

Each takes a few minutes to appear after a push.

## Making changes

1. Make changes on the `dev` branch, either directly or through a pull request into `dev`.
2. Check the result on the preview site.
3. Open a pull request from `dev` into `main`. `main` is protected, so another member of the Working Group has to review it before it's merged and goes live.

The wiki page [How the Gemini documentation is compiled](https://github.com/agiorguk/gemini/wiki/How-the-Gemini-documentation-is-compiled) walks through editing on GitHub and on your own computer.

### Build the pages locally

With Docker installed, run this from the `docs` folder:

```bash
docker run --rm -v "$(pwd):/documents/" asciidoctor/docker-asciidoctor asciidoctor -a docinfo1 -T templates -E slim '*.asciidoc' '*.adoc'
```

The HTML files are written next to the sources; open them in a browser. Errors in the AsciiDoc are printed to the terminal.

## What's in this repository

| Path | Contents |
| --- | --- |
| [`docs/`](docs) | AsciiDoc source for every published page. Most file names start with the article number the page had on the old AGI website, for example `1062-gemini-datasets-and-data-series.adoc`. |
| [`docs/partials/`](docs/partials) | One file per GEMINI element, named after the element in lower case without spaces (for example `resourcelocator.asciidoc`). The datasets and services pages are assembled from these. |
| [`docs/snippets/`](docs/snippets) | The XML examples shown on the element pages. They're named after the element, optionally starting with `dataset-`, `service-` or `series-` and ending with the example's name, for example `service-resourcelocator-function-wms.xml`. |
| [`docs/includes/`](docs/includes), [`docs/partials/includes/`](docs/partials/includes) | Shared AsciiDoc settings. |
| [`docs/templates/`](docs/templates) | Template that changes how lists are rendered. |
| [`docs/assets/`](docs/assets), `docs/docinfo*.html` | Styles, fonts, and the AGI header and footer added to every page. |
| [`docs/archive/`](docs/archive) | Pages that have been taken off the site. They aren't built. |
| [`archive/`](archive) | Working Group records: the DD3-3 Recommendations Report, the old bug tracker, and the actions log from 2015 to 2021. |
| [`governance/`](governance) | The Working Group governance proposal and notes on the website update process. |
| [`resources/`](resources) | Supporting material: the GEMINI UML model (Enterprise Architect), workshop slides, and a map of the pages and their old AGI addresses. |
| [`pending/`](pending) | Copies of pages from the old AGI website, kept from the 2021 move to GitHub Pages. |

### Datasets and services from the same files

Most elements apply to both datasets and services, with some differences. Each element file marks the dataset-only and service-only parts with tagged regions:

```asciidoc
// tag::dataset[]
...content for datasets and series...
// end::dataset[]
// tag::service[]
...content for services...
// end::service[]
```

The datasets page includes each element with `tag=!service`, and the services page with `tag=!dataset`, so each page leaves out the other's regions.

## Licence

GEMINI is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).
