<table style="width:100%">
  <tr>
    <th width="100%" colspan="5"><h2>SC17 Xilinx Developer Lab</h2></th>
  </tr>
  <tr>
    <td width="20%" align="center"><a href="README.md"><b>1. Introduction</b></a></td>
    <td width="20%" align="center"><a href="SETUP.md">2. Connecting to your F1 instance</a></td> 
    <td width="20%" align="center"><a href="FFMPEG_Lab.md">3. Experiencing F1 acceleration</a></td>
    <td width="20%" align="center"><a href="IDCT_Lab.md">4. Developing F1 applications</a></td>
    <td width="20%" align="center"><a href="WRAP_UP.md">5. Wrapping-up</td>
  </tr>
</table>

---------------------------------------
### Introduction

Welcome to the SC17 Xilinx Developer Lab. During this session you will gain hands-on experience with AWS F1 and learn how to develop accelerated applications using the AWS F1 OpenCL flow and the Xilinx SDAccel development environment.

#### Overview of the AWS F1 platform

Some explanation of F1 (CPU+FPGA)

#### Overview of the SDAccel flow

Some explanation of SDAccel flow (Application on host CPU + Kernels on the FPGA (AFI))

#### Modules

This developer lab is divided in 4 modules. It is recommended to complete each module before proceeding to the next.

1. **Connecting to your F1 instance** \
You will start a pre-configured EC2 F1 instance and connect to it using a remote desktop client. Once connected, you will download the Lab files and confirm you can execute a simple application on F1.
1. **Experiencing F1 acceleration** \
AWS F1 instances are ideal to accelerate complex workloads. In this module you will experience the potential of F1 by using FFmpeg to run both a software implementation and an F1-optimized implementation of an H.265/HEVC encoder. 
1. **Developing and optimizing F1 applications with SDAccel** \
You will use the SDAccel development environment to create, profile and optimize an F1 accelerator. The lab focuses on the Inverse Discrete Cosine Transform (IDCT), a compute intensive function used at the heart of all video codecs.
1. **Wrap-up and stopping your F1 instance** \
bla bla bla.

---------------------------------------

[**Start Module 2: Connecting to your F1 instance**](Setup.md)
