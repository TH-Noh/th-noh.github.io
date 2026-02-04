---
layout: page
title: AI-based Prediction Model Development
description: Predicting Supply-Chain Relationships with Multi-Feature Graph Attention Networks
img: assets/img/MFRGAT_Framework.png
importance: 1
category: research
giscus_comments: False
---

<div><h3><b>Project Overview</b></h3></div>

In this research, we developed a **Graph Attention Netowkr (GAT)–based model** to predict **potential supply-chain relationships** between companies in a large-scale real-world supply chain network.
The key objective was to go beyond existing supplier networks and identify **previously unknown but plausible supply relationships** by jointly modeling network structure and semantic company attributes

<hr style="border: 1px solid #ccc;">

<div><h3><b>Multi-Feature Graph Attention Model (MFRGAT)</b></h3></div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/MFRGAT_Framework_Full.png" title="Framework for MFRGAT" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">Framework for MFRGAT</div>

We proposed a Multi-Feature Representation Graph Attention Network (MFRGAT) that integrates heterogeneous information sources:

- **Graph embeddings**: Used node2vec to capture both local and global topological structures of the supply chain network.

- **Product embeddings**: Applied semantic word embeddings (fastText) to encode companies’ product characteristics.

- **Industry features**: Incorporated industry-level categorical information to preserve sector-specific supply patterns.

These representations were concatenated and fed into a Graph Attention Network (GAT), allowing the model to learn adaptive importance weights between companies instead of relying on fixed neighborhood aggregation.

<div><b> Results: </b></div>

Compared to traditional machine learning models (SVM, DNN-based methods) and state-of-the-art graph models (GCN-based approaches), the proposed model consistently achieved higher accuracy, F1-score, and specificity, demonstrating superior ability to capture complex supply-chain structures

<hr style="border: 1px solid #ccc;">

<div><h3><b>Industry-Level Performance Analysis with Heatmaps</b></h3></div>

To evaluate robustness across sectors, we analyzed model performance **by industry pair** using heatmap visualizations.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/GCN_F1.jpg" title="F1_GCN" class="img-fluid rounded z-depth-1" %}
        <div class="caption">F1 score of the Baseline GCN</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/GAT_F1.jpg" title="F1_GAT" class="img-fluid rounded z-depth-1" %}
        <div class="caption">F1 score of the MFRGAT</div>
    </div>
</div>

- Each cell in the heatmap represents the F1-score for predicting supply relationships between two industry sectors.

- This analysis highlights that, compared to baseline GCN models, the proposed model consistently achieves **higher performance across individual industry sectors**.

 It demonstrates **superior capability in capturing supply-chain relationships** within heterogeneous industrial ecosystems.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Robustness Analysis via Negative Sampling & Statistical Validation</b></h3></div>

Since real-world supply chain data contains only observed (positive) relationships, we generated **multiple datasets by varying the negative sampling ratio** and compared model performances across these datasets.

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Model_Performances.jpg" title="performances" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Ablation Study Results</div>
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Paired_t-test.jpg" title="t-test" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Paired t-test Results Comparing MFRGAT with other GAT Models</div>
    </div>
</div>

<div><b>Negative sampling (D1–D5):</b></div>

- From D1 to D5, the proportion of negative samples is progressively increased (D1: 0.3, D2: 0.5, D3: 1.0, D4: 1.3, D5: 1.5), making link prediction increasingly difficult.

<div><b>Ablation comparison:</b></div>

- **PRGAT (product features only):** Limited performance, indicating that semantic product information alone is insufficient.

- **GRGAT (graph features only):** Significantly better than PRGAT, highlighting the importance of network topology.

- **MFRGAT (product + graph features):** Achieved the best performance by jointly modeling semantic and structural information.

<div><b>Statistical validation:</b></div>

- **Paired t-tests at the 99% confidence level** confirmed that performance improvements of MFRGAT over all baselines and ablation variants were statistically significant.

This process confirmed the **stability** and **robustness** of the model under different data imbalance conditions

<hr style="border: 1px solid #ccc;">

<div><h3><b>Discovering New Supply-Chain Networks</b></h3></div>

Beyond numerical metrics, the model was applied to **extend real-world supply chain networks**:

- The predicted links introduced **new potential supplier–buyer connections** that did not previously exist in the observed data.

- High prediction accuracy and consistency across industries provide strong evidence that these newly inferred links are structurally and semantically plausible.

This demonstrates that the model is not merely fitting existing networks, but can serve as a **decision-support tool** for discovering alternative suppliers and improving supply chain resilience

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/original_network.jpg" title="original supplychain network" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Original Supplychain Network</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/extended_network.png" title="extended supplychain network" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Extended Supplychain Network</div>
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>Key Takeaway</b></h3></div>

This project shows how attention-based graph learning combined with multi-feature representations can uncover hidden structures in large-scale supply chain networks, enabling both accurate prediction and meaningful real-world insights.