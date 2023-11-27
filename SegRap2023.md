# SegRap2023: A Benchmark of Organs-at-Risk and Gross Tumor Volume Segmentation for Radiotherapy Planning of Nasopharyngeal Carcinoma

Radiation therapy is a primary and effective treatment strategy for nasopharyngeal carcinoma (NPC). The precise delineation of the gross tumor volume (GTV) and organs at risk (OARs) is crucial during the radiation treatment process for NPC, directly impacting patient treatment outcomes and prognosis. Previously, the delineation of GTVs and OARs was performed by experienced radiation oncologists. Recently, deep learning has achieved promising results in many medical image segmentation tasks. However, for NPC's OARs and GTVs, few public datasets are available for model development and evaluation. To advance research in this area, the Segmentation of Organs-at-Risk and Gross Tumor Volume Segmentation for Nasopharyngeal Carcinoma Radiation Therapy Planning Challenge (SegRap2023) was organized in conjunction with MICCAI2023. SegRap2023 represents the first large-scale benchmark for OARs and GTVs, providing 400 CT scans from 200 NPC patients, each with a pair of pre-aligned non-contrast and contrast-enhancement scans. The challenge's goal was to accurately segment 45 OARs and 2 GTVs from the paired CT scans, a task made challenging by the significant differences in OAR/GTV size, ambiguous boundaries, and class imbalance. In this paper, we detail the challenge and analyze the solutions of all participants. The average Dice scores for the submitted solutions ranged from 0.7668 to 0.8670 for OARs segmentation and from 0.7042 to 0.7344 for GTVs segmentation. Based on these results, we argue that while segmentation of large-size OARs is well-addressed, greater focus should be placed on GTVs and small-size or thin-structure OARs to better support clinical practice.

<div align="center">
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/SegRap2023_main.png"></a>
</div>



## ✨ Overview

- We built a new clinical organs-at-risk and gross tumor volume segmentation dataset (400 CT scans from 200 NPC patients) that has more categories (45 organs and 2 GTVs) and high-quality annotations than previous works.

- We provide several organs-at-risk and gross tumor volume segmentation methods by (1) evaluating the baseline method using [nnUNet](https://github.com/MIC-DKFZ/nnUNet), (2) summarizing and analyzing the solutions from more than ten participant teams. 

  

## 🛠️ Description of Dataset

The SegRap2023 dataset consists of 200 newly treated nasopharyngeal carcinoma patients from Sichuan Cancer Hospital & Institute, Sichuan Cancer Center, Chengdu, China. The data acquisition was approved by the Sichuan Cancer Hospital & Institute ethics board and the private information of each patient has been anonymized. Each patient has a non-contrast CT scan and a contrast-enhanced CT scan. All CT scans are collected by Siemens CT scanners with the following scanning conditions: bulb voltage, 120 kV; current, 300 mA; scan thickness, 3.0 mm; resolution, 1024×1024 or 512×512; injected contrast agent, iohexol (volume, 60-80 mL; rate, 2 mL/s; delay, 50 s). The clinical characteristic of the SegRap2023 dataset are listed below.

<div align="center">
    <a href="https://"><img width="480px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/SegRap2023_clinical.jpg"></a>
</div>


All scans of SegRap2023 dataset are exhaustively annotated with 45 OARs and 2 GTVs, including Brain, BrainStem, Chiasm, Cochlea left (Cochlea\_L), Cochlea right (Cochlea\_R), Esophagus, Eustachian tube bone left (ETbone\_L), Esophagus, Eustachian tube bone right (ETbone\_R), Eye left (Eye\_L), Eye right (Eye\_R), Hippocampus left (Hippocampus\_L), Hippocampus right(Hippocampus\_R), Internal auditory canal left (IAC\_L), Internal auditory canal right  (IAC\_R), Larynx, Larynx glottic, Larynx supraglottic, Lens left  (Len\_L), Lens right (Len\_R), Mandible left (Mandible\_L), Mandible right (Mandible\_R), Mastoid left (Mastoid\_L), Mastoid right (Mastoid\_R), Middle Ear left (MiddleEar\_L), Middle ear right (MiddleEar\_R), Optic nerve left (OpticNerve\_L), Optic nerve right (OpticNerve\_R), Oral cavity, Parotid left (Parotid\_L), Parotid right (Parotid\_R), Pharyngeal constrictor muscle (PharynxCont), Pituitary, Spinal cord, Submandibular left (Submandibular\_L), Submandibular right (Submandibular\_R), Temporal lobe left (TemporalLobe\_L), Temporal lobe right (TemporalLobe\_R), Thyroid, Temporomandibular joint left (TMjoint\_L), Temporomandibular joint right (TMjoint\_R), Trachea, Tympanic cavity left (TympanicCavity\_L), Tympanic cavity right (TympanicCavity\_R), Vestibular semicircular canal left (VestibulSemi\_L), Vestibular semicircular canal right (VestibulSemi\_R) and primary gross tumor volume (GTVp) and lymph node grooss tumor volume (GTVnd).


All images were anonymized and approved by the ethics committee to protect privacy and all clinical treatment details have been deleted. The SegRap2023 dataset are split into three parts: 120 patients for training, 20 patients for validation, and 60 patients for testing.

## Results

#### Supervised Learning Methods for OAR Segmentation

In the experiment, we investigated several methods' performance on the SegRap2023 dataset for OAR segmentation.

The results (DSC scores) are shown as below:

<div align="center">
    <a href="https://"><img width="1080px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/SegRap2023_results_task01.png"></a>
</div>


#### Supervised Learning Methods for GTV Segmentation

In the experiment, we investigated several methods' performance on the SegRap2023 dataset for GTV segmentation.

The results (DSC scores) are shown as below:

<div align="center">
    <a href="https://"><img width="320px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/SegRap2023_results_task02.png"></a>
</div>


#### Visualization of segmentation performance on SegRap2023 dataset.

Figure 1 visually presents the OAR segmentation outcomes from the top three performing teams. To showcase segmentation differences, we selected three patients based on the lower quartile (LQ), median quartile (MQ), and high quartile (HQ) of the average across both the top three teams and the 45 OAR. The results highlight that these methods excel in achieving accurate segmentations for larger organs such as BrainStem, Parotid_L, and Parotid_R. However, challenges persist in accurately segmenting small and intricate organs. For instance, the Chiasm exhibits under-segmentation, particularly in the case of the LQ patient.

<div align="center">
    <a href="https://"><img width="1080px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/SegRap2023_vis_task01.png"></a>
</div>


Figure 2 visualizes the GTV segmentation results of the top 3 teams. These results show that the GTVp and GTVnd segmentation are still challenging. Specifically, most GTVp segmentation results suffer from under-segmentation (in HQ, MQ and LQ patients). Additionally, some GTVnd even can not be identified and segmented (in the LQ patient). These findings highlight the challenge of achieving precise and automated GTV segmentation, which warrants heightened attention and further investigation.

<div align="center">
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/SegRap2023_vis_task02.png"></a>
</div>




## 🙌 Download Link

- The SegRap2023 training set could be downloaded from [GoogleOne](https://drive.google.com/drive/folders/115mzmNlZRIewnSR2QFDwW_-RkNM0LC9D) and [BaiduNetDisk](https://pan.baidu.com/share/init?surl=fJ8tec69tRJbPTKxwjCa3A&pwd=2023#list/path=%2FSegRap2023)(code: 2023).



## 📊 Official Baseline and Results

The related official code is available [here](https://github.com/HiLab-git/SegRap2023).

### Evaluation metric

The evaluation metrics of SegRap2023 are flexible for users. It could be Dice, NSD, HD95 and so on.

## 🎫 License

This project is released under the [Apache 2.0 license](LICENSE).


## 🖊️ Citation

```
TODO
```

