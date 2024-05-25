# Disease-informed VLM Adaptation

## Disease Diagnosis

### Framework overview
<p align='center'><img src="images/diagnosis.png" width=70% height=70% /></p>

### Disease-informed prompts
| XAI Methods | Description | Applications in MedAI |
| :--- | :---- | :---- |
| [Vanilla Grad](https://arxiv.org/abs/1312.6034) | It calculates the impact of pixels by approximating their respective gradient on the prediction.| [1] [Breast Mass Classification from Mammograms using Deep Convolutional Neural Networks](https://arxiv.org/pdf/1612.00542.pdf ). NIPS 2016 workshop <br> [2] [AI for Radiographic COVID-19 Detection Selects Shortcuts Over Signal](https://www.nature.com/articles/s42256-021-00338-7.pdf ). Nature Machine Intelligence, 2021: 1-10. <br> [3] [Iterative Augmentation of Visual Evidence for Weakly-Supervised Lesion Localization in Deep Interpretability Frameworks: Application to Color Fundus Images](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9103111 ). IEEE TMI, 2020 Nov, 39(11): 3499-3511. <br>[4] [Artificial Intelligence System Reduces False-positive Findings in the Interpretation of Breast Ultrasound Exams](https://www.nature.com/articles/s41467-021-26023-2 ). Nature Communications, 2021, 12. <br> [5] [Assessing the Trustworthiness of Saliency Maps for Localizing Abnormalities in Medical Imaging](https://pubs.rsna.org/doi/pdf/10.1148/ryai.2021200267), Radiology: AI, 2021, 3(6): e200267.|
| [Grad x Input](https://arxiv.org/pdf/1605.01713.pdf) | This method is initially proposed to improve sharpness of attribution maps. It multiplies the vanila grad map with the input. | [1] [Testing the Robustness of Attribution Methods for Convolutional Neural Networks in MRI-based Alzheimer’s Disease Classification](https://arxiv.org/pdf/1909.08856.pdf). iMIMIC 2019.|

### Prototype initialization
<p align='center'><img src="images/proto_init.png" width=70% height=70% /></p>


### Representation visualization
<p align='center'><img src="images/output.gif" width=25% height=25% /></p>

The figure above visualizes the evalution of the learnt representations epoch by epoch. 

Blue: Non-COVID pneumonia samples; Orange: COVID-19 samples.

Red cross: text-defined prompts; rectangular (blue and orange): learnt prototypes of Non-COVID pneumonia and COVID-19.

## Disease Risk Estimation

### Framework overview
<p align='center'><img src="images/risk_estimation.png" width=70% height=70% /></p>


