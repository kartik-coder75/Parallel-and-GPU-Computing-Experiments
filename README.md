# Parallel-and-GPU-Computing-Experiments
Lab Experiments
## Experiment 1: Matrix Multiplication using Sequential, OpenMP, MPI and CUDA

This experiment implements a **4000 × 4000 matrix multiplication** using four different computing models:

- Sequential CPU
- OpenMP Shared Memory
- MPI Distributed Memory
- CUDA GPU Parallelism

The same matrix multiplication problem is executed using all four approaches and their execution times are compared.

## Problem Definition

- Matrix A: 4000 × 4000, all elements = 1.0
- Matrix B: 4000 × 4000, all elements = 1.0
- Matrix C: A × B
- Expected verification value: `C[0][0] = 4000.00`

## Technologies Used

- C
- GCC
- OpenMP
- MPI
- CUDA
- WSL2 Ubuntu
- VMware Workstation
- NVIDIA GPU

## Experiment Parts

### Part A - Sequential Matrix Multiplication

The sequential implementation performs matrix multiplication using a single CPU execution flow. It is used as the baseline for comparing the performance of the parallel implementations.

**Execution Time:** 244.120000 seconds

**Verification:** `C[0][0] = 4000.00`

### Part B - OpenMP Matrix Multiplication

OpenMP is used to parallelize the matrix multiplication using multiple CPU threads on a shared-memory system.

**Number of Threads:** 8

**Execution Time:** 30.830434 seconds

**Speedup:** 7.92×

**Verification:** `C[0][0] = 4000.00`

### Part C - MPI Distributed Matrix Multiplication

MPI is used to distribute the matrix multiplication across four Ubuntu virtual machines.

- 1 Master VM
- 3 Worker VMs
- 4 MPI processes
- 1000 rows processed by each process

**Execution Time:** 92.979510 seconds

**Speedup:** 2.63×

**Verification:** `C[0][0] = 4000.00`

### Part D - CUDA Matrix Multiplication

CUDA is used to perform matrix multiplication on an NVIDIA GPU. Each CUDA thread computes one output element of the matrix.

**GPU:** NVIDIA RTX 4500 Ada Generation

**Block Size:** 16 × 16 threads

**Grid Size:** 250 × 250 blocks

**Kernel Execution Time:** 0.146443 seconds

**Total CUDA Phase Time:** 0.165004 seconds

**Speedup:** 1479.48×

**Verification:** `C[0][0] = 4000.00`

## Results and Performance Comparison

| Implementation | Computing Model | Resources | Execution Time | Speedup |
|---|---|---|---:|---:|
| Sequential | Single CPU execution | 1 CPU core | 244.120000 s | 1.00× |
| OpenMP | Shared memory | 8 CPU threads | 30.830434 s | 7.92× |
| MPI | Distributed memory | 4 processes / 4 VMs | 92.979510 s | 2.63× |
| CUDA | GPU parallelism | NVIDIA RTX 4500 Ada | 0.165004 s | 1479.48× |

## Speedup Formula

```text
Speedup = Sequential Execution Time / Parallel Execution Time
