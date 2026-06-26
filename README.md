# Intrinsic Neural Firewalls for Cyber-Physical Systems

This repository contains the official implementation of the Deep Delta Learning Firewall (DDL-FW) as presented in the WIN 6.0 2026 conference paper: **"Intrinsic Neural Firewalls for Cyber-Physical Systems: Robust Anomaly Rejection via Deep Delta Residual Overwrites"**.

## Overview

Modern Industrial Cyber-Physical Systems heavily leverage Web 6.0 communication fabrics, thus creating a practical opportunity for False Data Injection Attacks (FDIA). The adversary generates statistically plausible measurements, misleading deep-learning-based intrusion detection. External detectors suffer from latencies, need pre-labeled attack data, and cannot prevent internal corruption of the state.

This work proposes Deep Delta Learning Firewall (DDL-FW), an intrinsic defense architecture designed specifically for CPS, which is not dependent on any attack examples during training. While other defenses typically employ an additional detector, DDL-FW integrates the defense functionality directly in the residual connections, substituting a simple addition of the residual to the state vector with a depth-wise read-compare-write routine, based on the principles of Deep Delta Learning (DDL). 

## Key Features

* Every transformer block obtains the ability to explicitly reject anomalous input instead of absorbing it.
* Training on clean sequences of observations, DDL-FW produces anomaly scores at zero overhead as a result of residual errors accumulation through layers.
* Four channels of the extended residual state ensure the quarantine of adversarial perturbation on layer borders and stop its propagation into the global memory stream.

## Dataset

Experiments were conducted using the benchmark of HAI 21.03, including 79 sensors distributed between turbine, boiler, and water treatment systems. 

## Performance

Compared to inferior results of Isolation Forest, One-Class SVM, and statistical baselines by large margins, the attack-agnostic, zero-shot framework achieves the following metrics:
* DDL-FW exhibits an F1 score of 0.7206.
* DDL-FW maintains a false positive rate of 2.01%.
* The architecture is highly efficient, being 1.3M parameters only.
