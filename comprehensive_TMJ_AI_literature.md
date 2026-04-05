# Comprehensive Literature Review: AI in TMJ Disorders Classification

*Compiled for thesis manuscript on automated multi-label classification of TMJOA from CBCT*

---

## CATEGORY A: CBCT-Based Deep Learning for TMJOA Classification (Direct Comparators)

### A1. Lee et al. (2020)
**"Automated detection of TMJ osteoarthritis based on artificial intelligence"**
https://journals.sagepub.com/doi/abs/10.1177/0022034520936950
*J. Dent. Res.* 99:1363–1367.

- **Summary:** First deep learning application to TMJOA on CBCT. Used Single Shot Detection (SSD) on 3514 sagittal CBCT images. Binary classification (indeterminate vs. TMJOA). Tested on 2 sets totaling 300 images. Average accuracy 0.86, precision 0.85, recall 0.84, F1 0.84.
- **Limitations:** Required manual ROI definition and bounding boxes. Binary-only classification.
- **Rationale for citing:** Seminal paper establishing the DL paradigm for TMJOA on CBCT. Baseline comparison. Your method eliminates their manual ROI requirement.

### A2. Eşer et al. (2023)
**"Classification of TMJOA on CBCT images using artificial intelligence system"**
https://onlinelibrary.wiley.com/doi/abs/10.1111/joor.13481
*J. Pop. Ther. Clin. Pharmacol.* 31(8).

- **Summary:** YOLOv5 on 2000 manually selected sagittal CBCT sections from 290 patients. Four-class classification (normal, erosion, osteophyte, flattening). TMJ segmentation accuracy 0.9953 / AUC 0.9723. Classification accuracy 0.7678, F1 0.8686.
- **Limitations:** Required manual 2D slice selection and bounding box annotation. Published in a lower-tier journal.
- **Rationale for citing:** Closest methodological comparison (CBCT + DL + TMJOA). Your accuracy exceeds theirs. Their reliance on manual slices and bounding boxes is the key limitation your pipeline eliminates.

### A3. Talaat et al. (2023)
**"An AI model for the radiographic diagnosis of osteoarthritis of the TMJ"**
https://www.nature.com/articles/s41598-023-43277-6
*Sci. Rep.* 13:15972.

- **Summary:** YOLO-based detection model on 2737 CBCT images from 943 patients (largest CBCT dataset for TMJOA AI). Tested against experienced oral radiologist on 350-image set. Favorable sensitivity/specificity across individual OA signs. AI outperformed radiologist for subcortical cyst detection.
- **Limitations:** Still requires bounding box annotations. Single regression model architecture.
- **Rationale for citing:** Largest dataset study. Key bounding-box-annotation bottleneck example. Also demonstrates AI can outperform human experts.

### A4. Mourad et al. (2024)
**"Automatic detection of TMJOA radiographic features using deep learning AI"**
https://www.sciencedirect.com/science/article/pii/S2468785524004130
*Saudi Dent. J.* 36:1510–1517.

- **Summary:** YOLO-based object detection for individual TMJOA features on CBCT. Compared AI vs. experienced examiners. Substantial to near-perfect agreement for most features, except subcortical cyst (statistically significant difference, p=0.049).
- **Limitations:** Detection-based (requires bounding boxes).
- **Rationale for citing:** Most recent detection-based CBCT work. Confirms subcortical cyst is the hardest class — convergent with your findings (cyst had lowest AUC).

### A5. Yilmaz & Turgut (2025)
**"Improving TMJ Diagnosis: A Deep Learning Approach for Detecting Mandibular Condyle Bone Changes"**
https://www.mdpi.com/2075-4418/15/8/1022
*Diagnostics* 15:1022.

- **Summary:** CNN architectures for detecting morphological changes (normal, flattening, deformation) in TMJ on panoramic images. Addressed class imbalance through image weighting. April 2025 publication.
- **Limitations:** Panoramic images, not CBCT.
- **Rationale for citing:** Very recent. Addresses class imbalance — directly relevant to your sclerosis/cyst challenge.

---

## CATEGORY B: 3D Shape-Based Approaches (Cevidanes/Michigan Group)

### B1. de Dumast et al. (2018)
**"A web-based system for neural network based classification in TMJ osteoarthritis"**
https://www.sciencedirect.com/science/article/pii/S0895611118302805
*Comput. Med. Imaging Graph.* 67:45–54.

- **Summary:** Pioneered DSCI web-based system with SVA neural network classifier. 259 condyles training, 34 testing. Classified into 5 degeneration stages using 3D surface meshes (SPHARM-PDM). 91% close agreement with clinician consensus. Required manual CBCT segmentation via ITK-SNAP.
- **Rationale for citing:** First 3D-aware approach. Manual segmentation bottleneck your pipeline solves.

### B2. Ribera et al. (2019)
**"Shape Variation Analyzer: a classifier for TMJ damaged by osteoarthritis"**
https://www.spiedigitallibrary.org/conference-proceedings-of-spie/10950/1095021/Shape-variation-analyzer--a-classifier-for-temporomandibular-joint-damaged/10.1117/12.2506018.short
*Proc. SPIE* 10950:1095021.

- **Summary:** Improved SVA deep learning classifier. Used heat kernel signatures as shape descriptors on 3D meshes. Compared 9 ML algorithms; DNN was most accurate. 259 training, 34 testing. 6 morphological groups. Introduced SMOTE for class imbalance.
- **Rationale for citing:** Extends de Dumast 2018 with sophisticated features. Shows DL outperforms classical ML for condylar morphology.

### B3. Shoukri et al. (2019)
**"Minimally invasive approach for diagnosing TMJ osteoarthritis"**
*J. Dent. Res.* 98:1103–1111.
https://journals.sagepub.com/doi/abs/10.1177/0022034519865187

- **Summary:** Combined 3D condylar shape, clinical markers, and biomarkers (serum/saliva) using neural network. 46 OA + 46 matched controls. High conformity between NN and clinician classification. Demonstrated multi-modal integration improves diagnosis.
- **Rationale for citing:** Key multi-modal approach. Your imaging-only method achieving comparable performance undermines the argument that biomarkers are essential.

---

## CATEGORY C: Multi-Source Machine Learning (TMJOAI / TMJPI Tools)

### C1. Bianchi et al. (2020)
**"Osteoarthritis of the TMJ can be diagnosed earlier using biomarkers and ML"**
*Sci. Rep.* 10:8012.
https://www.nature.com/articles/s41598-020-64942-0

- **Summary:** 52 features (clinical, biological, CBCT radiomics) using XGBoost + LightGBM. 46 OA + 46 controls. Accuracy 0.823, AUC 0.870, F1 0.823. Interaction effects between features are important.
- **Rationale for citing:** Baseline for multi-modal ML. Your imaging-only AUC 0.99 for OA surpasses their AUC 0.87.

### C2. Le et al. (2021)
**"TMJOAI: An artificial web-based intelligence tool for early diagnosis of TMJ osteoarthritis"**
*LNCS* 12969:78–87.
https://link.springer.com/chapter/10.1007/978-3-030-90874-4_8

- **Summary:** Web-based ML tool using 52 markers. Best: XGBoost + LightGBM averaging, AUC 0.88 with mandibular fossa radiomics. 92 subjects. Open-source, web-deployed.
- **Rationale for citing:** Deployed clinical tool benchmark. Their AUC 0.88 is below your imaging-only results.

### C3. Zhang et al. (2021)
**"TMJ osteoarthritis diagnosis using privileged learning of protein markers"**
*IEEE EMBC* 2021:1810–1813.
https://ieeexplore.ieee.org/abstract/document/9629990/

- **Summary:** Learning Using Privileged Information (LUPI) paradigm. Protein markers available only during training. Best: KRVFL+ with AUC 0.80, accuracy 75.6%. 92 patients.
- **Rationale for citing:** Novel ML paradigm. Their AUC 0.80 with multi-modal data is well below your imaging-only results.

### C4. Mackie et al. (2022)
**"Quantitative bone imaging biomarkers and joint space analysis of the articular fossa in TMJOA using AI models"**
*Front. Dent. Med.* 3:1007011.
https://www.frontiersin.org/journals/dental-medicine/articles/10.3389/fdmed.2022.1007011/full

- **Summary:** Extended TMJOAI/TMJPI to include articular fossa radiomics and bone morphometry. LightGBM best with AUC 0.842, accuracy 0.804. Articular fossa radiomics improve via interaction effects.
- **Rationale for citing:** Most advanced ML from the Michigan group. Shows radiomics + ML plateau around AUC 0.84–0.88.

---

## CATEGORY D: Panoramic Radiography-Based OA Classification

### D1. Choi et al. (2021)
**"AI in detecting TMJOA on orthopantomogram"**
*Sci. Rep.* 11:10761.
https://www.nature.com/articles/s41598-021-89742-y

- **Summary:** ResNet on 1189 OPG images (CBCT as ground truth). Three-category classification failed; after removing indeterminate: accuracy 0.78, sensitivity 0.73, specificity 0.82. Compared to OMFR expert.
- **Rationale for citing:** Shows "indeterminate" category is problematic. Supports your binary DC/TMD approach.

### D2. Jung et al. (2023)
**"Deep learning for osteoarthritis classification in the TMJ"**
*Oral Dis.* 29:1050–1059.
https://onlinelibrary.wiley.com/doi/abs/10.1111/odi.14056

- **Summary:** ResNet-152 and EfficientNet-B7 on 858 panoramic TMJ images from 518 patients. Accuracies 0.87/0.88. Both outperformed general dentists; EfficientNet comparable to TMD specialists. Grad-CAM visualizations.
- **Rationale for citing:** Validates transfer learning from ImageNet for dental OA. Supports pretrained backbone use.

### D3. Kim et al. (2020)
**"Expert system for mandibular condyle detection and OA classification in panoramic imaging using R-CNN and CNN"**
*Appl. Sci.* 10:7464.

- **Summary:** Faster R-CNN for condyle detection (mAP 99.4%/100%), VGG16 for classification on 1000 panoramic images. Sensitivity 0.54, specificity 0.94, accuracy 0.84. Three categories.
- **Rationale for citing:** Another panoramic approach with low sensitivity. Your CBCT method achieves much higher sensitivity.

---

## CATEGORY E: Non-CBCT Imaging Modalities

### E1. Yun et al. (2025)
**"Deep learning-based diagnosis of TMJOA using whole-body bone scans"**
*iScience* 28:e112028.

- **Summary:** VGG16-based CNNs on 3886 TMJs from 1943 patients (bone scintigraphy). TMJ-focused imaging: AUC >0.90. Whole-body scans: AUC ~0.65. Largest patient count in TMJOA AI.
- **Rationale for citing:** Largest patient dataset (1943). Different modality, comparable AUC to your CBCT. Shows field expanding beyond CBCT.

### E2. Orhan et al. (2021)
**"Development and validation of an MRI-based ML model for TMJ pathologies"**
*Biomed. Res. Int.* 2021:6656773.

- **Summary:** Radiomic features from MRI for TMJ disc displacement and condylar bone changes. 214 TMJs from 107 patients. KNN and RF classifiers. Training AUC 0.89, testing AUC 0.77. Six classifiers compared.
- **Rationale for citing:** MRI-based approach for broader context. Shows radiomics work across modalities.

### E3. Lee et al. (2022)
**"Advantages of deep learning with CNN in detecting disc displacement of the TMJ in MRI"**
*Sci. Rep.* 12:11352.

- **Summary:** DL-based automatic detection of anterior disc displacement from MRI. 2520 TMJs from 1260 patients. Fine-tuning model AUC 0.8775, accuracy ~77%. Compared from-scratch, fine-tuned, and frozen models.
- **Rationale for citing:** Large MRI dataset. Demonstrates fine-tuning superiority — supports your use of pretrained models.

### E4. Kao et al. (2023)
**"Classifying TMD with artificial intelligent architecture using MRI"**
*Ann. Biomed. Eng.* 51:517–526.

- **Summary:** MRI-based deep learning for TMD classification.
- **Rationale for citing:** Shows MRI + DL is actively explored alongside CBCT approaches.

---

## CATEGORY F: TMJ Disc Displacement Detection (Related Task)

### F1. Yoon et al. (2023)
**"Explainable deep learning-based clinical decision support engine for MRI-based automated diagnosis of TMJ ADD"**
*Comput. Methods Programs Biomed.* 233:107465.

- **Summary:** Two-stage DL: ROI detection then 3-class classification (normal, ADD without reduction, ADD with reduction). Included Grad-CAM heatmaps as explainability. First validated MRI-based automatic TMJ ADD diagnosis.
- **Rationale for citing:** Demonstrates explainable AI in TMJ (similar to your EigenCAM approach). Shows clinical decision support trajectory.

### F2. Li et al. (2024/2025)
**"Deep learning-based automated diagnosis of TMJ anterior disc displacement and clinical application"**
*Front. Physiol.* 15:1445258.

- **Summary:** ResNet101_vd on 618 TMJ cases from two hospitals. Four-category MRI classification. Precision >92%. Deployed for clinical application. Grad-CAM + segmentation annotations for interpretability.
- **Rationale for citing:** Multi-center study with clinical deployment. Shows feasibility of AI deployment in TMJ diagnosis.

### F3. Wang et al. (2025)
**"CBCT assisted diagnosis system for TMJ disc displacement based on deep learning"**
*BMC Oral Health* (Feb 2025).

- **Summary:** Two-stage: YOLOv11 for ROI detection, then FastViT-t8 for binary classification. 330 patients, 5238 ROIs. Detection precision 0.986. Classification AUC 0.733.
- **Rationale for citing:** Uses same YOLOv11 architecture you tested. Very recent. Shows CBCT expanding to disc displacement detection.

### F4. Choi et al. (2025)
**"Automatic prediction of TMJ disc displacement in CBCT images using ML"**
*J. Digit. Imaging Inform. Med.* (2025).

- **Summary:** Radiomics-based ML (RF, XGBoost) for disc displacement from CBCT without MRI. 247 condyles from 134 patients. Three experiments with different group classifications.
- **Rationale for citing:** Shows CBCT-based ML expanding to tasks previously requiring MRI. Same modality as your work.

### F5. Yuksel et al. (2025)
**"Evaluation of TMJ disc displacement with MRI-based radiomics analysis"**
*Oral Radiol.* (2025).

- **Summary:** Radiomics from T1/PD-weighted MRI for disc displacement. 180 TMJs from 90 patients. KNN best classifier. Training AUC 0.944, testing AUC 0.913.
- **Rationale for citing:** Shows radiomics-based classification of TMJ pathology achieving high AUC.

### F6. Flügge et al. (2025)
**"Automated pediatric TMJ articular disk identification and displacement classification in MRI with ML"**
*J. Dent.* (2025).

- **Summary:** UNet++ for segmentation (Dice 0.67 disc, 0.91 condyle), then automated displacement classification. 235 pediatric patients (470 joints). AUC 0.89–0.92.
- **Rationale for citing:** Pediatric population. Shows segmentation-then-classification pipeline (conceptually similar to your approach).

---

## CATEGORY G: TMJ Segmentation (Pipeline Components)

### G1. Vinayahalingam et al. (2023)
**"Deep learning for automated segmentation of the TMJ"**
*J. Dent.* 132:104475.

- **Summary:** Three-step 3D U-Net: ROI detection → bone segmentation → TMJ classification. 154 CBCTs for training. High accuracy, speed, and consistency for condyle and glenoid fossa segmentation.
- **Rationale for citing:** TMJ-specific segmentation. Your pipeline uses DentalSegmentator for mandible, then custom cropping — this paper shows alternative segmentation approaches.

### G2. Jeon et al. (2022)
**"Fully automated condyle segmentation using 3D convolutional neural networks"**
*Sci. Rep.* 12:20188.

- **Summary:** 3D U-Net and cascaded 3D U-Net for condyle segmentation. 234 condyles from 117 subjects. DSC 0.886–0.932. Stress-tested optimal dataset size.
- **Rationale for citing:** Condyle-specific segmentation. Shows cascaded U-Net can work well for condylar morphology.

### G3. Wu et al. (2025)
**"Automatic segmentation and visualization of cortical and marrow bone in mandibular condyle on CBCT"**
*Oral Radiol.* 41:88–101.

- **Summary:** DL model for simultaneous cortex and marrow segmentation. 825 condyles, 490 CBCTs from 3 centers. 3D U-Net with modifications. Multi-center. Can generate 3D color maps for cortical thickness visualization.
- **Rationale for citing:** Multi-center study. Clinical application in diagnosis of condylar bony changes. Shows automated quantification potential.

### G4. Jeon et al. (2021)
**"Automated cortical thickness measurement of the mandibular condyle head on CBCT using DL"**
*Sci. Rep.* 11:14855.

- **Summary:** Modified U-Net + CNN for condylar cortex/marrow segmentation. 12,800 images from 25 subjects. 3D color maps for cortical thickness visualization. IoU 0.870 (marrow), 0.734 (cortex).
- **Rationale for citing:** Shows automated quantification of condylar bone changes — future direction for your pipeline.

---

## CATEGORY H: Non-Imaging AI for TMD Diagnosis

### H1. Kreiner & Viloria (2022)
**"A novel artificial neural network for the diagnosis of orofacial pain and TMD"**
*J. Oral Rehabil.* 49:884–889.

- **Summary:** Multilayer perceptron (MLP) for diagnosing orofacial pain and TMD from clinical data (chief complaint + maximal mouth opening). NLP-based approach. Multiple TMD subtypes.
- **Rationale for citing:** Shows AI applied to TMD diagnosis from clinical text data (non-imaging). Contextualizes the imaging-based approach within broader TMD AI.

### H2. Taşkıran & Çunkaş (2021)
**"A deep learning based decision support system for diagnosis of TMJ disorder"**
*Appl. Acoust.* 182:108292.

- **Summary:** Novel device for recording TMJ sounds. Signal processing + ANN (78% accuracy) + deep learning for TMD classification from acoustic data. Non-imaging, non-invasive.
- **Rationale for citing:** Shows alternative modalities (sound) for TMD diagnosis. Contextualizes the imaging landscape.

### H3. Bas et al. (2012) / Bas et al. (2022)
**"Use of artificial neural network in differentiation of subgroups of TMD"**
*Comput. Biol. Med.* 42:785–790.

- **Summary:** ANN for classifying TMD subgroups from clinical data alone (no imaging). Early AI application in TMD.
- **Rationale for citing:** Historical perspective. Shows AI for TMD pre-dates the deep learning era.

### H4. Schmitter et al. (2025) / Tkalec et al. (2024)
**"Using ML to classify TMD: a proof of concept"**
*Cranio* (2024).

- **Summary:** ML model for classifying TMDs based on ICOP criteria using structured patient record data.
- **Rationale for citing:** Shows structured clinical data-based classification approach.

---

## CATEGORY I: Systematic Reviews and Meta-Analyses

### I1. Xu et al. (2023)
**"AI for detecting TMJOA using radiographic image data: SR and meta-analysis"**
*PLoS One* 18:e0288631.

- **Summary:** 6 studies. Pooled sensitivity 80%, specificity 90%, AUC 92%. Substantial heterogeneity from imaging modality, ethnicity, technique, sample size.
- **Rationale for citing:** Key benchmark AUC 0.92 your results exceed.

### I2. Almășan et al. (2023)
**"TMJOA diagnosis employing AI: SR and meta-analysis"**
*J. Clin. Med.* 12:942.

- **Summary:** 7 studies (10,077 images). Panoramic ResNet models: pooled sensitivity 0.76, specificity 0.79.
- **Rationale for citing:** Provides sensitivity/specificity benchmarks you exceed.

### I3. Jha et al. (2022)
**"Diagnosis of TMD using AI technologies: SR and meta-analysis"**
*PLoS One* 17:e0272715.

- **Summary:** 21 studies across all TMD subtypes and AI methods. CNNs most frequent (7 studies). AUC 0.54–0.89. Includes NLP study.
- **Rationale for citing:** Broadest TMD AI review. Contextualizes your OA-specific work.

### I4. Farook & Dudley (2023)
**"Automation and deep (machine) learning in TMJ disorder radiomics: A systematic review"**
*J. Oral Rehabil.* 50:501–521.

- **Summary:** 20 articles. Sensitivity 0.63–0.95, specificity 0.54–0.99. Entropy most stable CBCT radiomic parameter. Noted substantial data loss from poor acquisition/augmentation.
- **Rationale for citing:** Most thorough methodological critique. Data quality finding supports your automated pipeline.

### I5. Zhang et al. (2024)
**"ML-based medical imaging diagnosis in patients with TMD: diagnostic test accuracy SR and meta-analysis"**
*Clin. Oral Investig.* 28:186.

- **Summary:** Broadest meta-analysis. LightGBM sensitivity 0.79 > XGBoost 0.76 for DJD on CBCT.
- **Rationale for citing:** Most recent comprehensive meta-analysis with latest benchmarks.

### I6. Al-Jaf et al. (2025)
**"Application of AI in the diagnosis and management of TMJOA using CBCT: evidence-based SR"**
*Imaging Sci. Dent.* 55:223–233.

- **Summary:** 9 CBCT-specific studies. Accuracy 73.5–99%, F1 0.80–0.86. YOLO highest accuracy.
- **Rationale for citing:** Most recent CBCT-specific systematic review. Directly positions your work.

### I7. Alabed et al. (2025)
**"AI in TMJ Disorders: An Umbrella Review"**
*Clin. Exp. Dent. Res.* 11:e70079.

- **Summary:** Umbrella review of 5 systematic reviews. Accuracy 0.59–1.0, sensitivity 0.76–0.80, specificity 0.63–0.95.
- **Rationale for citing:** Highest-level evidence synthesis available.

### I8. Manek et al. (2025)
**"TMJ assessment in MRI images using AI tools: where are we now? A systematic review"**
*Dentomaxillofac. Radiol.* 54:1–11.

- **Summary:** 13 MRI studies for TMJ disc assessment. High heterogeneity. MobileNet V2 best for disc position (AUC 0.95 closed mouth).
- **Rationale for citing:** Differentiates MRI vs. CBCT AI applications. Supports your CBCT modality choice.

### I9. Rokhshad et al. (2024)
**"Deep learning for temporomandibular joint arthropathies: SR and meta-analysis"**
*J. Oral Rehabil.* (2024).

- **Summary:** Focused specifically on DL (not all ML) for TMJ arthropathies. Meta-analysis of DL model performance.
- **Rationale for citing:** DL-specific meta-analysis directly relevant to your deep learning approach.

### I10. Yuce & Kucuk (2023)
**"A comprehensive review of AI-based algorithms regarding TMJ related diseases"**
*Diagnostics* 13:2700.

- **Summary:** 66 articles reviewed across segmentation (11), JIA (3), OA (10), TMD (21), decision support (6), reviews (10), sound (5). Catalogues all AI approaches.
- **Rationale for citing:** Most comprehensive narrative review covering the entire TMJ AI landscape.

### I11. Nha et al. (2024)
**"Neuroimaging and AI for assessment of chronic painful TMD: comprehensive review"**
*Int. J. Oral Sci.* 16:2.

- **Summary:** Covers neuroimaging (fMRI, PET) + traditional imaging AI for painful TMD. Broader pain neuroscience perspective.
- **Rationale for citing:** Shows AI being applied to TMD pain assessment beyond just structural diagnosis.

---

## CATEGORY J: Juvenile Idiopathic Arthritis (JIA) — TMJ

### J1. Christensen et al. (2024)
**"An explainable and conformal AI model to detect TMJ involvement in children with JIA"**
*arXiv* 2405.01617.

- **Summary:** Random Forest on 6154 clinical examinations from 1035 pediatric patients. Precision 0.86, sensitivity 0.70 for early TMJ involvement prediction. SHAP explanations.
- **Rationale for citing:** Shows AI for TMJ arthritis beyond adult OA. Pediatric population.

### J2. Lillelund et al. (2025)
**"Improving early detection of TMJ involvement in JIA with clinically interpretable ML model"**
*Sci. Rep.* (Nov 2025).

- **Summary:** ML model on longitudinal clinical data from Aarhus JIA-TMJ database. 55-patient test set. SHAP values for feature importance.
- **Rationale for citing:** Most recent JIA-TMJ AI paper. Shows early detection focus.

---

## CATEGORY K: Prognostic Models

### K1. Gurgel et al. (2024)
**"A comprehensive patient-specific prediction model for TMJOA progression"**
*PNAS* 121:e2306132121.

- **Summary:** First prognostic (not diagnostic) model for TMJOA progression. EHPN ensemble. Accuracy 0.87, F1 0.82. Published in PNAS.
- **Rationale for citing:** Field trajectory from diagnosis to prognosis. PNAS venue demonstrates impact.

---

## CATEGORY L: Clinical Foundation and Diagnostic Criteria

### L1. Wang et al. (2015) — TMJOA pathogenesis review, *J. Dent. Res.* 94:666–673.
### L2. Schiffman et al. (2014) — DC/TMD criteria, *J. Oral Facial Pain Headache* 28:6–27.
### L3. Larheim et al. (2015) — CBCT for TMJ diagnostics, *Dentomaxillofac. Radiol.* 44:20140235.
### L4. Peck et al. (2014) — DC/TMD taxonomy expansion, *J. Oral Rehabil.* 41:2–23.

*(Already summarized in previous version)*

---

## CATEGORY M: Technical/Methodological

### M1. Dot et al. (2024) — DentalSegmentator, *J. Dent.* 147:105139.
### M2. MST (2025) — Medical Slice Transformer, *Sci. Rep.* 15:9041.
### M3. Carreira & Zisserman (2017) — I3D/Kinetics, *CVPR* 2017.
### M4. Yang et al. (2021) — ACS convolutions, *IEEE J. Biomed. Health Inform.* 25:3009.
### M5. Cubuk et al. (2020) — RandAugment, *NeurIPS* 2020.
### M6. Muhammad & Yeasin (2020) — EigenCAM, *IJCNN* 2020.

*(Already summarized in previous version)*

---

## SUMMARY: Complete Paper Count by Category

| Category | Count | Description |
|----------|-------|-------------|
| A. CBCT-based DL for TMJOA | 5 | Direct comparators |
| B. 3D Shape-based (Michigan) | 3 | SPHARM-PDM / SVA approaches |
| C. Multi-source ML (TMJOAI) | 4 | Radiomics + biomarkers + clinical |
| D. Panoramic-based OA | 3 | OPG classification |
| E. Non-CBCT modalities | 4 | Scintigraphy, MRI |
| F. TMJ Disc Displacement | 6 | Related but different task |
| G. TMJ Segmentation | 4 | Pipeline components |
| H. Non-imaging AI for TMD | 4 | Sound, NLP, clinical data |
| I. Systematic Reviews & MAs | 11 | Evidence syntheses |
| J. JIA-TMJ | 2 | Juvenile idiopathic arthritis |
| K. Prognostic Models | 1 | Disease progression |
| L. Clinical Foundation | 4 | DC/TMD, pathogenesis |
| M. Technical Methods | 6 | Augmentation, explainability, etc. |
| **TOTAL** | **57** | |

---

## RECOMMENDED CITATION STRATEGY FOR YOUR MANUSCRIPT

### Tier 1 — Must cite (core comparators + methodology):
A1–A4, B1, C1, D1, D2, I1, I2, L1–L4, M1–M6, K1 = **~22 references**

### Tier 2 — Should cite (strengthens positioning):
A5, B2, B3, C2–C4, D3, E1, I3–I6, I9, I10 = **~14 additional**

### Tier 3 — Consider citing (shows breadth):
E2–E4, F1–F3, G1, H1, I7–I8, I11, J1 = **~12 more**

**Total recommended: 30–48 references** (up from current 21)

The most critical gaps in your current manuscript are:
1. **Lee et al. (2020)** — the seminal CBCT DL paper (you may have it but with wrong ref info)
2. **Ribera et al. (2019)** and **Shoukri et al. (2019)** — completes the Michigan group story
3. **Jha et al. (2022)**, **Farook & Dudley (2023)**, **Zhang et al. (2024)** — critical recent reviews
4. **Al-Jaf et al. (2025)** and **Rokhshad et al. (2024)** — most recent systematic reviews
5. **Yun et al. (2025)** — largest patient dataset in TMJOA AI
6. **Kim et al. (2020)** — panoramic R-CNN comparator
