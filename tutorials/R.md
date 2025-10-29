## How to run R on Tufts HPC

This guide explains how to run R in different ways on the HPC:

- From the terminal
- Within a Slurm job script
- Through RStudio on Open OnDemand
- And how to install R packages properly in the HPC environment.

### Loading R on the Cluster

The HPC provides `R` as a module. The module is named with lower case `r` intead of `R`.
Before using R, load the module:

```
$ module spider r
$ module load r/4.5.1
```
