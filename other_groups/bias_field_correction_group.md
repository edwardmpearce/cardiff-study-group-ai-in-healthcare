# Better Bias-field Correction in MRI Through Machine Learning

## Ian Hardingham (Oxford Brain Diagnostics) 
---

#### Team Members

* Ian Hardingham (Oxford Brain Diagnostics)
* Andreas Artemiou (Cardiff University)
* Federico Cerutti (Cardiff University)
* Luke Smallman (Cardiff University)
* Sam Lawrence (University of Portsmouth)

---


### Research Question to Address?
Estimating bias field in structural MRI images

---

### Task List
1. Understand the nature of the data and come up with ideas.
2. Review state-of-the-art literature to make sure we ar enot re-inventing the wheel.
3. Try a couple of different ideas.

---

### Progress Against Tasks
1. Data

#### One-dimensional version:

![](https://i.imgur.com/W5zk1dI.jpg)

#### Data visualisation
[Jupyter notebook](https://drive.google.com/file/d/1WVP24Cq9fwdM3v43HtLaGra6oXF4mMtj/view?usp=sharing)

#### We started by measuring the variance of each voxel in the observed MRI signal.


$X(\textbf{x})=B(\textbf{x})f(\textbf{x})$

where $X(\textbf{x})$ is the observed MRI signal, $B(\textbf{x})$ is the bias field and $f(\textbf{x})$ is the true uncorrupted signal. The variance is then given by

$V(\textbf{x})=Var(B(\textbf{x})f(\textbf{x}))$
$=\mathbb{E}(B(\textbf{x}))^2Var(f(\textbf{x}))+\mathbb{E}(f(\textbf{x}))^2Var(B(\textbf{x}))+Var(B(\textbf{x}))Var(f(\textbf{x}))$

In areas of homogeneity $\textbf{x}\in\delta(\textbf{x}_0,r)$, differences between neighbouring voxels are small and so

$f(\textbf{x})\approxeq F$ (constant),
$\Rightarrow Var(f(\textbf{x}))\approxeq 0$,

Therefore,
$V(\textbf{x})=\mathbb{E}(f(\textbf{x}))^2Var(B(\textbf{x}))$

We created a visual representation of this field using a Python script to generate the values of $V(\textbf{x})$ for each vocel and then used FSLeyes to view it. 

To ensure that we considered only homogeneous regions of the image, we discounted all regions with a variance getter that some upper bound $b$.

2. Lit review

* Manjon et al. A nonparametric MRI inhomogeneity correction method. https://www.sciencedirect.com/science/article/pii/S1361841507000254
* Tustison et al. N4ITK: Improved N3 Bias Correction. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3071855/
* Sulaiman et al. Segmentation of brain MRI image based on clustering algorithm
https://ieeexplore.ieee.org/document/8049872
* Juntu et al. Bias Field Correction for MRI Images (DOI: 10.1007/3-540-32390-2_64)
* Ji et al. MR image segmentation and bias field estimation using coherent local and global intensity clustering (DOI: 10.1109/FSKD.2010.5569472)
* Belaroussi et al. Intensity non-uniformity correction in MRI: existing methods and their validation. https://www.ncbi.nlm.nih.gov/pubmed/16307900

**An alternative approach: measuring the intensity  percentiles**

We attempted to probe the bias field by taking a slice (2D plane) and asking where each voxel sat in its intensity distribution. Specifically we looked at the distribution of its intensity neighbourhood - what percentile was it in? 

Since the bias field seemed to peak from an area of the slice, could the percentile classification of each voxel give an indication of where this peak was?

The idea here, is that for each voxel we will run the following algorithm: 
* Take the value.
* Take the voxels that have similar values (within a range to be defined by the user i.e. 10%).
* Plot a histogram of the values in the voxel. 
* See what is the percentile of the point in comparison with the rest. 

**Explanation on why this may work**: We expect that points that are in higher percentiles will be the ones that are more likely to belong to areas where the bias field peaks, while points that are in lower percentiles will be in areas where the bias field is low. 

A histogram of the raw values look like this : 
![](https://i.imgur.com/Q4PYigL.png)

This is how the source image look like: 
![](https://i.imgur.com/3UeTmfv.png)

Thinally this is the bias field in this case: 
![](https://i.imgur.com/vLS2b9E.png)

Let's draw some percentiles.  Here is an image where we are ploting the brain using the percentiles for each voxel (whiter means higher percentile).
![](https://i.imgur.com/nv0nkme.png)

So one can see that the image roughly agrees with the bias-field (the whiter areas are in the same region).  There are though some areas which are grey in that region in the first image. We believe that these are the areas that there is a change to different matter and on the histogram are represented by the valleys. As a test we removed one valley as shown below: 
![](https://i.imgur.com/LlernSq.png)
and this is how the image of the brain when plotting the percentiles
![](https://i.imgur.com/se6Fcqs.png)
the gradient of the bias field now appears to be more visible.

The first "small" challenge we face after this is to try to address the black areas we cut out of the analysis.  To do this we decided to interpolate based on the values we already have. To achieve this through linear interpolation we need the distances between voxel to be correct.  The distances we have are only correct in physical space but not in voxel (array) space.  Therefore we worked on an affine transformation. 


The formula looks roughly like this: 
$$ \boldsymbol{A} \begin{bmatrix} \boldsymbol{x} \\ 1 \end{bmatrix} = \begin{bmatrix} \boldsymbol{p} \\ 1 \end{bmatrix}$$
where matrix $\boldsymbol{A}$ denotes the affine transformation, $\boldsymbol{x}$ denotes the voxel (array) coordinates) and $\boldsymbol{p}$ denotes the physical coordinates. 


**What is the bigger challenge**: We still need to estimate the actual bias field after this. As a first guess this could be something of the form... 

$$B(\textbf{x})=\lambda(\alpha+ I(\textbf{x})), $$
where $I(\textbf{x})$ is the intensity distribution field as given in the above image, $\lambda$ is a constant scaling factor and $\alpha$ is a additive constant.



---

### Next Steps
 * Finalize the transformation algorithm
 * Finalize how to actually best use these results in estimating the bias field. 