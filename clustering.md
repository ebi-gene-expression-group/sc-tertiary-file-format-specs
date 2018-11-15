# Cell cluster definitions

Many tools in single-cell RNA seq analysis define clusters at some point of their workflow. This specification defines a format to be used to specify those clusters. This is an example format to be used as the basis for discusssion and ratification by the community. 

## Scope

This is a 'consumer level' format. That is, it is likely to be used as the end product of clustering workflows. We expect that internal to a workflow, clusters will be stored as part of the overall project schema (e.g. in Loom, R objects etc).

## Format

Suggested cluster specification is simply:

```
Cell    clustering_1   clustering_2,...
cell_1  cluster_2    cluster_3,
cell_2  cluster_1    cluster_2,
cell_3  cluster_2    cluster_1,
cell_4  cluster_3    cluster_2,
cell_5  cluster_1    cluster_1,
...
```

This example illustrates the following design decisions:

* A tab-separated file with cells by row and clusterings by column.
* Format to store cluster assignments only. Specification of clusters as part of a trajectory-centric format was considered but rejected.
* No probalistic assignment necessary since this is not currently a common feature of tools.
* Multiple cluster assignments to be allowed based on different methods or parameterisations.




