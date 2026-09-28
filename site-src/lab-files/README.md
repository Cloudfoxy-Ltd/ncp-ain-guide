# Lab files for the NCP-AIN Hands-On Lab Guide

| File | Used in | What it is |
|---|---|---|
| `helix-b-air.json` | Lab 0 | NVIDIA DSX Air topology: 2 spines, 4 rail leaves (Cumulus VX), 4 Ubuntu "GPU" servers, an InfiniBand simulator node, OOB network. Fits the Air free trial. |
| `helix-a.net` | Lab 8 | ibsim fabric file: 2 spines, 4 leaves, 4 GPU nodes × 2 HCAs, two UFM hosts |
| `partitions.conf` | Lab 8 | OpenSM partitions: RESEARCH 0x8001, PRODUCTION 0x8002, SHARED 0x0100 (limited) |

Import `helix-b-air.json` in Air with **Create Simulation → JSON**.
