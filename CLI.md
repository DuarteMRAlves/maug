## Command Line Interface

This document describes the command line interface provided by this package. There are three types of operations: Transforms, Validations and Utilities.

Transforms take as input a sentence and produce one or multiple perturbed sentences.

Validations receive an original sentence and a perturbed sentence and verify if the pertubed sentece complies with some requirement.

Utilities offer functions to perform common operations, such as reading and writing files.

### Transforms

| Name        | CLI Command    | Description |
| ----------- | -------------- | ----------- |
| Negate      | transf-neg     | Negates an english sentence using [PolyJuice](https://arxiv.org/abs/2101.00288) conditioned for negation.
| Swap Number | transf-swp-num | Detects a single number with RegEx and swaps it for text generated with [Google's mT5](https://arxiv.org/abs/2010.11934). |

### Validations

| Name                   | CLI Command            | Description |
| ---------------------- | ---------------------- | ----------- |
| Keep Contradiction     | val-keep-contradiction | Verifies if the perturbed sentence contradicts the original sentence. Relies on an [RoBERTa](https://arxiv.org/abs/1907.11692) model trained for mnli. |
| Remove Equal Sentences | val-rm-equal           | Verifies if the perturbed sentence is different from the original sentence with string comparison. Useful if the transform is unable to produce a perturbation and returns the original sentence.
| Remove a Pattern       | val-rm-pattern         | Verifies if the perturbed sentence does not have a specific regular expression. Usefull with language models that may leave special tokens behind. |

### Utilities

| Name       | CLI Command | Description |
| ---------- | ----------- | ----------- |
| Read Lines | read-lines  | Reads sentences from a text file, where each line is a sentence. |
| Read CSV   | read-csv    | Reads a csv file with multiple language pairs, storing all columns. The original sentence will be associated to the "ref" column. |
| Write JSON | write-json  | Writes the perturbed sentences in a human-readable JSON format. |