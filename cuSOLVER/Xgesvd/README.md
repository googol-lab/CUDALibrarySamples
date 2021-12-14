# cuSOLVER Singular Value Decomposition example

## Description

This code demonstrates a usage of cuSOLVER Xgesvd 64-bit functions for using cusolverDnXgesvd

_**A** = **U** * **&Sigma;** * **V**<sup>H</sup>_

All matrices A<sub>i</sub> are small perturbations of
```
A = | 1.0 | 2.0 |
    | 4.0 | 5.0 |
    | 2.0 | 1.0 |
```

The following code uses three steps:

Step 1: compute A = U * S * VT

Step 2: check accuracy of singular value

Step 3: measure residual A - U * S * VT

## Supported SM Architectures

All GPUs supported by CUDA Toolkit (https://developer.nvidia.com/cuda-gpus)  

## Supported OSes

Linux  
Windows

## Supported CPU Architecture

x86_64  
ppc64le
arm64-sbsa

## CUDA APIs involved
- [cusolverDnXgesvd_bufferSize API](https://docs.nvidia.com/cuda/cusolver/index.html#cuSolverDnXgesvd)
- [cusolverDnXgesvd API](https://docs.nvidia.com/cuda/cusolver/index.html#cuSolverDnXgesvd)

# Building (make)

# Prerequisites
- A Linux/Windows system with recent NVIDIA drivers.
- [CMake](https://cmake.org/download) version 3.18 minimum
- Minimum [CUDA 11.1 toolkit](https://developer.nvidia.com/cuda-downloads) is required.

## Build command on Linux
```
$ mkdir build
$ cd build
$ cmake ..
$ make
```
Make sure that CMake finds expected CUDA Toolkit. If that is not the case you can add argument `-DCMAKE_CUDA_COMPILER=/path/to/cuda/bin/nvcc` to cmake command.

## Build command on Windows
```
$ mkdir build
$ cd build
$ cmake -DCMAKE_GENERATOR_PLATFORM=x64 ..
$ Open cusolver_examples.sln project in Visual Studio and build
```

# Usage
```
$  ./cusolver_Xgetrf_example
```

Sample example output:

```
A = (matlab base-1)
1 2 0
4 5 3.21143e-322
2 1 0
=====
after gesvd: info_gpu = 0
=====
S = (matlab base-1)
7.06528
1.63042e-322
=====
U = (matlab base-1)
-0.308219 -0.906133 -0.289695
0.488195 0.110706 -0.865685
0.816497 -0.408248 0.408248
=====
VT = (matlab base-1)
-0.638636 -0.769509
-0.769509 0.638636
=====
|S - S_exact| = 7.065283E+00
|A - U*S*VT| = 1.790181E-15
```