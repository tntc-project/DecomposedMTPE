# DecomposedMTPE

## Introduction

This repository contains 50 pairs of a machine-translated (MT) sentence and its post-edited (PE) result with their intermediate sentences, which gradually convert the MT sentence to the PE sentence by primitive edit operations.

## Content

- [DecomposedMTPE.json](/DecomposedMTPE.json)

| Field | Explanation |
| ---- | ---- |
| `docId` | document ID retrieved from MTPEdocs | 
| `stId` | source text ID |
| `st` | source text |
| `mt` | MT output for `st` |
| `mtSystem` | MT system used to obtain `mt` |
| `pe` | PE result for `mt` |
| `latticeId` | ID for a lattice of edit operation paths from `mt` to `pe` |
| `editNum` | number of edit operations required to convert `mt` to `pe`, i.e., length of each path in `paths` |
| `paths` | all possible edit operation paths from `mt` to `pe` |


The `st`, `mt` and `pe` sentences were selected from the following dataset:

- Rei Miyata (2024) MTPEdocs. https://github.com/tntc-project/MTPEdocs

For each pair of `mt` and `pe` sentences, we created its intermediate sentences in the following steps:

1. Manually extracted all edit operations from the pair.
2. Created all possible permutations of edit operations.
3. Rendered a sequence of edit operations into a sequence of intermediate sentences.


## Features

We impose the following three constraints on the edit operations (Yamaguchi et al. 2024, to appear):

- Grammaticality: "[A]n edit operation must generate a sentence with the newly rendered part having no grammatical error";
- Unswervingness: "Given a pair of sentences, the edit operation sequence for it must not contain redundant edit operations";
- Primitiveness: "[A]n edit operation as primitive iff a source side and an edited side of an edit operation form a group of minimal words related to each other".

## License

![Creative Commons License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)

* Use and/or redistribution of this dataset is permitted under the conditions of [Creative Commons Attribution-NonCommercial-ShareAlike License 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).

## Acknowledgments

Construction of the dataset was supported by JSPS KAKENHI Grant Numbers [JP19H05660](https://kaken.nii.ac.jp/en/grant/KAKENHI-PROJECT-19H05660/) and [JP23K28378](https://kaken.nii.ac.jp/en/grant/KAKENHI-PROJECT-23K28378/).

## Author and Citation

Daichi Yamaguchi, the first author of the following paper, developed this resource, discussing with the co-authors. Please cite if you use this resource.

```
@inproceedings{lreccoling-2024-yamaguchi,
  author    = {Daichi Yamaguchi and Rei Miyata and Atsushi Fujita and Tomoyuki Kajiwara and Satoshi Sato},
  title     = {Automatic Decomposition of Text Editing Examples into Primitive Edit Operations: Toward Analytic Evaluation of Editing Systems},
  booktitle = {Proceedings of the 2024 Joint International Conference on Computational Linguistics, Language Resources and Evaluation (LREC-COLING)},
  year      = {2024},
  address   = {Torino, Italia},
  pages     = {1899--1914},
  url       = {https://aclanthology.org/2024.lrec-main.170/}
}
```

