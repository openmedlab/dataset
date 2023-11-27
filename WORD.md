# WORD: A large-scale dataset, benchmark and clinically applicable study for abdominal organ segmentation from CT image

Whole abdominal organ segmentation is important in diagnosing abdomen lesions, radiotherapy, and follow-up. However, oncologists’ delineating all abdominal organs from 3D volumes is time-consuming and very expensive. Deep learning-based medical image segmentation has shown the potential to reduce manual delineation efforts, but it still requires a large-scale fine annotated dataset for training, and there is a lack of large-scale datasets covering the whole abdomen region with accurate and detailed annotations for the whole abdominal organ segmentation. In this work, we establish a new large-scale Whole abdominal ORgan Dataset (WORD) for algorithm research and clinical application development. This dataset contains 150 abdominal CT volumes (30495 slices). Each volume has 16 organs with fine pixel-level annotations and scribble-based sparse annotations, which may be the largest dataset with whole abdominal organ annotation. Several state-of-the-art segmentation methods are evaluated on this dataset. And we also invited three experienced oncologists to revise the model predictions to measure the gap between the deep learning method and oncologists. Afterward, we investigate the inference-efficient learning on the WORD, as the high-resolution image requires large GPU memory and a long inference time in the test stage. We further evaluate the scribble-based annotation-efficient learning on this dataset, as the pixel-wise manual annotation is time-consuming and expensive. The work provided a new benchmark for the abdominal multi-organ segmentation task, and these experiments can serve as the baseline for future research and clinical application development.

<!-- Insert a pipeline of your algorithm here if got one -->
<div align="center">
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/word_main.png"></a>
</div>

## ✨ Overview
- We built a new clinical whole abdominal organ segmentation dataset (150 CT scans) and has more categories (16 organs) and high-quality annotations than previous works. In addition, we further annotate 20 cases from LiTS for networks’ generalization evaluation.

- We establish a new abdominal organ segmentation benchmark by (1) evaluating the existing fully supervised segmentation methods, (2) measuring the gap between deep learning models and oncologists, (3) investigating the pre-trained model generalization ability on open datasets, (4) investigating the inference-efficient learning for the high-resolution abdominal CT image segmentation, (5) introducing scribble-based weakly supervised methods to reduce the labelling cost.

## 🛠️ Description of Dataset

The 150 CT scans in the WORD dataset were collected from 150 patients before the radiation therapy in a single center. All of them are scanned by a SIEMENS CT scanner. The clinical characteristics of the WORD dataset are listed below.

<div align="center">
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/word_clinical_info.png"></a>
</div>

Each CT volume consists of 159 to 330 slices of 512 x 512 pixels, with an in-plane resolution of 0.976 mm x 0.976 mm and slice spacing of 2.5 mm to 3.0 mm, indicating that the WORD dataset is a very high-resolution dataset. All scans of WORD dataset are exhaustively annotated with 16 anatomical organs, including the liver, spleen, kidney (L), kidney (R), stomach, gallbladder, esophagus, duodenum, colon, intestine, adrenal, rectum, bladder, head of the femur (L) and head of the femur (R). All images were anonymized and approved by the ethics committee to protect privacy and all clinical treatment details have been deleted. We randomly split WORD dataset into three parts: 100 scans (20115 slices) for training, 20 scans (4103 slices) for validation, and 30 scans (6277 slices) for testing. The following picture shows the volume distributions of all annotated organs. It shows that the extremely unbalanced distribution among large and small organs may bring some challenges to the segmentation task. At the same time, we further selected and annotated 20 CT scans from  LiTS as an external evaluation set. These scans cover the whole abdominal region, each with 16 organ annotations.
<div align="center">
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/word_size_dis.png"></a>
</div>
A senior oncologist (with 7 years of experience) uses ITK-SNAP to delineate all organs slice-by-slice in axial view. After that, an expert in oncology (more than 20 years of experience) checks and revises these annotations carefully and discusses them in cases of disagreement to produce consensus annotations and further ensure the annotation quality. Finally, these consensus labels are released and used for methods or clinical application development and evaluation. Note that all annotations and consensus discussions obey the radiation therapy delineation guideline published by Radiation Therapy Oncology Group (RTOG).

<div align="center">
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/word_annotation_differ.png"></a>
</div>

### Results

#### Supervised Learning Baseline

In the experiment, we investigated several methods' performance on the WORD dataset.

The results are shown as below:

<!-- Insert a pipeline of your algorithm here if got one -->
<div align="center">
    <a href="https://"><img width="600px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/word_baseline_results.png"></a>
</div>

#### Transfer Learning Baseline

We run the transfer learning experiments using the pre-trained nnUNetV2 to other abdominal organ segmentation datasets.

<!-- Insert a pipeline of your algorithm here if got one -->
<div align="center">
    <a href="https://"><img width="600px" height="auto" src="https://github.com/openmedlab/dataset/blob/main/figures/word_transfer_results.png"></a>
</div>


## 🙌 Download Link

- The WORD dataset can be downloaded from [here](https://github.com/HiLab-git/WORD).


## 📊 Official Baseline and Results

The related official code is available [here](https://github.com/HiLab-git/WORD).

### Evaluation metric

The evaluation metrics of WORD are flexible for users. It could be Dice, HD95 and so on.

## 🎫 License

This project is released under the [Apache 2.0 license](LICENSE).


## 🖊️ Citation

```
@article{luo2022word,
  title={{WORD}: A large scale dataset, benchmark and clinical applicable study for abdominal organ segmentation from CT image},
  author={Xiangde Luo, Wenjun Liao, Jianghong Xiao, Jieneng Chen, Tao Song, Xiaofan Zhang, Kang Li, Dimitris N. Metaxas, Guotai Wang, and Shaoting Zhang},
  journal={Medical Image Analysis},
  volume={82},
  pages={102642},
  year={2022},
  publisher={Elsevier}}
```
