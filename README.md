

## Revisiting Online Map Uncertainty for More Reliable Trajectory Prediction in Driving Perception

Abstract: High-definition (HD) maps are essential for autonomous vehicle (AV) perception and planning but come with high labeling and maintenance costs. To address this, recent approaches estimate HD maps online from sensor data, allowing AVs to operate beyond pre-mapped regions. However, these methods are often developed in isolation from downstream tasks like trajectory prediction and lack uncertainty estimates, limiting their reliability. This paper revisits the impact of online map uncertainty on trajectory prediction and proposes a framework that integrates uncertainty-aware map representations into the prediction pipeline. By dynamically assessing map reliability and adapting predictions accordingly, our approach improves robustness in complex urban environments. Extensive experiments on benchmark datasets demonstrate that our method significantly outperforms state-of-the-art models, reducing prediction errors and enhancing AV decision-making. This work underscores the necessity of uncertainty-aware mapping for safer and more resilient autonomous systems.




## Our Contribution  ⚙️


- Revisiting the method proposed in \cite{gu2024producing} to explore its applicability to end-to-end motion forecasting (MF). Specifically, we analyze the method's core principles and extend its capabilities to accommodate the direct prediction of future agent trajectories within an end-to-end framework.
    
- Enhancing existing online map estimation techniques to generate uncertainty-aware map representations tailored for end-to-end motion forecasting. This involves developing methods to quantify and propagate uncertainty in online map features, thereby improving the robustness and reliability of map-based contextual cues for trajectory prediction tasks.
    
- Demonstrating the integration of these uncertainty-aware online mapping approaches within an end-to-end motion forecasting pipeline. By leveraging this integration, we highlight how our approach enables tighter coupling between online mapping and trajectory prediction, leading to improved performance and generalization in dynamic and partially observed environments.

    

## Our proposed architecture ⛓️
Our approach to online HD map estimation: multi-camera images are transformed to a shared BEV space, with map vertices modelled probabilistically to capture uncertainty. This setup is integrated into both GNN and Transformer-based encoders.

<img src="https://github.com/user-attachments/assets/60f4bff9-ec8b-4114-8ed2-ca86802c1081" width ="850">



Here's a complete GitHub-flavored `README.md` section including the two tables you requested, written in Markdown format and styled appropriately for direct inclusion in a GitHub repository:

---

## 🚗 Trajectory Prediction – Performance Comparison

We compare our proposed model (MMTraP) with the baseline and ground truth using the following metrics:

* **minADE**: Minimum Average Displacement Error
* **minFDE**: Minimum Final Displacement Error
* **MR**: Miss Rate

> 🔽 Lower values indicate better performance.

| **Model**    | **minADE ↓** | **minFDE ↓** | **MR ↓**     |
| ------------ | ------------ | ------------ | ------------ |
| **GT Map**   | 0.8809       | 1.489        | 0.1903       |
| **Baseline** | 2.21         | 5.16         | 0.93         |
| **Ours**     | 1.92 (--13%) | 4.21 (--18%) | 0.64 (--31%) |

---

## 🗺️ Map Estimation – Model Comparison

We evaluate our model against existing map estimation approaches based on modality, backbone architecture, training epochs, and various AP metrics:

* **AP\_Pred.**: Prediction accuracy
* **AP\_Div.**: Divider accuracy
* **AP\_Bound.**: Boundary accuracy
* **mAP**: Mean Average Precision

> 🔼 Higher values indicate better performance.

| **Model**    | **Modality** | **Backbone** | **Epoch** | **AP\_Pred.** | **AP\_Div.** | **AP\_Bound.** | **mAP**   |
| ------------ | ------------ | ------------ | --------- | ----------- | ------------ | -------------- | --------- |
| HDMapNet     | Camera       | Efficient-B0 | 30        | 14.4        | 21.7         | 33.0           | 23.0      |
| VectorMapNet | Camera       | ResNet-50    | 60        | 42.5        | 51.4         | 44.1           | 46.0      |
| MapVR        | Camera       | ResNet-50    | 24        | 55.0        | 61.8         | 59.4           | 58.73     |
| PivotNet     | Camera       | ResNet-50    | 30        | 53.8        | 55.8         | 59.6           | 56.4      |
| MapTR        | Camera       | ResNet-50    | 24        | 68.1        | 69.7         | 69.7           | 68.83     |
| **Ours**     | Camera       | ResNet-50    | 24        | **71.4**    | **73.7**     | **75.0**       | **73.36** |

---






## Qualitative results 📈

Multi-view camera images from nuScenes (left), with corresponding ground truth (first column, right), trajectory prediction (second column), and improved map uncertainty with trajectory prediction (third column).
<img src="https://github.com/user-attachments/assets/a9493660-addf-4fab-bb46-7867ec95c581" width ="650">










