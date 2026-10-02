# Lab files

These are the files used in the NCP-AIN Hands-On Lab Guide. Click a file to download it. If your browser opens it as text instead, right-click the link and choose **Save link as…**.

[Download all lab files (.zip)](ncp-ain-lab-files.zip){ .md-button .md-button--primary download="ncp-ain-lab-files.zip" }

| File | Used in | What it is |
|---|---|---|
| [helix-b-air.json](helix-b-air.json){ download="helix-b-air.json" } | Lab 0 | NVIDIA DSX Air topology: 2 spines, 4 rail leaves (Cumulus VX), 4 Ubuntu "GPU" servers, an InfiniBand simulator node and the OOB network. It fits the Air free trial. |
| [helix-b-air-bare.json](helix-b-air-bare.json){ download="helix-b-air-bare.json" } | Lab 0 (fallback) | The same topology in Air's minimal JSON format. Use it if the main file fails to import. |
| [helix-a.net](helix-a.net){ download="helix-a.net" } | Lab 8 | ibsim fabric file: 2 spines, 4 leaves, 4 GPU nodes with 2 HCAs each, and two UFM hosts. |
| [partitions.conf](partitions.conf){ download="partitions.conf" } | Lab 8 | OpenSM partitions: RESEARCH 0x8001, PRODUCTION 0x8002, SHARED 0x0100 (limited). |

To import `helix-b-air.json` in Air, choose **Create Simulation → Import JSON**.

The files are also in the [GitHub repository](https://github.com/Cloudfoxy-Ltd/ncp-ain-guide/tree/main/site-src/lab-files). They're released under the [MIT licence](../license.md).
