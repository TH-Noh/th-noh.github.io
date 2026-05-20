---
layout: page
title: KPMG Data Analytics Competition
description: 2025 KPMG + Layton Construction Data Analytics Challenge
permalink: /projects/kpmg-data-analytics-competition/
img: assets/img/kpmg_thumbnail.png
importance: 2
category: competition
---

<div><h3><b>Overview</b></h3></div>

Participated in a data analytics competition focused on transforming HR data into actionable insights for **workforce planning and retention strategy**. The project emphasized building **decision-support dashboards and predictive models** rather than isolated descriptive statistics.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Analytical Approach & Deliverables</b></h3></div>

<b>Workforce & Demographics Analysis</b>

Analyzed workforce demographics, tenure distribution, and hiring trends using Power BI.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/KPMG_demographics.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/KPMG_diversity.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/KPMG_RoleJobs.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Designed an interactive demographics dashboard to visualize:

- Headcount trends and workforce composition

- Tenure and generational distribution

- Department-level workforce structure

<div><b>Value to the company:</b></div>

Enabled leadership to quickly assess workforce composition and identify structural risks related to succession, diversity, and capacity planning.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Turnover Analysis & Reporting Design</b></h3></div>

Conducted multi-year turnover analysis segmented by:

- Tenure, job family, department, and generation

Differentiated programmatic turnover (e.g., interns) from core employee turnover to improve reporting clarity.

Built a turnover dashboard highlighting:

- High-risk employee segments

- Timing patterns of employee exits

- Retention trends over time

<div><b>Value to the company:</b></div>
Provided HR teams with clearer, more actionable turnover metrics to support targeted retention initiatives rather than reactive reporting.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Data Preprocessing & Target Engineering</b></h3></div>

Before developing the turnover prediction model, I transformed the raw HR snapshot data into a clean employee-level modeling dataset. Since the dataset contained monthly employee records and repeated snapshot updates, I first organized the data by employee ID and reporting period to reconstruct each employee’s employment timeline.

To improve data reliability, I removed records that appeared after an employee had already reached a terminal employment status, such as termination, retirement, or departure. I also handled retroactive updates by keeping the most recent snapshot for each employee and reporting period. This ensured that the model was trained on the latest and most accurate version of each employee record.

The prediction target was created by comparing each active employee’s current employment status with their next-period status. If an active employee remained active in the following period, the record was labeled as non-turnover. If the employee transitioned from active status to a non-active status, the record was labeled as turnover. This allowed the model to learn turnover risk as a forward-looking prediction problem rather than a simple historical reporting task.

Key preprocessing steps included:

- Cleaned and organized monthly HR snapshot data by employee and reporting period
- Removed records after terminal employment status to avoid post-separation noise
- Kept the latest available snapshot for each employee-period pair
- Created a next-period employment status variable
- Filtered the modeling dataset to active employees only
- Engineered a binary turnover target based on future employment status
- Selected demographic, employment type, role, department, tenure, and management-level features for prediction

<div><b>Value to the company:</b></div>

This preprocessing process converted complex HR snapshot data into a reliable prediction-ready dataset. By structuring the data around employee timelines and future status changes, the model could support proactive retention planning instead of only summarizing past turnover.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Machine Learning–Based Turnover Prediction</b></h3></div>

Developed a machine learning model using an Explainable Boosting Machine (EBM) to predict employee turnover.

Focused on interpretability to answer both:

- Who is likely to leave?

- Why are they likely to leave?

<div><h4><b>Handling Class Imbalance</b></h4></div>

Employee turnover prediction was a highly imbalanced classification problem because only a small portion of employees left the company compared to the number of employees who stayed. If this imbalance was ignored, the model could achieve high overall accuracy by simply predicting that most employees would remain active, while failing to identify the smaller but more important group of employees at risk of leaving.

To address this issue, I used a stratified train-validation-test split so that the turnover ratio remained consistent across the training, validation, and test datasets. I also applied class weighting during model training by assigning a higher weight to turnover cases. This encouraged the model to pay more attention to the minority class and improved its usefulness for identifying potential turnover risks.

Rather than optimizing only for accuracy, I evaluated the model using metrics that are more appropriate for imbalanced classification, including precision, recall, F1-score, ROC-AUC, and PR-AUC. This helped assess whether the model could meaningfully distinguish employees with higher turnover risk from the broader active workforce.

<div><b>Value to the company:</b></div>

By accounting for class imbalance, the model became better aligned with the business objective of detecting relatively rare but important turnover risks. This made the prediction results more useful for HR teams seeking to prioritize early intervention and retention strategies.

<div><h4><b>Threshold Selection & Model Evaluation</b></h4></div>

Instead of relying on the default classification threshold, I evaluated different probability thresholds using the validation set. This was important because the goal of the project was not simply to maximize prediction accuracy, but to create a practical decision-support tool for HR teams.

A lower threshold may identify more potentially at-risk employees but can also increase false positives, while a higher threshold produces a more selective list of high-risk employees. I compared precision, recall, and F1-score across thresholds and selected a threshold that provided a practical balance for business use.

The final model was evaluated on the test set using multiple performance metrics, including ROC-AUC, PR-AUC, F1-score, confusion matrix, and classification report. I also used the Explainable Boosting Machine’s interpretability features to identify the most influential drivers of turnover risk.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/kpmg_auc.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/kpmg_metrics.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div><b>Value to the company:</b></div>

This evaluation approach helped translate model output into a more actionable HR decision-making process. Instead of only producing a turnover probability, the model supported a business-facing risk classification that could be adjusted based on how broadly or selectively HR wanted to identify at-risk employees.

<div><b>Value to the company:</b></div>

Enabled proactive identification of at-risk employees and supported early intervention strategies instead of relying on historical turnover patterns.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Prediction Output for Business Use</b></h3></div>

After training and evaluating the model, I applied it to the most recent active employee records to generate forward-looking turnover risk predictions. Each employee received a predicted turnover probability and a binary risk label based on the selected threshold.

The predicted results were then combined with the existing HR dataset so they could be used in dashboard reporting and workforce planning analysis. This allowed the project to move beyond descriptive analytics and provide a forward-looking view of potential employee turnover.

The prediction output was designed to support:

- Employee-level turnover risk scoring
- HR dashboard integration
- Identification of higher-risk employee groups
- Proactive retention planning
- Future workforce planning and capacity analysis

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/KPMG_Prediction1.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/KPMG_Prediction2.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div><b>Value to the company:</b></div>

The final prediction output helped HR teams move from historical turnover reporting to proactive workforce planning. By identifying employees or groups with elevated turnover risk, the company could better prioritize retention efforts and make more informed staffing decisions.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Key Takeaway</b></h3></div>

This project demonstrates my ability to translate complex HR snapshot data into a scalable analytics solution. I combined data preprocessing, target engineering, dashboard design, imbalanced classification, interpretable machine learning, and business-facing prediction outputs to support workforce planning and retention strategy.

Rather than building a model in isolation, I focused on connecting the full analytics pipeline from raw HR data to actionable business insights. The final solution enabled both historical turnover analysis and forward-looking employee risk prediction, helping HR teams make more proactive and data-driven decisions.
