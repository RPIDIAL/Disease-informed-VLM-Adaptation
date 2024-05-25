# Disease-informed VLM Adaptation

## Disease Diagnosis

### Framework overview
<p align='center'><img src="images/diagnosis.png" width=70% height=70% /></p>

### Disease-informed prompts

<table>
  <tr>
    <th style="width: 20%;"> Findings (Condition categories)</th>
    <th style="width: 20%;"> Attributes </th>
    <th style="width: 20%;"> Prompt Candidate 1</th>
    <th style="width: 20%;"> Prompt Candidate 2</th>
    <th style="width: 20%;"> Prompt Candidate 3</th>
  </tr>
  <tr>
    <td rowspan="4">COVID-19 pneumonia</td>
    <td>$$Des_{k=1}(basic)$$<sup id="a1">[1]</sup></td>
    <td>"A chest X-ray image of a patient with COVID-19."</td>
    <td>"A radiograph of a COVID-19 patient."</td>
    <td>"An X-ray image showing a patient diagnosed with COVID-19."</td>
  </tr>
  <tr>
    <td>$$Des_{k=1}(texture)$$</td>
    <td>"Texture Patterns include bilateral, patchy and ground-glass opacities (GGO) in the lungs. These opacities can vary in density and distribution."</td>
    <td>"Texture patterns feature bilateral, patchy and ground-glass opacities in the lungs, which may differ in density and distribution."</td>
    <td>"Texture patterns exhibit bilateral, patchy and ground-glass opacities (GGO) in the lungs, varying in density and distribution."</td>
  </tr>
  <tr>
    <td>$$Des_{k=1}(shape)$$</td>
    <td>"The opacities can have irregular shapes, appearing as hazy areas with fuzzy borders."</td>
    <td>"The opacities may exhibit irregular contours, manifesting as hazy regions with indistinct edges."</td>
    <td>"The opacities often feature irregular forms, presenting as blurred areas with indeterminate boundaries."</td>
  </tr>
  <tr>
    <td>$$Des_{k=1}(location)$$</td>
    <td>"The opacities are commonly located in the peripheral regions of the lungs, particularly in the lower lobes. They may involve multiple lung segments of both chest sides."</td>
    <td>"The opacities typically appear in the peripheral areas of the lungs, especially in the lower lobes, and can affect multiple segments of both sides of the chest."</td>
    <td>"Opacities are often found in the peripheral parts of the lungs, mainly within the lower lobes, and may affect several lung segments on both sides of the chest."</td>
  </tr>
    <tr>
    <td rowspan="4">Non-COVID-19 pneumonia</td>
    <td>$$Des_{k=2}(basic)$$<sup id="a1">[1]</sup></td>
    <td>"A chest X-ray image of a patient with pneumonia."</td>
    <td>"A radiograph displaying the lung condition of a patient diagnosed with pneumonia."</td>
    <td>"An X-ray image of a pneumonia patient."</td>
  </tr>
  <tr>
    <td>$$Des_{k=2}(texture)$$</td>
    <td>"Textual Patterns can include areas of increased lung density due to inflammatory infiltrates."</td>
    <td>"Textual patterns may feature regions of heightened lung density resulting from inflammatory infiltrates."</td>
    <td>"Textural patterns can display areas of elevated lung density caused by inflammatory infiltrates."</td>
  </tr>
  <tr>
    <td>$$Des_{k=2}(shape)$$</td>
    <td>"In non-COVID pneumonia, opacities may have a lobar or segmental distribution, depending on the type of pneumonia."</td>
    <td>"Opacities can present with a lobar or segmental distribution, varying according to the specific type of pneumonia."</td>
    <td>"The distribution of opacities can be either lobar or segmental, based on the type of non-COVID pneumonia."</td>
  </tr>
  <tr>
    <td>$$Des_{k=2}(location)$$</td>
    <td>"The location of pneumonia opacities can vary but is often seen in specific lobes or segments of the lung."</td>
    <td>"The position of pneumonia opacities varies but is usually observed in particular lobes or segments of the lung."</td>
    <td>"Pneumonia opacities can appear in various locations but commonly manifest in specific lobes or segments of the lung."</td>
  </tr>
  <tr>
    <td rowspan="4">Healthy individuals</td>
    <td>$$Des_{k=2}(basic)$$<sup id="a1">[1]</sup></td>
    <td>"A chest X-ray image of a normal healthy individual."</td>
    <td>"A chest X-ray showing the lungs of a normal, healthy individual."</td>
    <td>"An X-ray image of the chest from a healthy individual"</td>
  </tr>
  <tr>
    <td>$$Des_{k=2}(texture)$$</td>
    <td>"No respiratory symptoms or underlying lung conditions, chest typically show clear lung fields with no areas of abnormal opacities."</td>
    <td>"In the absence of respiratory symptoms or pre-existing lung conditions, a chest X-ray generally reveals clear lung fields free from any abnormal opacities."</td>
    <td>"Without respiratory symptoms or pre-existing lung conditions, a chest X-ray typically shows clear lung fields without any abnormal opacities."</td>
  </tr>
  <tr>
    <td>$$Des_{k=2}(shape)$$</td>
    <td>"No hazy areas with fuzzy borders."</td>
    <td>"There are no unclear regions with blurred boundaries."</td>
    <td>"There are no indistinct areas with blurred edges."</td>
  </tr>
  <tr>
    <td>$$Des_{k=2}(location)$$</td>
    <td>"The whole lung fields appear homogeneous and translucent without any irregularities or opacities."</td>
    <td>"The entire lungs seem uniform and translucent, devoid of any irregularities or areas of opacity."</td>
    <td>"The whole lung fields present as homogeneous and translucent, lacking any irregularities or opacities."</td>
  </tr>
</table>

------

[1] <a id="f1">The default prompt template setting in the previous work, such as [MaPLe](https://arxiv.org/abs/2210.03117) and [KgCoOp](https://arxiv.org/abs/2303.13283).</a>

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


