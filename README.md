# Spot Traces

This repository contains spot availability and preemption traces collected from the cloud providers and the scripts to collect and process the traces. 

The data was used in paper *Can't Be Late: Optimizing Spot Instance Savings under Deadlines with SkySpot* (NSDI 24). The policy in the paper is prototyped on [SkyPilot](https://github.com/skypilot-org/skypilot).


## Data Description

We collected the spot instance availability and preemption traces by directly pinging the cloud providers. The traces contain the following information:

```jsonc
{
  "metadata": {
    // The interval seconds between two consecutive data points
    "gap_seconds": 300,
  },
  // A trace of spot instance availability or preemption, where each data point
  // is the number of available instances at a specific tick.
  "data": []
}
```
## Availability Traces

### Single Node
#### 2-week availability trace for V100/K80 on AWS

The 2-week (13 days) availability trace started on 10/26/2022 for K80 and V100 GPUs.

* Start date: 10/26/2022
* Instance types: `p3.2xlarge`/`p3.16xlarge` (1/8 V100), `p2.2xlarge`/`p2.16xlarge` (1/8 K80)
* Availability zones: `us-west-2a` and `us-west-2b`
* Data path: [availability/1-node/aws-10-26-2022](availability/1-node/aws-10-26-2022).

#### 2-month availability trace for V100 on AWS

The 2-month (45 days) availability trace started on 02/15/2023 for V100 GPUs.

* Start date: 02/15/2023
* Instance types: `p3.2xlarge` (1 V100)
* Availability zones: all 9 regions in `us-east-1`, `us-east-2`, and `us-west-2`
* Data path: [availability/1-node/aws-02-15-2023](availability/1-node/aws-02-15-2023).

###  Multi-node

#### 2-week availability trace for 16-node for V100 on AWS

The 2-week (11/16 days) availability trace started on 08/27/2023 for V100 GPUs with multi-node.

* Start date: 08/27/2023
* Instance types: `p3.2xlarge` (1 V100)
* Availability zones: `us-east-2b`, `us-west-2a`, and `us-west-2c`
* Data path: [availability/16-node/aws-08-27-2023](availability/16-node/aws-08-27-2023).


## Preemption Traces

### Single Node

#### 1-week preemption trace for V100 on AWS

The 1-week (7 days) preemption trace started on 04/22/2023 for V100 GPUs on AWS.
This trace is used for ML workloads.

* Start date: 04/22/2023
* Instance types: `p3.2xlarge` (1 V100)
* Availability zones: `us-east-1c`, `us-east-1f`, `us-west-2b`, and `us-west-2c`
* Data path: [preemption/1-node/aws-04-22-2023](preemption/1-node/aws-04-22-2023).

#### 2-day preemption trace for Intel CPU on GCP

The 2-day preemption trace started on 04/30/2023 for Intel CPUs on GCP.

This trace is used for Bioinformatics workloads.

* Start date: 04/30/2023
* Instance types: `c3-highcpu-88` (88 vCPUs)
* Availability zones: `us-central1-a`, `us-central1-b`, `us-central1-c`, and `us-east1-b`
* Data path: [preemption/1-node/gcp-04-30-2023](preemption/1-node/gcp-04-30-2023).

#### 1-week preemption trace for Intel CPU on AWS

The 1-week (7 days) preemption trace started on 05/01/2023 for Intel CPUs on AWS.

This trace is used for Data Analytics workloads.

* Start date: 05/01/2023
* Instance types: `r5.16xlarge` (64 vCPUs)
* Availability zones: `us-east-1b`, `us-east-1c`, and `us-east-1d`
* Data path: [preemption/1-node/aws-04-19-2023](preemption/1-node/aws-04-19-2023).


### Multi-node
#### 2-week preemption trace for 4-node for V100 on AWS

The 2-week (13 days) preemption trace started on 08/03/2023 for V100 GPUs on AWS.

* Start date: 08/03/2023
* Instance types: `p3.2xlarge` (1 V100)
* Availability zones: `us-east-1f`, `us-east-2a`, and `us-west-2c`
* Data path: [preemption/4-node/aws-08-03-2023](preemption/4-node/aws-08-03-2023).

## Citation

```
@inproceedings{wu2024skyspot,
  title={Can't Be Late: Optimizing Spot Instance Savings under Deadlines},
  author={Wu, Zhanghao and Chiang, Wei-Lin and Mao, Ziming and Yang, Zongheng and Friedman, Eric and Shenker, Scott and Stoica, Ion}
  booktitle = {21th USENIX Symposium on Networked Systems Design and Implementation (NSDI 24)},
  year = {2024}
}
```
