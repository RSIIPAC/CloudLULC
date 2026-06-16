# CloudLULC-Net: Heterogeneous SAR–Optical Fusion for Near-Real-Time LULC Mapping under Cloud Contamination

## Heterogeneous SAR–Optical Fusion for Near-Real-Time Land Use and Land Cover Mapping under Cloud Contamination: A Novel Framework and Global Benchmark Dataset

**Jiangong Xu, Weibao Xue, Xiaoyu Yu, Jun Pan, Xinlian Liang, Mi Wang**

[![Project](https://img.shields.io/badge/Project-CloudLULC--Net-blue)](https://github.com/RSIIPAC/CloudLULC)
[![Dataset](https://img.shields.io/badge/Dataset-CloudLULC--Set-green)](https://github.com/RSIIPAC/CloudLULC)
[![Task](https://img.shields.io/badge/Task-Cloud--contaminated%20LULC%20Mapping-orange)](https://github.com/RSIIPAC/CloudLULC)
[![Sensors](https://img.shields.io/badge/Sensors-Sentinel--1%20%2F%20Sentinel--2-lightgrey)](https://github.com/RSIIPAC/CloudLULC)

---

## Overview

Cloud contamination is a persistent obstacle for optical remote sensing, especially when land use and land cover (LULC) maps are expected to represent the target-date or near-real-time land-surface state. Optical imagery provides rich spectral and textural information, but clouds and cloud shadows often obscure land-surface signals and introduce semantic uncertainty. Synthetic aperture radar (SAR), by contrast, can acquire cloud-insensitive microwave observations and provide complementary structural and backscattering information.

This repository provides the official implementation and project materials for **CloudLULC-Net**, an end-to-end heterogeneous SAR–optical fusion framework for near-real-time LULC mapping under cloud-contaminated conditions.

Different from reconstruction-first pipelines that first restore cloud-contaminated optical imagery and then perform classification, CloudLULC-Net directly predicts pixel-level LULC maps from:

* cloud-contaminated Sentinel-2 optical imagery;
* temporally adjacent Sentinel-1 SAR observations;
* task-oriented heterogeneous semantic representations.

The framework is designed to suppress unreliable optical responses, exploit SAR-derived structural cues, and organize fused SAR–optical features in a LULC-oriented semantic latent space.

---

## Framework

![CloudLULC-Net framework](https://github.com/RSIIPAC/CloudLULC/blob/main/Subsidiaries/conceptual.png)

CloudLULC-Net contains four key components:

1. **Optical Reliability Modulation (ORM)**
   ORM learns feature-level optical reliability from cloud-contaminated optical representations. It adaptively reduces unreliable optical responses in cloud-covered, cloud-shadow, or haze-affected regions while preserving useful spectral and textural cues in clear or weakly contaminated areas.

2. **Heterogeneous Information Adaptive Aggregation (HIAA)**
   HIAA progressively integrates SAR and optical representations through high-order spatial–channel interaction. It includes:

   * Spatial High-Order Interaction (SHOI), which models long-range cross-modal spatial dependencies;
   * Channel High-Order Interaction (CHOI), which recalibrates heterogeneous spectral–structural channel responses.

3. **Unified Semantic Mapping Transformer (USMT)**
   USMT maps fused SAR–optical tokens into a LULC-oriented semantic latent space. Instead of reconstructing cloud-free optical images, it focuses on task-oriented semantic representation learning for dense LULC prediction.

4. **Semantic Anchor-Guided Optimization**
   A label-derived semantic anchor is used during training to regularize the intermediate semantic latent representation, improving the consistency and robustness of LULC predictions under varying cloud conditions.

---

## Key Contributions

* We formulate **near-real-time LULC mapping under cloud contamination** as a heterogeneous SAR–optical fusion problem.
* We construct **CloudLULC-Set**, a large-scale benchmark dataset for cloud-contaminated SAR–optical LULC mapping.
* We propose **CloudLULC-Net**, an end-to-end SAR–optical fusion framework that directly predicts LULC maps from cloud-contaminated optical imagery and temporally adjacent SAR observations.
* We design **optical reliability modulation** and **high-order heterogeneous interaction** modules to adaptively integrate degraded optical features and SAR structural information.
* We introduce a **unified semantic mapping transformer** and **semantic anchor-guided optimization** strategy to align fused SAR–optical features with a LULC-oriented semantic latent space.

---

## CloudLULC-Set

To support target-date LULC mapping under real cloud-contaminated conditions, we construct **CloudLULC-Set**, a large-scale SAR–optical benchmark dataset.

CloudLULC-Set contains:

* cloud-contaminated Sentinel-2 optical imagery;
* temporally adjacent Sentinel-1 SAR imagery;
* temporally close cloud-free or near-cloud-free Sentinel-2 reference imagery for annotation and quality inspection;
* pixel-level LULC annotations;
* fixed training, validation, and testing splits.

![CloudLULC-Set overview](https://github.com/RSIIPAC/CloudLULC/blob/main/Subsidiaries/location.png)

### Dataset Statistics

| Item               | Description                                                    |
| ------------------ | -------------------------------------------------------------- |
| Dataset name       | CloudLULC-Set                                                  |
| Optical data       | Sentinel-2 Level-2A surface reflectance                        |
| Optical bands      | B1, B2, B3, B4, B5, B6, B7, B8, B8A, B9, B11, B12              |
| SAR data           | Sentinel-1 GRD                                                 |
| SAR channels       | VV and VH                                                      |
| Spatial resolution | 10 m                                                           |
| Patch size         | 512 × 512                                                      |
| Number of triplets | 40,223                                                         |
| Spatial coverage   | approximately 578,690 km²                                      |
| LULC classes       | Water, Forest, Grassland, Barren land, Built-up land, Cropland |

### LULC Taxonomy

CloudLULC-Set adopts a unified six-class LULC taxonomy:

| Class         | Description                                                         |
| ------------- | ------------------------------------------------------------------- |
| Water         | Rivers, lakes, reservoirs, ponds, and other visible water bodies    |
| Forest        | Natural forests, plantations, and other tree-covered areas          |
| Grassland     | Herbaceous vegetation-dominated areas                               |
| Barren land   | Bare soil, exposed rock, sand, and sparsely vegetated surfaces      |
| Built-up land | Buildings, roads, industrial areas, and other impervious surfaces   |
| Cropland      | Paddy fields, dryland crops, and other managed agricultural parcels |

---

## Dataset Download

The CloudLULC-Set dataset can be downloaded from the following link:

**[Download CloudLULC-Set](https://www.wenjuan.com/s/JnyMzq1/#)**

After downloading the dataset, please organize the files following the structure below.

```text
./
+-- CloudLULC-Set
    +-- SAR_S1
    |   +-- VH
    |   |   +-- patch_ROIs_01_name.tif
    |   |   +-- ...
    |   +-- VV
    |       +-- patch_ROIs_01_name.tif
    |       +-- ...
    |
    +-- Opt_S2_cloudy
    |   +-- patch_ROIs_01_name.tif
    |   +-- ...
    |
    +-- Opt_S2_clear
    |   +-- patch_ROIs_01_name.tif
    |   +-- ...
    |
    +-- Label
    |   +-- patch_ROIs_01_name.tif
    |   +-- ...
    |
    +-- split
        +-- train.csv
        +-- val.csv
        +-- test.csv
```

The split files provide the sample list for training, validation, and testing. A typical split record is organized as follows:

```text
split_id    sar_vh                  sar_vv                  opt_cloudy              opt_clear                label
1           SAR_S1/VH/name.tif       SAR_S1/VV/name.tif       Opt_S2_cloudy/name.tif  Opt_S2_clear/name.tif    Label/name.tif
2           SAR_S1/VH/name.tif       SAR_S1/VV/name.tif       Opt_S2_cloudy/name.tif  Opt_S2_clear/name.tif    Label/name.tif
3           SAR_S1/VH/name.tif       SAR_S1/VV/name.tif       Opt_S2_cloudy/name.tif  Opt_S2_clear/name.tif    Label/name.tif
```

where:

* `1` denotes the training set;
* `2` denotes the validation set;
* `3` denotes the testing set.

---

## Code Release

The source code, pretrained model weights, and detailed training / inference instructions will be publicly released in this repository after the manuscript is accepted for publication. During the review stage, this repository serves as the official project page for presenting the dataset information, methodological overview, and related project materials.

The planned repository structure is:

```text
./
+-- configs
|   +-- cloudlulcnet.yaml
|
+-- datasets
|   +-- cloudlulc_dataset.py
|
+-- models
|   +-- cloudlulc_net.py
|   +-- modules
|       +-- orm.py
|       +-- hiaa.py
|       +-- usmt.py
|
+-- tools
|   +-- train.py
|   +-- test.py
|   +-- inference.py
|
+-- utils
|   +-- metrics.py
|   +-- visualization.py
|
+-- Subsidiaries
|   +-- conceptual.png
|   +-- location.png
|
+-- README.md
```

---

## Results

CloudLULC-Net is evaluated on CloudLULC-Set under a unified benchmark protocol. The experiments include:

* comparison with heterogeneous reconstruction-first methods;
* comparison with end-to-end SAR–optical fusion methods;
* class-wise IoU and F1-score analysis;
* product-level validation against existing global LULC products;
* cloud-coverage-stratified analysis;
* input-modality analysis;
* ablation studies of ORM, HIAA, USMT, and semantic anchor-guided optimization.

The complete quantitative results are reported in the manuscript. The result tables in this repository will be synchronized with the final accepted version.

---

## Citation

If this project is useful for your research, please consider citing our work:

```bibtex
@article{xu2026cloudlulc,
  title   = {Heterogeneous SAR--optical fusion for near-real-time land use and land cover mapping under cloud contamination: A novel framework and global benchmark dataset},
  author  = {Xu, Jiangong and Xue, Weibao and Yu, Xiaoyu and Pan, Jun and Liang, Xinlian and Wang, Mi},
  journal = {ISPRS Journal of Photogrammetry and Remote Sensing},
  year    = {2026},
  note    = {Under review}
}
```

---

## Contact

If you have any questions about this work, please contact us:

* Jiangong Xu: **[dd_xjg@whu.edu.cn](mailto:dd_xjg@whu.edu.cn)**
* Jun Pan: **[panjun1215@whu.edu.cn](mailto:panjun1215@whu.edu.cn)**

---

## Acknowledgements

We gratefully acknowledge the European Space Agency for providing Sentinel-1 and Sentinel-2 satellite imagery.

This work was supported by the National Natural Science Foundation of China under Grants **62371352** and **62425102**.
