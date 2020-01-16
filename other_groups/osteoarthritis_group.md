# Machine Learning for Improved Osteoarthritis Prediction

## Shameem Sampath (Knee Tracker) 
---

#### Team Members

* Shameem Sampath (Knee Tracker)
* Irena Spasic
* YoYo Zhou
* Clement Twumasi
* Andrey Pepelyshev
* Alex Balinsky

---


### Research Question to Address?

---

* Predict the effect of initial physical activities on outcome measures

### Task List

---

* T1: Selecting a subset of data
* T2: Selecting variables
* T3: Importing data into R
* T4: Explore methods including functional data analysis (FDA)

### Progress Against Tasks

---

* T1: years 0, 1, 3 and 6 because they had the force data unlike e.g. year 8
* T2: files selected: accelerometer, clinical, oscf, KOOS
* T2: redundant data removed
* T3: data imported
* T2: dependant variables identified based on clinical expertise
* T2: estimated correlations and significance of relationships among all remaining variables
* T2: visualised these relationships
* T4: PART method chosen to analyse the data. This choice was made because of the interpretability of the output - decision tree, which can be checked against clinical expectations.
* T4: Decision trees analysed manually to assess the relevance of the variables to the result also in an attempt to reduce the error.
* All of the above was done in multiple iterations.
* T4: FDA was conducted to visualise outcome variables over time including their convergence.

The initial results suggest that: 

* H1: Patient status changes rapidly reaching a plato at around 2.5 years into the study.
* H2: The plato lasts around 3 months. 
* H3: Further rapid change occurs after the plato. 
* H4: This is consistent with clinical findings. However, to the best of our knowledge, these findings have so far not been formally substantiated by data-driven mathematical models. 


### Next Steps

* S1: Publish the results of the pilot study.
* S2: Refine the idea further into a large-scale study into predictors of OA and design an appropriate intervention.
* S3: Assemble a team that involves representatives from healthcare, industry and academia.
* S4: Define a project proposal around the idea specified in S2.