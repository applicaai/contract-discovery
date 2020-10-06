# Contract Discovery: Few-Shot Semantic Retrieval Challenge

The aim is to provide substrings of the requested document representing clauses analogous (semantically and formally equivalent) to provided examples from other documents.

Clauses can consist of a single sentence, multiple sentences, or sentence parts. The exact kind of clause is not important during the evaluation since no full-featured training is allowed, and one has to use a set of few sample clauses during the execution.

The input file consists of up to 6 tab-separated fields, eg.:

| ID of the document to search in | Entity considered | Example #1 | ... | Example #N |
|-----------------------------|----------------------|----------------------|--------------------|----------------------|
| NDA\_057 | governing-law | NDA\_059 15215-15453 | NDA\_033 7890-8032 | NDA\_009 12797-13364 |

Each example consists of document ID (_NDA\_059, NDA\_033, NDA\_009_) and characters range (_15215-15453_ and so on). Ranges can be discontinuous. In such a case, their parts are distinguished with a colon, e.g., _4103-4882,12127-12971_.

The same annotation may occur in multiple lines because evaluation is to be performed using a repeated random sub-sampling validation procedure. Sub-samples drawn from a particular set of annotations were split into _k-1_ seed documents and one target document. The selected _k_ interval results in 1-shot to 5-shot learning. Note that the _1–5_ range denotes the number of annotated documents available. It is possible that the same clause type appeared twice in one document, resulting in a higher number of clause instances.

The expected file contains one answer per line, consisting of entity name (to be copied from input) and characters range in the same format as described above. The reference file contains two tab-separated fields: document id and its content.

Directory structure
-------------------
* `README.md` — this file
* `config.txt` — configuration file (compatible with [GEval](https://gitlab.com/filipg/geval) commandline tool)
* `dev-0/` — directory with dev data
* `dev-0/in.tsv` — input data for the dev set
* `dev-0/expected.tsv` — expected (reference) data for the dev set
* `dev-0/reference.tsv.xz` — file with documents considered in dev set
* `test-A` — directory with test data
* `test-A/in.tsv` — input data for the test set
* `test-A/expected.tsv` — expected (reference) data for the test set
* `test-A/reference.tsv.xz` — file with documents considered in test set

Please refer to the paper for details regarding the annotation process and evaluation procedure.

