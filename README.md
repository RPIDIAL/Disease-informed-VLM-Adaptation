# Disease-informed VLM Adaptation

## Disease Diagnosis

### Framework overview
<p align='center'><img src="images/diagnosis.png" width=70% height=70% /></p>

### Disease-informed prompts
| Findings (Condition categories) | Attributes | Prompt Candidate 1 | Prompt Candidate 2 | Prompt Candidate 3 |
|----| ----| --------------|--------------|--------------|
| COVID-19 pneumonia | Desc(basic) | "A chest X-ray image of a patient with COVID-19." | "A radiograph of a COVID-19 patient." | "An X-ray image showing a patient diagnosed with COVID-19."|
|                    | Desc(texture) | "Texture Patterns include bilateral, patchy and ground-glass opacities (GGO) in the lungs. These opacities can vary in density and distribution." | "Texture patterns feature bilateral, patchy and ground-glass opacities in the lungs, which may differ in density and distribution." | "Texture patterns exhibit bilateral, patchy and ground-glass opacities (GGO) in the lungs, varying in density and distribution." |
|                    | Desc(shape) | "The opacities can have irregular shapes, appearing as hazy areas with fuzzy borders." | "The opacities may exhibit irregular contours, manifesting as hazy regions with indistinct edges." | "The opacities often feature irregular forms, presenting as blurred areas with indeterminate boundaries." |
|                    | Desc(location) | "The opacities are commonly located in the peripheral regions of the lungs, particularly in the lower lobes. They may involve multiple lung segments of both chest sides." | "The opacities typically appear in the peripheral areas of the lungs, especially in the lower lobes, and can affect multiple segments of both sides of the chest." | "Opacities are often found in the peripheral parts of the lungs, mainly within the lower lobes, and may affect several lung segments on both sides of the chest." |

<table>
  <tr>
    <th>Findings (Condition categories)</th>
    <th>Attributes</th>
    <th>Prompt Candidate 1</th>
    <th>Prompt Candidate 2</th>
    <th>Prompt Candidate 3</th>
  </tr>
  <tr>
    <td rowspan="4">COVID-19 pneumonia</td>
    <td>Desc(basic)</td>
    <td>"A chest X-ray image of a patient with COVID-19."</td>
    <td>"A radiograph of a COVID-19 patient."</td>
    <td>"An X-ray image showing a patient diagnosed with COVID-19."</td>
  </tr>
  <tr>
    <td>Desc(texture)</td>
    <td>"Texture Patterns include bilateral, patchy and ground-glass opacities (GGO) in the lungs. These opacities can vary in density and distribution."</td>
    <td>"Texture patterns feature bilateral, patchy and ground-glass opacities in the lungs, which may differ in density and distribution."</td>
    <td>"Texture patterns exhibit bilateral, patchy and ground-glass opacities (GGO) in the lungs, varying in density and distribution."</td>
  </tr>
  <tr>
    <td>Desc(shape)</td>
    <td>"The opacities can have irregular shapes, appearing as hazy areas with fuzzy borders."</td>
    <td>"The opacities may exhibit irregular contours, manifesting as hazy regions with indistinct edges."</td>
    <td>"The opacities often feature irregular forms, presenting as blurred areas with indeterminate boundaries."</td>
  </tr>
  <tr>
    <td>Desc(location)</td>
    <td>"The opacities are commonly located in the peripheral regions of the lungs, particularly in the lower lobes. They may involve multiple lung segments of both chest sides."</td>
    <td>"The opacities typically appear in the peripheral areas of the lungs, especially in the lower lobes, and can affect multiple segments of both sides of the chest."</td>
    <td>"Opacities are often found in the peripheral parts of the lungs, mainly within the lower lobes, and may affect several lung segments on both sides of the chest."</td>
  </tr>
</table>


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


