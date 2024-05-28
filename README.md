# Disease-informed Adaptation of Vision-Language Models

This repository includes extra detailed information of our __Disease-informed Adaptation__ for adapting pre-trained medical Vision-Language Models (VLMs) to *newly identified* and *under represented* diseases.

The first version of [our work](http://arxiv.org/abs/2405.15728) is early accepted by __MICCAI 2024__.

*More results and the source code will be released soon!*

## Method Overview

### Proposed Framework
<p align='center'><img src="images/diagnosis.png" width=70% height=70% /></p>

### Disease-informed prompts

The complete set of prompt candidates for each attribute of every medical finding category is listed in the table below. Based on the disease-informed prompts (the ``Prompt candidate 1`` column) from our radiologist, we also utilized [*GPT-4*](https://arxiv.org/abs/2303.08774) to automatically generated the other two candidates (the ``Prompt candidate 2`` and ``Prompt candidate 3`` colums) for each descriptive attribute (texture, shape, and location) based on our predefined template. All these prompts were then manually revised with the help of a radiologist, ensuring that they are medically accurate. 

<table>
  <tr>
    <th style="width: 20%;"> Medical findings (Categories)</th>
    <th style="width: 25%;"> Attributes </th>
    <th style="width: 25%;"> Prompt candidate 1 </th>
    <th style="width: 25%;"> Prompt candidate 2 </th>
    <th style="width: 25%;"> Prompt candidate 3 </th>
  </tr>
  <tr>
    <td rowspan="4">COVID-19 pneumonia</td>
    <td><span style="white-space: nowrap;">Des<sub>k=1</sub>(basic)<sup id="a1"><a href="#f1">[1]</a></sup></span></td>
    <td>"A chest X-ray image of a patient with COVID-19."</td>
    <td>"A radiograph of a COVID-19 patient."</td>
    <td>"An X-ray image showing a patient diagnosed with COVID-19."</td>
  </tr>
  <tr>
    <td>Des<sub>k=1</sub>(texture)</td>
    <td>"Texture Patterns include bilateral, patchy and ground-glass opacities (GGO) in the lungs. These opacities can vary in density and distribution."</td>
    <td>"Texture patterns feature bilateral, patchy and ground-glass opacities in the lungs, which may differ in density and distribution."</td>
    <td>"Texture patterns exhibit bilateral, patchy and ground-glass opacities (GGO) in the lungs, varying in density and distribution."</td>
  </tr>
  <tr>
    <td>Des<sub>k=1</sub>(shape)</td>
    <td>"The opacities can have irregular shapes, appearing as hazy areas with fuzzy borders."</td>
    <td>"The opacities may exhibit irregular contours, manifesting as hazy regions with indistinct edges."</td>
    <td>"The opacities often feature irregular forms, presenting as blurred areas with indeterminate boundaries."</td>
  </tr>
  <tr>
    <td>Des<sub>k=1</sub>(location)</td>
    <td>"The opacities are commonly located in the peripheral regions of the lungs, particularly in the lower lobes. They may involve multiple lung segments of both chest sides."</td>
    <td>"The opacities typically appear in the peripheral areas of the lungs, especially in the lower lobes, and can affect multiple segments of both sides of the chest."</td>
    <td>"Opacities are often found in the peripheral parts of the lungs, mainly within the lower lobes, and may affect several lung segments on both sides of the chest."</td>
  </tr>
    <tr>
    <td rowspan="4">Non-COVID-19 pneumonia</td>
    <td><span style="white-space: nowrap;">Des<sub>k=2</sub>(basic)<sup id="a1"><a href="#f1">[1]</a></sup></span></td>
    <td>"A chest X-ray image of a patient with pneumonia."</td>
    <td>"A radiograph displaying the lung condition of a patient diagnosed with pneumonia."</td>
    <td>"An X-ray image of a pneumonia patient."</td>
  </tr>
  <tr>
    <td>Des<sub>k=2</sub>(texture)</td>
    <td>"Textual Patterns can include areas of increased lung density due to inflammatory infiltrates."</td>
    <td>"Textual patterns may feature regions of heightened lung density resulting from inflammatory infiltrates."</td>
    <td>"Textural patterns can display areas of elevated lung density caused by inflammatory infiltrates."</td>
  </tr>
  <tr>
    <td>Des<sub>k=2</sub>(shape)</td>
    <td>"In non-COVID pneumonia, opacities may have a lobar or segmental distribution, depending on the type of pneumonia."</td>
    <td>"Opacities can present with a lobar or segmental distribution, varying according to the specific type of pneumonia."</td>
    <td>"The distribution of opacities can be either lobar or segmental, based on the type of non-COVID pneumonia."</td>
  </tr>
  <tr>
    <td>Des<sub>k=2</sub>(location)</td>
    <td>"The location of pneumonia opacities can vary but is often seen in specific lobes or segments of the lung."</td>
    <td>"The position of pneumonia opacities varies but is usually observed in particular lobes or segments of the lung."</td>
    <td>"Pneumonia opacities can appear in various locations but commonly manifest in specific lobes or segments of the lung."</td>
  </tr>
  <tr>
    <td rowspan="4">Healthy individuals</td>
    <td><span style="white-space: nowrap;">Des<sub>k=3</sub>(basic)<sup id="a1"><a href="#f1">[1]</a></sup></span></td>
    <td>"A chest X-ray image of a normal healthy individual."</td>
    <td>"A chest X-ray showing the lungs of a normal, healthy individual."</td>
    <td>"An X-ray image of the chest from a healthy individual"</td>
  </tr>
  <tr>
    <td>Des<sub>k=3</sub>(texture)</td>
    <td>"No respiratory symptoms or underlying lung conditions, chest typically show clear lung fields with no areas of abnormal opacities."</td>
    <td>"In the absence of respiratory symptoms or pre-existing lung conditions, a chest X-ray generally reveals clear lung fields free from any abnormal opacities."</td>
    <td>"Without respiratory symptoms or pre-existing lung conditions, a chest X-ray typically shows clear lung fields without any abnormal opacities."</td>
  </tr>
  <tr>
    <td>Des<sub>k=3</sub>(shape)</td>
    <td>"No hazy areas with fuzzy borders."</td>
    <td>"There are no unclear regions with blurred boundaries."</td>
    <td>"There are no indistinct areas with blurred edges."</td>
  </tr>
  <tr>
    <td>Des<sub>k=3</sub>(location)</td>
    <td>"The whole lung fields appear homogeneous and translucent without any irregularities or opacities."</td>
    <td>"The entire lungs seem uniform and translucent, devoid of any irregularities or areas of opacity."</td>
    <td>"The whole lung fields present as homogeneous and translucent, lacking any irregularities or opacities."</td>
  </tr>
</table>

------

[1] <a id="f1">The default prompt template setting in the previous work, such as [*MaPLe*](https://arxiv.org/abs/2210.03117) and [*KgCoOp*](https://arxiv.org/abs/2303.13283).</a>


### Representation visualization
<p align='center'><img src="images/output.gif" width=25% height=25% /></p>

The figure above visualizes the evalution of the learnt representations epoch by epoch. 

Blue: Non-COVID pneumonia samples; Orange: COVID-19 samples.

Red cross: text-defined prompts; rectangular (blue and orange): learnt prototypes of Non-COVID pneumonia and COVID-19.

## Prerequisites

- Python 3.8
- PyTorch 1.8.1+
- A computing device with GPU

## Getting started

### Installation

- (Not necessary) Install [Anaconda3](https://www.anaconda.com/products/distribution)
- Install [CUDA 11.0+](https://developer.nvidia.com/cuda-11.0-download-archive)
- Install [PyTorch 1.12.1+](http://pytorch.org/)

Noted that our code is tested based on [PyTorch 1.12.1](http://pytorch.org/)

### Dataset & Preparation

The two medical image datasets used in our work are publicly available.

The __Fundus__ datasets include the [REFUGE](https://refuge.grand-challenge.org/) and the [RIM](https://github.com/miag-ull/rim-one-dl). We follow the [DoFE](https://arxiv.org/pdf/2010.06208.pdf) to preprocess the datasets.

The __Camelyon__ dataset is a subset from the [WILDS](https://wilds.stanford.edu/datasets/). This dataset is already preprocessed by the challenge.


### Measure the sensitivity map of an ERM model

Train and evaluate an ERM model by

```bash
python ./AAAIcodeSubmissoin__model_sensitivity_map/train_ERM.py
```

The model will be saved in `./AAAIcodeSubmissoin__model_sensitivity_map/save_dir`.


Measure the DoDiSS map of an ERM model by

```bash
python ./AAAIcodeSubmissoin__model_sensitivity_map/model_sensitivity_map.py
```

### Train model with Spectral Adversarial Data Mixup (SAMix)

Train and evaluate the models with SADA by

```bash
python ./AAAIcodeSubmissoin__SADA/train_SADA.py
```

The key __SAMix data augmentation module__ is in 

```
./AAAIcodeSubmissoin__SADA/sada.py
```

Augmentation settings for all datasets:

- `--epsilon` iteration of the checkpoint to load. #Default: 0.2
- `--step_size` step size of the adversarial attack on the amplitude spectrum. #Default: 0.08
- `--num_steps` batch size of the attack steps. #Default: 5
- `--tau` settings for the early stop acceleration. #Default: 1
- `--random_init` if or not initializing amplitude spertrums with random perturbations. #Default: True
- `--randominit_type` type of random init type. #Default: 'normal'
- `--criterion` loss functions to attack. #Default: 'ce', choices=['ce', 'kl']
- `--direction` neg: standard attack || pos:inverse attack. #Default: neg, choices=['pos','neg']

## Citation

Please cite these papers in your publications if it helps your research:

```bibtex
@article{zhang2022spectral,
  title={Spectral Adversarial MixUp for Few-Shot Unsupervised Domain Adaptation},
  author={Zhang, Jiajin and Chao, Hanqing and Dhurandhar, Amit and Chen, Pin-Yu and Tajer, Ali and Xu, Yangyang and Yan, Pingkun},
  journal={https://arxiv.org/abs/2309.01207},
  year={2023}
}
```

## Acknowledgement

We would like to thank the authors we cited in our paper for sharing their codes.

