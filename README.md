This repository includes the final project submission for Georgetown University's PPOL5205 – Data Science III: Advanced Modeling Techniques, Fall 2024.

<h1 align="center">Criminal Sentencing Delay Analysis</h1>
<h3 align="center">A Multi-Method Study of Cook County Cases During the COVID Era</h3>


<p align="center">
By Tian Tong | Instructor: Prof. NaLette Brodnax  
</p>


---

<!-- ABSTRACT -->
<h2 id="abstract">Abstract</h2>

<p>
This project investigates the relationship between arrest delay and sentencing severity using court data from Cook County (2020–2024). Motivated by prior research on perceptual justice and judicial discretion, we conduct a multi-method analysis of approximately 42,000 criminal cases.
<p>

<p>
We employ Ordinary Least Squares (OLS) regression to estimate the marginal effects of arrest delay, Bi-Secting K-Means clustering to identify latent case profiles, and Random Forest classification to evaluate the predictive salience of key features. Findings indicate that longer delays are modestly associated with harsher sentencing outcomes, particularly in cases involving violent offenses and sexual exploitation-related charges.
</p>

<p>
A public-facing website presentation for this project is available at:  
<a href="https://yt5831.wixsite.com/my-site-2">https://yt5831.wixsite.com/my-site-2</a>
</p>

---

<!-- METHODOLOGY -->
<h2 id="methodology-summary">Methodology Summary</h2>

<p>
This study employs a combined supervised learning and exploratory data analysis approach to examine sentencing outcomes in Cook County between 2020 and 2024. The analytic pipeline consists of the following components:
</p>

<ul>
  <li><strong>Data:</strong> Administrative records from Cook County’s sentencing data, comprising approximately 42,000 criminal cases. A focal subset of 9,111 cases involving delayed arrests (defined by a measurable gap between incident and arrest dates) was isolated for targeted analysis.</li>

  <li><strong>Outcome Variable:</strong> A composite sentencing severity index, constructed by multiplying sentence length (in months) by the statutory severity level of the offense.</li>

  <li><strong>Methods:</strong> 
    <ul>
      <li>Ordinary Least Squares (OLS) regression with fixed effects to estimate the marginal effect of arrest delay on sentencing severity while controlling for observable covariates and temporal heterogeneity.</li>
      <li>Bi-Secting K-Means clustering to explore latent typologies among delayed-arrest cases based on case complexity and demographic characteristics.</li>
      <li>Random Forest classification to model sentencing outcomes and assess the relative predictive power of key covariates through feature importance metrics.</li>
    </ul>
  </li>

  <li><strong>Key Covariates:</strong>
    <ul>
      <li>Arrest delay (days between incident and arrest)</li>
      <li>Case duration and number of charges filed</li>
      <li>Case complexity, operationalized as an interaction between case duration and charge count</li>
      <li>Defendant demographics: age at incident, race, and gender</li>
      <li>COVID-19 period indicators, classified as pre-pandemic, peak disruption, and post-peak recovery phases</li>
      <li>Offense type, aggregated into six broad categories (e.g., violent offenses, property crimes, and exploitation-related charges)</li>
    </ul>
  </li>

  <li><strong>Model Interpretation:</strong> Predictor salience and explanatory contribution were evaluated using feature importance rankings derived from the Random Forest model.</li>
</ul>

<p>
For complete methodological details and empirical results, please refer to the final report:  
<code>Insight_report_yt583.pdf</code>
</p>


---

<!-- OBJECTIVES -->
<h2 id="objectives">Objectives</h2>
This study aims to extend existing literature on perceptual justice by analyzing real-world sentencing outcomes during a period of systemic disruption. Specifically, we pursue the following objectives:

<ul>
  <li>Quantify the relationship between time delays (from incident to arrest) and sentencing severity using case-level data from Cook County (2020–2024).</li>
  <li>Examine temporal and demographic variation in sentencing outcomes across three pandemic phases: Pre-COVID, Peak-COVID, and Post-COVID.</li>
  <li>Identify latent profiles of criminal cases through Bi-Secting K-Means clustering, revealing how case complexity, crime type, and delay dynamics shape sentencing patterns.</li>
  <li>Evaluate the relative importance of temporal, demographic, and case-specific predictors using Random Forest classification with comprehensive hyperparameter tuning.</li>
  <li>Generate empirical insights to inform sentencing reform and improve judicial responsiveness during systemic crises.</li>
</ul>

---

<!-- DATASET -->
<h2 id="dataset">Dataset</h2>

<p>
This project uses case-level data from the Cook County Data Portal, accessible via the  
<a href="https://datacatalog.cookcountyil.gov/Legal-Judicial/Sentencing/tg8v-tm6u/about_data">Cook County Sentencing Dataset</a>.
</p>

<p>
The full dataset comprises felony-level prosecutions initiated in Cook County and is maintained by the State’s Attorney’s Office. For this project, we used the version of the dataset available as of late 2024, prior to the January 3, 2025 update. Our analytic sample includes approximately 42,000 cases recorded between January 2020 and October 2024. A focal subset of 9,111 cases involving non-immediate arrests (i.e., a delay between the date of the offense and the arrest) was extracted for primary analysis.
</p>

<p>
The cleaned and filtered dataset used in our analysis—<code>cook_county_filtered_2020_2024.csv</code>—is included in this repository and can be accessed for replication and further exploration.
</p>


---

<!-- PREREQUISITES -->
<h2 id="prerequisites">Prerequisites</h2>

<p>
This project is written in the Python programming language and requires the following packages:<br>
<code>pandas</code>, <code>numpy</code>, <code>matplotlib</code>, <code>seaborn</code>, <code>scikit-learn</code>, <code>requests</code>
</p>

<p>
These can be installed using <code>pip install</code> or your preferred environment manager:
</p>

<pre><code>pip install pandas numpy matplotlib seaborn scikit-learn requests</code></pre>

---

<!-- Repository Structure -->
<h2 id="project-files">Repository Structure</h2>

<p>
This repository contains datasets, scripts, model outputs, and documentation for an individual final project analyzing sentencing delays in Cook County criminal cases. The analysis incorporates regression, clustering, and machine learning techniques to explore the effects of arrest delays on sentencing outcomes.
</p>

---

<h3>Data</h3>

### 📂 Data Files

| File Name                          | Description                                                                 |
|-----------------------------------|-----------------------------------------------------------------------------|
| `cook_county_2020_2024.csv`       | Raw sentencing-level dataset from the Cook County State’s Attorney’s Office, covering 2020–2024 |
| `cook_county_filtered_2020_2024.csv` | Cleaned and filtered version of the dataset used for analysis and modeling |


---

<h3>Script</h3>


| File Name                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| `Criminal_Sentencing_Analysis.ipynb` | Main notebook including preprocessing, regression modeling, clustering (Bi-Secting K-Means), Random Forest classification, and feature analysis |
| `Criminal_Sentencing_Analysis.html`  | Rendered HTML output of the notebook for easy viewing                      |

---

<h3>Output</h3>


| File Name                                         | Description                                                                                      |
|--------------------------------------------------|--------------------------------------------------------------------------------------------------|
| `Important_Features.png`                         | Ranked feature importance plot from the Random Forest model                                      |
| `Percentage_of_Delays_COVID.png`                 | Temporal analysis of delayed arrests across COVID-19 periods                                     |
| `Parallel_Coordinates_Plot_for_Clusters.png`     | Visualization of cluster-specific characteristics across multiple variables                     |
| `Silhouette_Scores_Bisecting.png`                | Silhouette score evaluation for Bi-Secting K-Means clustering                                    |
| `WCSS_Bisecting.png`                             | WCSS trend across different cluster numbers for Bi-Secting K-Means                               |
| `Silhouette_Scores_WCSS_Bisecting_Kmeans.png`    | Combined plot showing both WCSS and silhouette scores for cluster evaluation                     |


---

<h3>Documentation</h3>


| File Name             | Description                                                                                   |
|----------------------|-----------------------------------------------------------------------------------------------|
| `Insight_report.pdf` | Final written report summarizing the research question, methodology, results, and policy implications |


<!-- CONTRIBUTORS -->
<h2 id="contributors">Contributors</h2>

<p>
This replication study was completed as part of the final project for 
<strong>PPOL 5205 – Data Science III: Advanced Modeling Techniques</strong> (Fall 2024) at the 
<a href="https://mccourt.georgetown.edu/">Georgetown University McCourt School of Public Policy</a>.
</p>

<p>
We gratefully acknowledge the original authors for publicly sharing their data, which made this replication possible. We also extend our sincere thanks to Professor NaLette Brodnax for her invaluable guidance and support throughout the project.
</p>

<ul>
  <li><strong>Tian Tong</strong> – <a href="mailto:yt583@georgetown.edu">yt583@georgetown.edu</a></li>
</ul>

