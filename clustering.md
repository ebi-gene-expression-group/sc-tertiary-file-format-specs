# Cell cluster definitions

## Motivation

Many tools in single-cell RNA seq analysis define clusters at some point of their workflow. The mechanism by which these clusters are defined could be a trivial two-column table (cell, cluster), or more complex. The following are possible directions for defining this specification:

### Option 1: minimal two-column csv

Simple definintion to define clusters only, in one definition only.

```
Cell,cluster
cell_1,cluster_2
cell_2,cluster_1
cell_3,cluster_2
cell_4,cluster_3
cell_5,cluster_1
...
```

Questions:

* Do we even need a header?

Rules:

* Cell and cluster names should not contain commas

### Option 2: store multiple cluster definitions in one file


