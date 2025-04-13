<h1 align="center">Criminal Sentencing Delay Analysis</h1>
<h3 align="center">A Multi-Method Study of Cook County Cases During the COVID Era</h3>

<p align="center">
Final Project for PPOL 5205 – Data Science III: Advanced Modeling Techniques  
<br>
Instructor: Prof. NaLette Brodnax  
<br>
Author: Tian Tong  
</p>
---

<!-- ABSTRACT -->
<h2 id="abstract">Abstract</h2>

<p>
This project investigates how time delays between crime and arrest affect the severity of criminal sentencing, using court data from Cook County (2020–2024). Motivated by prior literature on perceptual justice and judicial fairness, we conduct a multi-method analysis on nearly 42,000 criminal cases.
</p>

<p>
We apply OLS regression, Bi-Secting K-Means clustering, and Random Forest classification to assess the relationship between delay and sentence length, uncover latent case profiles, and rank key predictive features. Results suggest that longer delays are modestly associated with harsher sentencing, particularly for violent and sexual exploitation-related cases.
</p>

<p>
A public-facing website presentation for this project is available at:  
<a href="https://yt5831.wixsite.com/my-site-2">https://yt5831.wixsite.com/my-site-2</a>
</p>

---

<!-- METHODOLOGY -->
<h2 id="methodology-summary">Methodology Summary</h2>

<p>
We designed a supervised learning and exploratory pipeline with the following components:
</p>

<ul>
  <li><strong>Data:</strong> Cook County Sentencing Data (2020–2024), filtered to ~42,000 cases with an emphasis on 9,111 delayed-arrest cases</li>
  <li><strong>Targets:</strong> Composite sentencing severity, measured as Sentence Months × Severity Level</li>
  <li><strong>Methods:</strong> OLS regression with fixed effects, Bi-Secting K-Means clustering, Random Forest classification</li>
  <li><strong>Key Features:</strong> 
    <ul>
      <li>Delay in days (between incident and arrest)</li>
      <li>Case duration and number of charges filed per case</li>
      <li>Case complexity, operationalized as the interaction between case duration and number of charges</li>
      <li>Age at incident, race, gender</li>
      <li>COVID-19 period classification, categorized into pre-pandemic, peak-disruption, and post-peak phases</li>
      <li>Offense type, consolidated into six high-level categories (e.g., violent crime, property-related offenses, and exploitation-related charges)</li>
    </ul>
  </li>
  <li><strong>Interpretation:</strong> Predictor influence was assessed through feature importance rankings from the Random Forest model.</li>

</ul>

<p>
For implementation details, see the final project report:  
<code>Insight_report_yt583.pdf</code>
</p>

---

<!-- OBJECTIVES -->
<h2 id="objectives">Objectives</h2>

<ul>
  <li>Assess the relationship between arrest delay and sentencing severity using case-level court data</li>
  <li>Examine temporal and demographic variation in sentencing outcomes during the COVID-19 period</li>
  <li>Identify latent case groupings through Bi-Secting K-Means clustering to uncover underlying sentencing patterns</li>
  <li>Evaluate the relative importance of predictors using Random Forest classification</li>
  <li>Generate data-driven insights to inform judicial policy and sentencing reform efforts</li>
</ul>

---

<!-- DATASET -->
<h2 id="dataset">Dataset</h2>

<p>
This project uses case-level data from the Cook County Data Portal, available at:  
<a href="https://datacatalog.cookcountyil.gov/Legal-Judicial/Sentencing/tg8v-tm6u/about_data">Cook County Sentencing Dataset</a>.
</p>

<p>
The full dataset comprises felony-level prosecutions initiated in Cook County and is regularly updated by the State’s Attorney’s Office. For this analysis, we used the version of the dataset available as of late 2024, prior to the January 3, 2025 update. Our working sample includes approximately 42,000 cases recorded between January 2020 and late 2024, with a subset of 9,111 cases involving a delay between the date of the offense and the date of arrest. This filtered subset formed the basis for our primary analysis on sentencing delay effects.
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

<ul>
  <li><code>cook_county_2020_2024.csv</code> – Raw sentencing-level dataset from the Cook County State’s Attorney’s Office, covering 2020–2024</li>
  <li><code>cook_county_filtered_2020_2024.csv</code> – Cleaned and filtered version of the dataset used for analysis and modeling</li>
</ul>

---

<h3>Script</h3>

<ul>
  <li><code>Criminal_Sentencing_Analysis.ipynb</code> – Main notebook including preprocessing, regression modeling, clustering (Bi-Secting K-Means), Random Forest classification, and feature analysis</li>
  <li><code>Criminal_Sentencing_Analysis.html</code> – Rendered HTML output of the notebook for easy viewing</li>
</ul>

---

<h3>Output</h3>

<ul>
  <li><code>Important_Features.png</code> – Ranked feature importance plot from Random Forest model</li>
  <li><code>Percentage_of_Delays_COVID.png</code> – Temporal analysis of delayed arrests across COVID-19 periods</li>
  <li><code>Parallel_Coordinates_Plot_for_Clusters.png</code> – Visualization of cluster-specific characteristics across multiple variables</li>
  <li><code>Silhouette_Scores_Bisecting.png</code> – Silhouette score evaluation for Bi-Secting K-Means clustering</li>
  <li><code>WCSS_Bisecting.png</code> – WCSS trend across cluster numbers for Bi-Secting K-Means</li>
  <li><code>Silhouette_Scores_WCSS_Bisecting_Kmeans.png</code> – Combined plot of WCSS and silhouette scores for Bi-Secting K-Means cluster evaluation</li>


</ul>

---

<h3>Documentation</h3>

<ul>
  <li><code>Insight_report.pdf</code> – Final written report summarizing the research question, methodology, results, and policy implications</li>
</ul>
