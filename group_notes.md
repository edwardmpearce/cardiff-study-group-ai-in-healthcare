# AI and EO for the Prediction of Malaria Outbreak Risk

## Mark Pattle and Chandra Taposeea (isardSAT) 

---

#### Team Members

* Chandra Taposeea (isardSAT) chanda.taposeea@isardsat.co.uk
* Mark Pattle (isardSAT) mark.pattle@isardsat.co.uk
* Emma Southall (Warwick University) e.r.southall@warwick.ac.uk
* Edward Pearce (University of Sheffield) empearce1@sheffield.ac.uk
* Ann Smith (Cardiff University) smitha53@cardiff.ac.uk
* Víctor Gutiérrez-Basulto (Cardiff University) gutierrezbasultov@cardiff.ac.uk
* Federico Cerutti (Cardiff University) CeruttiF@cardiff.ac.uk
* Shelan Jeawak (Cardiff University) Jeawakss@cardiff.ac.uk
* Yazmin Ibanez-Garcia (Cardiff University) ibanezgarciay@cardiff.ac.uk
* Yuhua Li (Cardiff University) liy180@cardiff.ac.uk
* Steven Schockaert (Cardiff University) schockaerts1@cardiff.ac.uk
* David Pearson (PHE) sporadic.group@gmail.com

---

### Research Question to Address?

* How to detect precipitation through the waveform of radar altimetry?
* Can you characterise likelihood of standing water in villages with respect to waveforms?
* Would it be more of a mosquito habitat indicator?

---

### Task List

* How to address small number of malaria data points?
* How to best address how to process data - unsupervised vs supervised?
* How long to look at the data for? (length of time-series)
* Finding of more malaria cases?

### Resources

- Datasets: https://drive.google.com/drive/folders/1pl-ugfJkegmxa7vhbDmCZvTX9xdB5APc?usp=sharing
  - Note: Name typo for smos_i**m**hambane.csv, should be I**n**hambane..
  - Time in the waveform dataset is measured in International Atomic Time (TAI), but we want to convert this to UTC to compare with the precipitation dataset. Click [here](https://opensource.com/article/17/5/understanding-datetime-python-primer) for more information on different time formats.

- Problem presentation: https://drive.google.com/file/d/1bgm4YKh6wILdig5AgWBxk_3XGjJnxXx0/view?usp=sharing

#### Existing work

An R interface to open-access malaria data, hosted by the Malaria Atlas Project. https://github.com/malaria-atlas-project/malariaAtlas

Existing work on using machine learning for malaria outbreak prediction
* B. Modu et al. Towards a predictive analytics-based intelligent malaria outbreak warning system. Applied Sciences 2017 (https://www.mdpi.com/2076-3417/7/8/836)
* P Haddawy et al. Spatiotemporal Bayesian networks for malaria prediction. Artificial Intelligence in Medicine 2018 (https://reader.elsevier.com/reader/sd/pii/S0933365716305164?token=5C493D1401EAC0BCF3D6D3ECD0979268E4F68F6DDB2E041E9BC78B88CC152ABC9E63482D600CEF5C77C4029BCE2F2A12)
* M.O. Sewe et al. Using remote sensing environmental data to forecast malaria incidence at a rural district hospital in Western Kenya. Scientific Reports 2017 (https://www.nature.com/articles/s41598-017-02560-z.pdf)
* Sewe et al. Remotely Sensed Environmental Conditions and Malaria Mortality in Three Malaria Endemic Regions in Western Kenya. PLOS ONE. 2016 (https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0154204)

Existing work studying the relationship between malaria cases and potential drivers (rainfall, location and source of infection). This paper uses incidence case data from Bushbuckridge municipality:
* Silal et al. Exploring the seasonality of reported treated malaria cases in Mpumalanga, South Africa 2013 (https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0076640)
* Riedel et al. Geographical patterns and predictors of malaria risk in Zambia: Bayesian geostatistical modelling of the 2006 Zambia national malaria indicator survey (ZMIS), 2010
(https://malariajournal.biomedcentral.com/articles/10.1186/1475-2875-9-37)

Nasa Datasets:
* Mosquito Distribution Maps https://svs.gsfc.nasa.gov/vis/a000000/a002500/a002565/

* GLOBE Observer, an international citizen upload of land characteristics including Mosquito Habitat Mapper https://vis.globe.gov/mosquitohabitats

Using NASA Satellite Data to Predict Malaria Outbreaks Project

https://www.nasa.gov/feature/goddard/2017/using-nasa-satellite-data-to-predict-malaria-outbreaks

https://svs.gsfc.nasa.gov/12603

https://www.nasa.gov/sites/default/files/files/Malaria_Early_Warning_508.pdf

Outbreak data (past 3 months) inc. Malaria:
https://www.healthmap.org/en/

Nkomazi Muncipality 2013-2017 data
https://drive.google.com/open?id=1Z8yJOwV56UAT5Ut2eKZsPF7fNoQE9JbU

#### Information about Altimetry Waveforms

http://seom.esa.int/cryotraining2016/files/CTC16/Day3/1_Sorensen_Altimetry_theory_Louise.pdf

---

### Progress Against Tasks

---

### Next Steps