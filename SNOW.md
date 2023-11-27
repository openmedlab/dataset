# A Large-scale Synthetic Pathological Dataset for Deep Learning-enabled Segmentation of Breast Cancer.

The success of training computer-vision models heavily relies on the support of large-scale, real-world images with annotations. Yet such an annotation-ready dataset is difficult to curate in pathology due to the privacy protection and excessive annotation burden. To aid in computational pathology, synthetic data generation, curation, and annotation present a cost-effective means to quickly enable data diversity that is required to boost model performance at different stages. In this study, we introduce a large-scale synthetic pathological image dataset paired with the annotation for nuclei semantic segmentation, termed as Synthetic Nuclei and annOtation Wizard (SNOW). The proposed SNOW is developed via a standardized workflow by applying the off-the-shelf image generator and nuclei annotator. The dataset contains overall 20k image tiles and 1,448,522 annotated nuclei with the CC-BY license. We show that SNOW can be used in both supervised and semi-supervised training scenarios. Extensive results suggest that synthetic-data-trained models are competitive under a variety of model training settings, expanding the scope of better using synthetic images for enhancing downstream data-driven clinical tasks.

<div align="center">
    <caption> <b> Figure 1. Comparison of data and model training pipeline.</b> </caption>
    <a href="https://"><img width="600px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Figure1.png"></a>
</div>
In Figure 1, (a) Conventional model training pipeline. Conventional model training heavily relies on real-world images and laborious human-expert annotations. (b) Synthetic-data-enabled model training pipeline. By comparison, we focus on a pure synthetic image generation and annotation. We use the off-the-shelf GAN model as an image generator to yield informative synthetic images and then annotate the generated images by the weakly trained annotator.


<div align="center">
    <caption><b> Figure 2. Synthetic image examples and annotations of SNOW data set.</b> </caption>
    <a href="https://"><img width="600px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Figure2.png"></a>
</div>
In Figure 2, (a) Common nuclei examples (e.g., major nuclei are separated). (b) Challenging nuclei examples (e.g., closely adjacent or clumped nuclei).


## ✨ Overview
- SNOW data set (Figure 2) opens up perspectives on the utility of meaningful synthetic data in pathological image assessment. This simple yet useful pipeline, together with quality verification on image contents, has demonstrated that training models from synthetic images alone can achieve competitive performance for nuclei semantic segmentation.

- The pipeline (Figure 3) contains a joint workflow of synthetic image generator (SIG) and nuclei annotator (NA). First, the real-world image training data include the high-resolution images from breast cancer histopathological annotation and diagnosis dataset (BreCaHAD). So we can train the synthetic image generator from scratch to generate synthetic breast tissue images from StyleGAN2. Next, PanNuke dataset provides pairs of image and annotation to weakly train the nuclei annotator to generate the needed annotation (e.g., nuclei mask) for synthetic images. The blue arrows represent the workflow of the synthetic image generation and the green arrows denote the workflow of nuclei annotation.

<div align="center">
    <caption> <b> Figure 3. Overview of SNOW dataset pipeline.</b> </caption>
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Figure3.png"></a>
</div>

- Regarding data set evaluation, we consider two common training settings including supervised and semi-supervised training of segmentation models. Under each training strategy, we trained segmentation models on two types of data sets respectively, including the real-world data set and the proposed synthetic data set. The experiments based on a strict separation of these two types of data sets without overlap, allowing us to assess the segmentation performance gained from the real-world data set and synthetic data set.
<div align="center">
    <caption> <b> Figure 4. Summary of the datasets used in our dataset generation and experiments.</b> </caption>
    <a href="https://"><img width="600px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Figure4.png"></a>
</div>


## 🛠️ Description of Dataset

### SNOW: Synthetic Nuclei and annOtation Wizard

The creation of our synthetic dataset is associated with two real-world data sets. Table 1 summarizes several public real-world data sets related to nuclei segmentation and the proposed SNOW data set. Due to the high-resolution detailed view of tissues (1,360 × 1,024), we use BreCaHAD to ensure the training performance of synthetic image generator. BreCaHAD data set includes 162 breast tissue tiles with point location for each nuclei. As BreCaHAD data set does not provide the semantic segmentation mask of entire nuclei (e.g., only point annotation), we utilize PanNuke data set for training nuclei annotator, which contains both images and corresponding annotation masks (e.g., nuclei is foreground and others are background). To date, PanNuke data set is the largest nuclei segmentation data set (tiles n = 7,901). Under the proposed pipeline,SNOW expands the current data scale of pathological nuclei analysis without adding human annotation efforts (e.g. overall 20k tiles and 1,448,522 annotated nuclei.

<div align="center">
    <caption> <b> Table 1. Summary of the datasets used in our dataset generation and experiments.</b> </caption>
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Table1.png"></a>
</div>

All data records are included in Zenodo (https://doi.org/10.5281/zenodo.663372143) and GitHub (https://github.com/Cassie07/SNOW-Dataset).

- Image folder All synthetic images are in SNOW_Image.zip folder.

- Mask folders Due to the large size of the nuclei segmentation mask, we split all masks into four folders (e.g., mask_0_5000.zip, mask_5001_10k.zip, mask_10k_15k.zip, and mask_15k_20k.zip). In each zip folder, we include three sub-folders: json, mat, and overlay. We only use mat folders to save nuclei segmentation mask for each synthetic image.

- Datasheets for Datasets To help users understand details of the dataset and possible extensive use, we prepared datasheets44 for our data set. The detailed responses are related to the following factors, including study motivation, composition, collection process, preprocessing/cleaning/labeling information, distributions, and data maintenance.


## 🙌 Download Link

- The full SNOW dataset could be dowloaded from [SNOW](https://zenodo.org/records/6633721).

## 📊 Official Baseline and Results

The related official code is available [here](https://github.com/Cassie07/SNOW-Dataset).

### Evaluation metric

We evaluate the segmentation performance on the independent, real-world dataset of Triple Negative Breast Cancer (TNBC) data set16. For all experiments in our study, the batch size is 64, the optimizer is Adam, and the learning rate is 1e-4. We used four Tesla V100 SXM2 GPUs for our experiments. To evaluate nuclei semantic segmentation performance, we use the DICE score, Jaccard index (also known as Intersection-Over-Union (IoU)), and average Hausdorff Distance (aHD).

### Results

#### Supervised learning comparison.
In the experiment, we trained the models on the real-world dataset and synthetic SNOW dataset separately to compare the performance difference derived from datasets. We use ImageNet-pretrained encoder in segmentation models. For supervised training, we randomly split the used data set into the training set and the validation set (e.g., the split ratio is 95%, 5%).

The results are shown as below:

<div align="center">
    <caption> <b> Table 2. (Supervised learning) The comparison of nuclei semantic segmentation performance on TNBC dataset. </b> </caption>
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Table2.png"></a>
</div>

#### Semi-supervised learning comparison.
For the semi-supervised training, we randomly split the data set into three sets, including the labeled teacher model training set, the labeled validation set, and the unlabeled set (e.g., the split ratio is 45%, 5%, and 50%). Thus the annotation ratio of the entire data set is 0.5. To prepare the unlabeled set, we use image samples only (i.e., no mask annotation is included). Next, we train the teacher model on the labeled teacher training set and select the best model by evaluating the model performance on the validation set. The best teacher model was used to generate the soft pseudo-label for the unlabeled set and worked as the initialized student model. Then, we trained the student model and selected the best student model as a new teacher model to update the unlabeled set annotation. Further, the best student model became the initialized model in the next iteration. After five iterations, we finally used the best student model for model evaluation. The number of epoch for teacher model and student model training is 100 and 15 respectively.

<div align="center">
    <caption> <b> Table 3. (Semi-supervised learning comparison) The comparison of nuclei semantic segmentation performance on TNBC dataset. </b> </caption>
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Table3.png"></a>
</div>

#### Synthetic data set utility evaluation.
We use ResNet34 as the encoder of the UNet segmentation model, which is either initialized by ImageNet pre-trained weights (e.g., out-domain pretraining) or trained from scratch. In the bellow table, “pretrain data (in-domain)” represents that we use the entire SNOW data set (e.g., 20k) for the segmentation model training. “Finetuning data (in-domain)” means that we use the TNBC training and validation set for the segmentation model finetuning. Finally, all the experiments are evaluated on the TNBC testing set.

<div align="center">
    <caption> <b> Table 4. Synthetic data set utility evaluation.</b> </caption>
    <a href="https://"><img width="800px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Table4.png"></a>
</div>


#### Visualization of segmentation performance on TNBC dataset.
In Figure 5, the first and second columns are original tiles and the associated ground truth. Columns a to d offer the zoom-in view of segmentation outputs that generated by the model (e.g., ResNet34 as encoder of the UNet architecture) with the best performance. The column a shows the segmentation performance when the model trained on the real-world dataset (e.g., PanNuke) under the supervised learning setting (e.g., in Table 2). The column b shows the segmentation performance of model trained on SNOW under the supervised learning setting (e.g., in Table 2). The column c shows the segmentation performance of model trained on SNOW under the semi-supervised learning setting (e.g., in Table 3). The column d shown the segmentation performance of model that are not pretrained on ImageNet (e.g., in Table 4). The yellow dotted regions represent missing nuclei and the blue ones denote redundant nuclei when comparing to the ground truth.

<div align="center">
    <caption> <b> Figure5. Visualization of segmentation performance on TNBC dataset. </b> </caption>
    <a href="https://"><img width="600px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Figure5.png"></a>
</div>

#### Visualization of segmentation performance on TNBC dataset.
In Figure 6, (a) The real-world images for synthetic image generator training. In (a), we show the images from the BreCaHAD dataset. (b) The synthetic images. In (b), we show the representative synthetic images in SNOW dataset.

<div align="center">
    <caption> <b> Figure6. The comparison between the real-world and the synthetic images.  </b> </caption>
    <a href="https://"><img width="600px" height="auto" src="https://github.com/openmedlab/dataset/blob/main//figures/snow_Figure6.png"></a>
</div>


## 🎫 License

This project is released under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).


## 🖊️ Citation

```
@article{ding2023large,
  title={A large-scale synthetic pathological dataset for deep learning-enabled segmentation of breast cancer},
  author={Ding, Kexin and Zhou, Mu and Wang, He and Gevaert, Olivier and Metaxas, Dimitris and Zhang, Shaoting},
  journal={Scientific Data},
  volume={10},
  number={1},
  pages={231},
  year={2023},
  publisher={Nature Publishing Group UK London}
}
```
