# ENSO impact on river discharge in South America

This project was developed in the course of a bachelor thesis in media informatics at the University of Tübingen. 

The supervisor and corrector of this thesis is:
[Bedartha Goswami] &nbsp;    Machine Learning in climate sciecne, Excellence Cluster of Machine Learning, 

Bachelor student: 
[Markus Deppner] &nbsp; University of Tübingen, Department for Mediainformatics

This document is intended to provide additional explanation of the source code of the work.

The entire analysis was carried out in python and divided into four Jupyter notebooks: 

- DataInferring.ipynb
- GeneralAnalysis.ipynb
- Similarity Analysis.ipynb
- Maps.ipybn

The notebooks should be run in the above order. When reconstructing the whole process it is particularly important that DataInferring.ipynb is executed first, the order of the remaining three notebooks is not decisive and interchangeable. When only interested in recreating the results but not inferring the data itself, one can use the provided data in the repository to run the other notebooks.

In the following the notebooks are presented 

## DataInferring.ipynb
The purpose of this notebook is to extend the data set. First, those stations are determined that serve as the basis for the analysis by covering the entire period. We then filter those stations that start taking measurements at a later point in time, within our time period, or stations that stop taking measurements at a certain point in time and thus have missing data during our time period. The data is inferred by using Gaussian Process Regression and saved on the harddrive. 
The inferred data is stored in intermediate folders, and then loaded, merged and cleaned in a second step. The new dataset containing all inferred data is then saved as ds_gaussian.csv and ds_gaussian_clean.csv.

To run this notebook the [GPy library from the University of Sheffield][GPy] needs to be installed. 
To do so run the following command in the Juptyer Notebook 

```sh
pip install gpy
```

## GeneralAnalysis.ipynb
This notebook is for general analysis and contains some interesting plots that can be seen as an addition to the work. The last section of the notebook contains the RMSE analysis which was also described in the thesis. The sections above analyse the general distribution of the data, and analyses other featrues than the mean river discharge that has been analysed throught the whole work. 


## Similarity Analysis.ipynb
In order to group similar ENSO events together we ran a similarity analysis such that we can compute the Jaccard distance between events and group them based on their distance values. This analysis as well as the cross validation of those results are done in the SimilarityAnalysis notebook.

## Maps.ipybn
This notebook is about the interpolated data that was previously computed in DataInferring. It contains some additional maps of South America which could not all be included in the paper due to lack of space. Here you will find known plots in different dimensions, other features etc. 

 
 [//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [GPy]: <https://sheffieldml.github.io/GPy/>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [Bedartha Goswami]: <https://machineclimate.de/people/goswami/>
   [Markus Deppner]: <https://machineclimate.de/people/deppner/>
