# Gemini documentation

Simple readme for testing conversion of asciidoctor files


* [Services](titleservices-title.html) 
* [Datasets](titledatasets-datasets.html)

Both files are generated from [title.asciidoc](https://github.com/archaeogeek/gemini/blob/main/docs/title.asciidoc) with different snippets for datasets and services in the partials folder.

To generate, use the `-a` parameter, eg with docker (from the docs folder):

```
docker run --rm -v $(pwd):/documents/ asciidoctor/docker-asciidoctor asciidoctor -a variant-dataset title.asciidoc
```