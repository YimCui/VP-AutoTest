<head>
 <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
 <script type="text/x-mathjax-config">
 MathJax.Hub.Config({
 tex2jax: {
 skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
 inlineMath: [['$','$']]
 }
 });
 </script>
</head>

# VP-AutoTest: A Virtual-Physical Fusion Autonomous Driving Testing Platform

**[Yiming Cui](https://tops.tongji.edu.cn/info/1131/1818.htm)**, [Shiyu Fang](https://tops.tongji.edu.cn/info/1033/1190.htm), [Jiarui Zhang](https://tops.tongji.edu.cn/info/1132/1815.htm),[Yan Huang](https://tops.tongji.edu.cn/info/1033/1189.htm), [Peng Hang](https://tops.tongji.edu.cn/info/1031/1383.htm), [Jian Sun](https://tops.tongji.edu.cn/info/1031/1187.htm)  

[Department of Traffic Engineering and Key Laboratory of Road and Traffic Engineering, Ministry of Education, Tongji University](https://tops.tongji.edu.cn/)  

## Abstract

The rapid development of autonomous vehicles has led to a surge in testing demand. Traditional testing methods, such as virtual simulation, closed-course, and public road testing, face several challenges, including unrealistic vehicle states, limited testing capabilities, and high costs. These issues have prompted increasing interest in virtual-physical fusion testing. However, despite its potential, virtual-physical fusion testing still faces challenges, such as limited element types, narrow testing scope, and fixed evaluation metrics. 
To address these challenges, we propose the Virtual-Physical Testing Platform for Autonomous Vehicles (VP-AutoTest), which integrates over ten types of virtual and physical elements, including vehicles, pedestrians, and roadside infrastructure, to replicate the diversity of real-world traffic participants. The platform also supports both single-vehicle interaction and multi-vehicle cooperation testing, employing adversarial testing and parallel deduction to accelerate fault detection and explore algorithmic limits, while OBU and Redis communication enable seamless vehicle-to-vehicle (V2V) and vehicle-to-infrastructure (V2I) cooperation across all levels of cooperative automation. Furthermore, VP-AutoTest incorporates a multidimensional evaluation framework and AI-driven expert systems to conduct comprehensive performance assessment and defect diagnosis. Finally, by comparing virtual–physical fusion test results with real-world experiments, the platform performs credibility self-evaluation to ensure both the fidelity and efficiency of autonomous driving testing. Please refer to the website for the full testing functionalities on the autonomous driving public service platform OnSite: \href{https://www.onsite.com.cn/}{https://www.onsite.com.cn/}.

## Key Contributions

To address the aforementioned challenges, we propose the Virtual-Physical Testing platform for Autonomous vehicles (VP-AutoTest). By integrating over ten distinct virtual-physical elements, it enables both single-vehicle and multi-vehicle testing functionalities. Additionally, it incorporates multidimensional evaluation and defect diagnosis, thus supporting comprehensive and systematic testing of AD systems. The key contributions of the proposed platform are summarized as follows.

**Integration of Diverse Virtual-Physical Elements**: To replicate the complexity and diversity of real-world traffic participants, the proposed VP-AutoTest integrates a wide range of physical and virtual components. The physical elements include Connected and Automated Vehicles (CAVs), cloud-controlled vehicles, mannequins, and roadside infrastructure. The virtual components consist of simulated CAVs, remotely operated vehicles controlled by driving simulators, and simulated background traffic flows, enabling a comprehensive and realistic testing environment.

**Single and Multi-Vehicle Testing Capabilities**: To efficiently evaluate the various capabilities of AD systems, platform supports both single-vehicle interaction and multi-vehicle cooperation tests. For single-vehicle interaction, we introduce adversarial testing to adjust challenge intensity based on system performance, and parallel deduction to simulate high-risk takeover scenarios for evaluating decision-making algorithms. In the multi-vehicle cooperation tests, the platform utilizes communication between OBUs and Redis to evaluate V2V and V2I cooperation, covering the entire spectrum of Cooperative Driving Automation (CDA).

**Multidimensional Evaluation and Defect Diagnosis**: The platform facilitates multidimensional comparisons of algorithms, both horizontally and vertically, enabling detailed performance assessments across various versions. Additionally, it incorporates AI-driven expert systems that leverage knowledge reasoning to generate comprehensive diagnostic reports for the Algorithm Under Test (AUT), providing constructive insights for algorithmic improvement and optimization.

**Platform Credibility Self-Evaluation**: Since credibility remains one of the most critical challenges in virtual–physical fusion testing, VP-AutoTest incorporates a credibility self-evaluation mechanism that quantitatively assesses the reliability of each test case. Based on credibility analysis, the platform adaptively adjusts element combinations—adding more physical components in low-credibility scenarios to enhance realism and increasing virtual components in high-credibility ones to improve efficiency, thereby enhancing testing efficiency while ensuring credibility.

<div align="center">
  <img src="./Figs/Framework.png" alt="示意图" width="800">
  <p>Data transmission pipeline of the VPF-ADTP</p>
</div>

## Overview of the Proposed VP-AutoTest Framework
The proposed VP-AutoTest is designed to achieve seamless integration between the physical and virtual domains, as illustrated in Fig.~\ref{Framework}. Built upon digital twin technology, the platform establishes a spatiotemporally aligned digital twin base that provides a unified reference for virtual–physical fusion testing. Static elements are digitally reconstructed based on high-definition maps to form the spatial reference framework of the test site. Dynamic elements are captured and localized in real time through perception and sensing devices deployed across the test field. Simulated elements are synchronized with real-world perception data, enabling fusion at the perception layer. Together, these three types of elements ensure high-fidelity synchronization between the real and virtual worlds, thereby supporting unified multi-source data processing, accurate entity reconstruction, and reliable algorithm validation.

Specifically, in terms of temporal synchronization, VP-AutoTest supports multiple clock alignment standards according to application requirements. The Network Time Protocol (NTP) achieves a synchronization accuracy of 10 ms, while the Precision Time Protocol (PTP) provides accuracy up to 50 ns, and Global Navigation Satellite System (GNSS) synchronization reaches 10 ns. For spatial synchronization, a centimeter-level high-definition map is used to construct a unified spatial reference system. The three-dimensional scene reconstruction service integrates physical features and virtual models and is regularly updated to ensure consistency between domains.

To optimize the allocation of virtual and physical elements and improve resource utilization, VP-AutoTest introduces a human–vehicle–road–environment coupling risk-field model to quantify the influence of background traffic on the test target. A risk contribution evaluation system is then established to determine the optimal distribution of virtual and physical elements based on risk gradient analysis, ensuring economical resource deployment and maximal risk coverage. Combined with the platform’s credibility self-evaluation mechanism, the virtual–physical composition is dynamically adjusted across iterative tests, maintaining testing credibility while enhancing efficiency.

As shown in Fig.~\ref{Framework}, the physical test field includes a variety of real-world driving scenarios such as parking lots, straight roads, intersections, and roundabouts. The virtual environment, built upon the high-definition map (HD map), achieves a one-to-one digital replica of these physical scenes. Through the fusion of virtual environments that generate controllable background traffic flows, virtual CAVs, and remotely operated HDVs, the platform enables free combinations and dynamic interactions among virtual and physical participants. This design supports both single-vehicle and multi-vehicle testing requirements. The single-vehicle testing includes adversarial testing and parallel deduction, which focus on evaluating decision-making performance and system robustness. The multi-vehicle testing involves V2V and V2I cooperation tests to assess cooperative driving capabilities under complex traffic conditions.
In addition, the platform provides comprehensive evaluation capabilities for both algorithm performance and its own credibility. It supports multidimensional and customizable assessments of algorithmic intelligence, enabling defect diagnosis and targeted improvement. Meanwhile, the platform can also self-evaluate its credibility to ensure its reliability and usability.

<div align="center">
  <img src="./Figs/Workflow.png" alt="示意图" width="700">
  <p>Data transmission pipeline of the VPF-ADTP</p>
</div>

## Testing Ability & Corresponding Cases
We systematically presents the testing capabilities supported by the virtual-physical fusion testing platform. These capabilities are categorized into single-vehicle and multi-vehicle virtual-physical fusion testing, with each category elaborating on the corresponding testing objectives, technical implementation methodologies, and representative test cases conducted based on the platform.

### Single-vehicle Virtual-physical Fusion Testing
The proposed VPF-ADTP platform offers two key capabilities for single-vehicle testing. (1) Adversarial testing: adaptively generating adversarial behaviors for surrounding vehicles to rapidly expose the capability boundaries of the Algorithm Under Test (AUT).And (2) parallel deduction testing: when a takeover occurs, running the AUT in parallel to assess whether it could in fact handle the current scenario, thereby identifying and correcting false-positive takeovers.

#### (1) Adversarial Testing
Adversarial testing is a methodology designed to evaluate the performance of the VUT under extreme scenarios by adaptively adjusting opposing strategies based on its real-time behavior. The primary objective is to efficiently expose critical weaknesses that may be difficult to identify through standard testing procedures, thereby more effectively exploring the capability boundaries of the tested algorithms.
However, a notable limitation of existing research is its predominant reliance on purely simulated environments, with a lack of application and validation on real-world vehicle platforms and in physical test conditions. 
Due to the nature of adversarial testing, which explores the boundary of vehicle capabilities, real-world field tests inherently carry certain safety risks. To address this gap, this study incorporates adversarial testing capabilities within the virtual–physical fusion testing platform, fully leveraging both virtual and physical vehicles as adversaries to construct realistic, safe, and efficient adversarial environments.

<div align="center">
  <figure>
    <video muted controls width="720">
      <source src="./Videos/AT-4views.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Adversarial Testing case</figcaption>
  </figure>
</div>

#### (2) Parallel Deduction Testing
During on-road testing of autonomous driving systems, a safety operator is typically assigned to take over control when signs of hazardous or improper behavior are detected. While this intervention ensures testing safety, it also prevents the autonomous system from completing complex scenario tasks; even when the system possesses the capability to handle them, execution may be prematurely terminated. In other words, false-positive takeovers may prevent the AUT’s capability boundaries from being fully evaluated. To address this issue, the platform is equipped with parallel deduction testing capability.

<div align="center">
  <figure>
    <video muted controls width="720">
      <source src="./Videos/PD.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Parallel deduction testing case</figcaption>
  </figure>
</div>

### Multi-vehicle Virtual-physical Fusion Testing
The virtual–physical fusion platform leverages comprehensive virtual and physical elements to build controllable and repeatable cooperative scenarios, and establishes bidirectional low-latency communication along with unified spatiotemporal synchronization, ensuring stable validation of cooperative algorithms. Based on these capabilities, the platform supports both V2V and V2I cooperation testing.

#### (1) Vehicle-vehicle Cooperation Testing
Physical vehicles are equipped with cooperative controllers that support millisecond-level communication latency, enabling real-time sharing of information such as current position, intended trajectory, and upcoming decisions. Given that V2V scenarios often involve a large number of participants while physical vehicle resources are typically limited, the platform also integrates a controllable virtual background traffic flow. This is achieved via a Redis database interface that reads and writes the states and actions of virtual cooperation vehicles in real time, allowing the system to simulate large-scale, high-density cooperative scenarios.Following the SAE J3216 standard and considering the range of variables transmitted in V2V communication, the proposed Vehicle-Vehicle Cooperation Testing framework evaluates four key levels of CDA: state sharing, intention sharing, cooperative decision-making, and cooperative control. 


<div align="center">
  <figure>
    <video muted controls width="720">
      <source src="./Videos/v2v-intention.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Vehicle-vehicle cooperation with intention sharing testing case</figcaption>
  </figure>
</div>


<div align="center">
  <figure>
    <video muted controls width="720">
      <source src="./Videos/v2v-decision.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Vehicle-vehicle cooperation with cooperative decision-making testing case</figcaption>
  </figure>
</div>


#### (2) Vehicle-infrastructure Cooperation Testing
The platform supports flexible configuration and combination of virtual and physical V2I testing elements, enabling the construction of special traffic event scenarios through digital twin technology and the safe, repeatable reproduction of identical testing conditions, thereby overcoming the limitations of uncontrollable events in real-road environments. Physical vehicles, RSUs, MEC edge computing units, cloud control platforms, and virtual background traffic are integrated into a unified testing system, achieving high-precision temporal synchronization of multi-source perception data and bidirectional real-time communication.

<div align="center">
  <figure>
    <video muted controls width="720">
      <source src="./Videos/v2i.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Vehicle-infrastructure cooperation testing cases</figcaption>
  </figure>
</div>

## Appendix

### **👉 A: Please refer to the website for the full testing functionalities [Onsite](https://www.onsite.com.cn/)**.

### **👉 B: Supplementary VRU test materials**
#### (1) Pedestrian road crossing
<div align="center">
  <figure>
    <video muted controls width="720">
      <source src="./Videos/pedestrian.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Pedestrian road crossing testing cases</figcaption>
  </figure>
</div>

#### (2) Reckless non-motor vehicles
<div align="center">
  <figure>
    <video muted controls width="720">
      <source src="./Videos/non-motor.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Reckless non-motor vehicles testing cases</figcaption>
  </figure>
</div>

### **👉 C: Supplementary Sensitivity Analysis of DTW and PCA**

To further examine the influence of DTW and PCA on the credibility comparison results, we conducted sensitivity analyses with different numbers of retained principal components and without PCA, together with a comparison with and without DTW, using the same 15 cases.

#### (1) Sensitivity Analysis of the Number of Retained Principal Components

To investigate the influence of PCA dimensionality, we kept the same 15 cases and their original DTW alignment paths fixed, retained 1, 2, 4, and 8 principal components, respectively, and additionally evaluated the full-dimensional results without PCA. Each input trajectory feature was standardized using **z-score standardization**:

`x̃(t,j) = [x(t,j) − μ(j)] / σ(j)`

Here, μ(j) and σ(j) denote the mean and standard deviation of the corresponding feature, respectively. The standardization parameters were kept unchanged across the different PCA settings.

The **mean cumulative explained variance was 47.6%, 64.3%, 82.7%, and 97.8% when retaining 1, 2, 4, and 8 principal components, respectively**. These averages were calculated across the 30 real-world–platform trajectory comparisons associated with the 15 cases. When multiple principal components were retained, the metrics were calculated directly in the retained principal-component space, without reconstruction. Without PCA, the same calculations were applied directly to all standardized state features. PCC, TIC, Cross-FuzzyEn, and CS-PSD were calculated separately for each dimension and then averaged with equal weights, whereas RMSE was calculated over all time points and evaluated dimensions.

**Table 1. Sensitivity analysis for different PCA settings**

| PCA setting | PCC ↑ | RMSE ↓ | TIC ↓ | Cross-FuzzyEn ↓ | CS-PSD ↑ |
|:---|:---:|:---:|:---:|:---:|:---:|
| 1 retained PC | **0.977** / 0.967 (0.018) | **0.583** / 0.757 (0.003) | **0.133** / 0.168 (0.003) | **0.112** / 0.122 (0.208) | **0.997** / 0.994 (0.169) |
| 2 retained PCs | 0.786 / 0.792 (0.679) | **0.983** / 1.057 (0.303) | **0.299** / 0.325 (0.252) | **0.138** / 0.145 (0.561) | **0.954** / 0.926 (0.151) |
| 4 retained PCs | **0.544** / 0.522 (0.359) | **1.122** / 1.199 (0.188) | **0.470** / 0.495 (0.169) | **0.248** / 0.311 (0.030) | **0.852** / 0.798 (0.151) |
| 8 retained PCs | **0.303** / 0.302 (0.847) | **1.014** / 1.055 (0.208) | **0.596** / 0.607 (0.389) | **0.227** / 0.283 (0.008) | **0.789** / 0.776 (0.978) |
| Without PCA | **0.656** / 0.643 (0.454) | **0.884** / 0.912 (0.252) | **0.410** / 0.420 (0.359) | **0.081** / 0.103 (<0.001) | **0.860** / 0.842 (0.151) |

*Each entry reports the VP-AutoTest mean / DC-in-the-loop mean (raw two-sided paired Wilcoxon p-value), based on 15 case pairs. Bold values indicate better mean performance by VP-AutoTest.*

The results are presented in Table 1. Across the reported 15 cases, VP-AutoTest achieves better overall mean RMSE, TIC, Cross-FuzzyEn, and CS-PSD values than DC-in-the-loop under all evaluated PCA settings, including without PCA. Its mean PCC is also higher under all settings except when retaining two principal components, where it is slightly lower. These results indicate that, although the magnitude and statistical significance of the differences vary with the number of retained components, VP-AutoTest generally exhibits an overall mean trend toward closer agreement with the real-world reference results across the evaluated configurations.

#### (2) Further Explanation of DTW and Comparison With and Without DTW

Temporal misalignment and discrepancies intrinsic to virtual–physical testing are coupled and difficult to separate rigorously. Consequently, it cannot be directly determined whether the temporal differences removed by DTW include meaningful delays. In other words, **the value of DTW cannot be established or dismissed solely on the basis of increases or decreases in similarity metrics before and after its application.**

Nevertheless, we additionally report results without DTW to provide supplementary evidence by examining whether the platform comparison remains consistent: if VP-AutoTest more closely reproduces the real-world results than DC-in-the-loop both with and without DTW, this would strengthen the original conclusion to some extent.

The comparison uses the same 15 cases. Both settings retain the full trajectories, reuse the original standardization parameters, and fit a one-dimensional PCA after temporal processing according to the same fitting procedure. The five metrics are calculated directly on PC1. Without DTW, **point-by-point alignment on the normalized time axis** is used to establish correspondence, without nonlinear DTW matching.

The DTW setting follows the original full-trajectory processing procedure. The Euclidean distance between standardized multidimensional state vectors is used as the local cost, and the cumulative cost along the alignment path is minimized. The alignment uses fixed endpoints, monotonicity, and continuity constraints, with allowable steps of (1, 0), (0, 1), and (1, 1). No additional time-window or slope constraints are imposed. The five metric results are presented in Table 2.

**Table 2. Comparison with and without DTW**

| DTW setting | PCC ↑ | RMSE ↓ | TIC ↓ | Cross-FuzzyEn ↓ | CS-PSD ↑ |
|:---|:---:|:---:|:---:|:---:|:---:|
| Without DTW | 0.956 / 0.959 (0.277) | 0.928 / 0.875 (0.762) | 0.208 / 0.196 (0.847) | **0.090** / 0.096 (0.035) | 0.994 / 0.994 (0.599) |
| With DTW | **0.977** / 0.967 (0.018) | **0.583** / 0.757 (0.003) | **0.133** / 0.168 (0.003) | **0.112** / 0.122 (0.208) | **0.997** / 0.994 (0.169) |

*Each entry reports the VP-AutoTest mean / DC-in-the-loop mean (raw two-sided paired Wilcoxon p-value), based on 15 case pairs. Both settings retain one principal component. Without DTW uses linear-progress resampling. Bold values indicate better mean performance by VP-AutoTest.*

Without DTW, the differences between the two platforms in PCC, RMSE, TIC, and CS-PSD do not reach the 0.05 significance level for individual tests, whereas **Cross-FuzzyEn remains significantly favorable to VP-AutoTest**, with a mean of 0.090 compared with 0.096 for DC-in-the-loop (p = 0.035). Thus, the results without DTW provide supplementary support for closer agreement between VP-AutoTest and the real-world results in terms of Cross-FuzzyEn. However, because temporal misalignment and discrepancies intrinsic to virtual–physical testing cannot be rigorously separated through this comparison, these numerical results serve only as supplementary reference evidence and cannot directly determine whether the temporal differences removed by DTW are meaningful.

## Contact

If you have any questions, feel free to contact us (yim211@tongji.edu.cn).
