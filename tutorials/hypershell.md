## Introduction

HyperShell is an elegant, cross-platform, high-throughput computing utility for processing shell commands over a distributed, asynchronous queue. It is a highly scalable workflow automation tool for many-task scenarios.
It was developed by Geoffrey Lentner, who is currently working as the lead research data scientist at Rosen Center for Advanced Computing at Purdue University. So hypershell is developed by a hpc specialist to help users run jobs efficiently on HPC.

The idea is simple - make a manifest of things to do (literally a file with 10000 commands), and create a pool of workers that feed from that manifest (XX at a time). And write successes/failures into corresponding files. Then if/when a hyper-shell run is restarted (with the same manifest/success/failure files), it'd just resume from where it left off.

## High-Throughput many-task computing

- Larget number of indepedent tasks without communication.
- Elements of the workflow can run anywhere.

## Why not use array from the slurm scheduler

### Pratical limits

HPC administrators don't want users:

- Submitting millions of jobs
- Filling up the database
- impacting site-wide throughtput, and
- polluting the queue

#### Limits of Tufts HPC

Our cluster does not allow users to submit > 1000 jobs.

##### CPUs, RAM and GPUs

```
Public Partitions (batch+mpi+largemem+gpu)
CPU: 1000 cores
RAM: 4000 GB
GPU: 10

Preempt Partition (preempt)
CPU: 2000 cores
RAM: 8000 GB
GPU: 20
```

Please note that the above limits are subject to change in the future. To ensure optimal resource allocation, the limit value is dynamic and may change as we evaluate system demands.
