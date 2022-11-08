# gemini DEV BRANCH
Resources relating to the UK Gemini metadata profile

The published version of GEMINI 2.3 lives at https://www.agi.org.uk/gemini/1037-uk-gemini-standard-and-inspire-implementing-rules/

This is the place to raise and manage issues

This repository does not contain the GEMINI Schematron and sample files, which are at https://github.com/agiorguk/gemini-schematron

Contact gemini@agi.org.uk, or just raise an issue here.

Meeting notes & actions - on https://github.com/agiorguk/gemini/wiki

# guide to our labels
This is how we use the labels:

| Label | Meaning |
| ----- | ------- |
|Guidance|We reckon this issue only affects informative parts of GEMINI|
|Breaking|We expect the solution to this issue to mean that previously valid instances will no longer be valid|
|documentation|We reckon this issue only affects documentation around GEMINI, not the actual elements|
|enhancement|We see this issue as a request for something extra|
|discussion|Probably a status - intended to mean 'the suggested solution requires more discussion'|
|Elements|This issue refers to one or more specific GEMINI elements|
|bug|it looks like somethings definitely broken; we're advising people to do something that is invalid|
|help wanted|whoever raised this issue is asking for help, not (yet) specifically saying something is wrong|
|Encoding|This issue primarily refers to the (XML) encoding of a GEMINI record|
|invalid|something that's wrong but probably not causing people to create invalid records|
|samples|This issue relates to the XML sample files (in the GEMINI-schematron repository)|

Note: overlaps between "Guidance" and "documentation", "bug" and "invalid"

Note: we have not firmly defined which parts of GEMINI are normative & which are informative. Roughly, the normative parts are:
- for each element: the GEMINI id, name, definition, "purpose and meaning", obligation, occurence, data type, and domain
- the general Encoding Guidance page: sections 2.2, 2.3, 2.4 
The rest are informative
