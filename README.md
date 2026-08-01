# SFDF-YOLO: Surface Defect Detection for Rigid Curved Food Packaging

This repository provides the project page for our study on real-time surface defect detection of rigid curved food packaging. The project focuses on detecting small, low-contrast, and weak-boundary defects on packaging surfaces under industrial production-line conditions.

The proposed method, SFDF-YOLO, is designed to improve defect-sensitive feature representation by combining spatial and frequency-domain cues, same-level gated feature fusion, edge-enhanced frequency modeling, and lightweight detail-aware prediction.

## Overview

Food-packaging defect inspection in practical production lines is challenging because many packaging objects have rigid curved surfaces, complex printed textures, specular highlights, and small local defects. These factors make defect regions easy to confuse with background texture, structural edges, and illumination changes.

SFDF-YOLO is developed for surface defect detection on rigid curved food packaging, including metal cans and bottled food packages. Experiments are conducted on both the public Canned-Food Surface Defect (CFSD) dataset and our self-built RCFP-SD dataset collected from an actual food-packaging production line.

## Main Features

- Spatial-frequency dual-stream feature extraction for complementary representation of structural and frequency-domain cues.
- Same-level spatial-frequency gated fusion to adaptively combine spatial and frequency features at corresponding feature levels.
- Edge-enhanced frequency-aware representation to strengthen weak defect boundaries and local texture variations.
- Lightweight detail-aware defect head for efficient classification and localization of small surface defects.
- Evaluation on both a public canned-food defect dataset and a real production-line food-packaging defect dataset.

## Method Framework

The overall SFDF-YOLO framework contains four main components. Placeholder figures are provided below and can be replaced with the final diagrams used in the paper or supplementary materials.

<p align="center">
  <img src="figures/sfdf-yolo-framework.png" width="85%" alt="Overall framework of SFDF-YOLO">
</p>

<p align="center">
  <b>Fig. 1.</b> Overall framework of SFDF-YOLO for surface defect detection on rigid curved food packaging.
</p>

1. A YOLO-based spatial branch for multi-scale visual feature extraction.
2. A frequency-enhanced branch for frequency-domain defect representation.
3. A spatial-frequency gated fusion module for same-level feature interaction.
4. A lightweight detail-aware detection head for defect classification and bounding-box regression.

### Key Modules

The spatial-frequency dual-stream design is used to capture complementary information from spatial textures and frequency-domain responses. The following placeholder can be replaced with the detailed backbone or dual-stream feature extraction diagram.

<p align="center">
  <img src="figures/spatial-frequency-dual-stream.png" width="80%" alt="Spatial-frequency dual-stream feature extraction">
</p>

<p align="center">
  <b>Fig. 2.</b> Spatial-frequency dual-stream feature extraction.
</p>

The same-level spatial-frequency gated fusion module adaptively estimates the relative contributions of spatial and frequency features at corresponding feature levels.

<p align="center">
  <img src="figures/sfgf-module.png" width="75%" alt="Same-level spatial-frequency gated fusion module">
</p>

<p align="center">
  <b>Fig. 3.</b> Same-level spatial-frequency gated fusion module.
</p>

The lightweight detail-aware defect head further enhances local defect cues before classification and bounding-box regression.

<p align="center">
  <img src="figures/lddh-module.png" width="75%" alt="Lightweight detail-aware defect head">
</p>

<p align="center">
  <b>Fig. 4.</b> Lightweight detail-aware defect head.
</p>

Implementation details, trained weights, and additional reproduction materials will be updated in this repository according to the paper publication and project release schedule.

## Datasets

### CFSD Dataset

The public Canned-Food Surface Defect (CFSD) dataset is used to evaluate the detection performance of SFDF-YOLO on public canned-food defect data.

- Source: Roboflow Universe
- Dataset name: Canned-food-surface-defect dataset
- Number of images: 8046
- Categories: Critical Defect, Major Defect, Minor Defect, and No defect
- Annotation format: YOLO format with bounding boxes and category labels
- Data split: training/validation/test sets with a ratio of 7:2:1

Dataset link: https://universe.roboflow.com/canned-food-surface-defect-classification/canned-food-surface-defect

### RCFP-SD Dataset

RCFP-SD is a self-built rigid curved food packaging surface defect dataset collected from an actual food-packaging production line. It is used to evaluate the adaptability of SFDF-YOLO to real industrial inspection scenarios.

The acquisition system consists of an industrial camera, directional LED illumination, and an online image acquisition terminal. Packaging objects continuously pass through the inspection region at a production-line speed of approximately 80 items/min.

Basic statistics:

| Item | Description |
| --- | --- |
| Total images | 4200 |
| Image resolution | 1920 x 1080 |
| Object types | Metal cans and bottled food packages |
| Metal-can images | 2200 |
| Bottle-package images | 2000 |
| Defect categories | Scratch, Surface, Graphic, Structure |
| Normal samples | Included |
| Annotation tool | Labelme |
| Released annotation format | YOLO format |

Class distribution:

| Class | Metal Can | Bottle Package |
| --- | ---: | ---: |
| Scratch | 447 | 394 |
| Surface | 487 | 431 |
| Graphic | 493 | 420 |
| Structure | 359 | 387 |
| Normal | 414 | 368 |

Each defective image contains one annotated defect instance, whereas defect-free images contain no defect annotations. The annotations are converted to YOLO format, where each annotation contains the category index and normalized bounding-box coordinates.

Representative samples:

<p align="center">
  <img src="figures/rcfp-sd-sample-1.png" width="30%" alt="Representative sample 1 from the RCFP-SD dataset">
  <img src="figures/rcfp-sd-sample-2.png" width="30%" alt="Representative sample 2 from the RCFP-SD dataset">
  <img src="figures/rcfp-sd-sample-3.png" width="30%" alt="Representative sample 3 from the RCFP-SD dataset">
</p>

<p align="center">
  <b>Fig. 5.</b> Representative samples from the RCFP-SD dataset.
</p>

## Data Access

The RCFP-SD dataset was collected from a real industrial food-packaging production line. Some images involve actual production scenarios and therefore require necessary data desensitization and confirmation of the permitted use scope before public release.

At the current stage, the complete RCFP-SD dataset is not directly available for unrestricted public download. Researchers with a clear academic or non-commercial research purpose may request access through this repository. After the research purpose and intended use are confirmed, dataset access support can be provided.

To request access, please open a GitHub issue or contact the authors by email at `anzhaoyu_sp@163.com` with the following information:

- Name and affiliation
- Research purpose
- Intended use of the dataset
- Whether the dataset will be used only for non-commercial research
- Agreement not to redistribute the dataset without permission

## Experimental Results

The main results reported in the paper are summarized below.

| Dataset | Metric | SFDF-YOLO |
| --- | --- | ---: |
| CFSD | AP50 | 97.6% |
| CFSD | AP50:95 | 75.6% |
| RCFP-SD | mAP50 | 95.6% |
| RCFP-SD | mAP50:95 | 84.0% |

Compared with YOLOv11n, SFDF-YOLO improves AP50 and AP50:95 by 3.1 and 6.8 percentage points on CFSD, and improves mAP50 and mAP50:95 by 3.5 and 7.4 percentage points on RCFP-SD.

Detailed comparison experiments, ablation studies, statistical validation, and embedded deployment tests are provided in the paper.

## Repository Status

| Resource | Status |
| --- | --- |
| Project overview | Available |
| Dataset description | Available |
| RCFP-SD access request channel | Available |
| Sample images | To be updated |
| Source code | To be released after paper acceptance, subject to project release policy |
| Trained weights | To be released after paper acceptance, subject to project release policy |
| Additional reproduction materials | To be updated |

## Citation

If this project or dataset is useful for your research, please cite our paper. The formal citation information will be updated after publication.



## Contact

For questions about the project, dataset access, or future updates, please contact the authors through GitHub Issues or by email at `anzhaoyu_sp@163.com`.
# SFDF-YOLO
