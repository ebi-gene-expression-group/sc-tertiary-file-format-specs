# Cell cluster definitions

## Motivation

Many tools in single-cell RNA seq analysis define clusters at some point of their workflow. The manner and mechanism in which those definitions are stored is the subject of this document, which will become a specification.

## Opening questions

### Is an isolated clustering specification desirable?

Clustering specifications are simple compared to e.g. trajectories, potentially just a two-column table. This being the case, is a clustering format specification desirable at all? If clusters are effectively just cell-wise metadata, would effort perhaps be better spent in standardising cell-wise metadata in the specifications used for expression matrices?

### Should metadata be stored along with clustering definitions?

Clustering is a complex process with diverse methods having diverse parameterisations. Understanding clustering outputs requires some understanding of thos parameterisations. Does this mean we should package clustering method metadata along with the cluster definitions? This is probably a consideration that should be kept separate given its complexity, but the question deserves to be asked.

### Should we allow for probabilistic cluster assignment of cells?

It is easy to imagine methods that assign cells to clusters with less than 100 percent certainty, which would allow for cells to part of multiple clusters with different probabilities. Is this something we should bake into any specification?

## Format possibilities

The following are possible directions for a clustering specification (assuming an isolated format is deemed necessary- see above). 

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
* Does this even need a specification?

Rules:

* Cell and cluster names should not contain commas

### Option 2: store multiple cluster definitions in one file

There may be a case for storing multiple cluster definitions in one file, for example from multiple parameterisations of the same method:

```
Cell,cluster_k_2,cluster_k_3
cell_1,cluster_2,cluster_1
cell_2,cluster_1,cluster_3
cell_3,cluster_1,cluster_2
cell_4,cluster_2,cluster_3
cell_5,cluster_2,cluster_1
...
```

Questions:

* There would be complexity here- for example in defining the metadata behind each parameterisation. Is this desirable?

### Option 3: probabilistic assignments

If cells are proabilitically assigned to multiple clusters the format looks like:

```
Cell,cluster,prob
cell_1,cluster_2,0.8
cell_1,cluster_3,0.2
cell_2,cluster_1,1
cell_3,cluster_1,0.3
cell_3,cluster_3,0.3
cell_3,cluster_2,0.4
cell_4,cluster_2,0.5
cell_4,cluster_3,0.5
cell_5,cluster_2,1
```

Clearly this option precludes option 2.

