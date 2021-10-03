# ENSO impact on river discharge in South America

This project was developed in the course of a bachelor thesis in media informatics at the University of Tübingen. 

The supervisor and corrector of this thesis is:
[Bedartha Goswami] &nbsp;    Machine Learning in climate sciecne, Excellence Cluster of Machine Learning,  

Bachelor student: 
[Markus Deppner] &nbsp; University of Tübingen, Department for Mediainformatics

This document is intended to provide additional explanation of the source code of the work.

The entire analysis was carried out in python and is divided into four Jupyter notebooks: 

- DataInferring.ipynb
- GeneralAnalysis.ipynb
- Similarity Analysis.ipynb
- Maps.ipybn

In the following the notebooks are presented 

## DataInferring.ipynb
The purpose of this notebook is to extend the dataset. First, the stations are determined that cover the entire time span and thus form the basis of the analysis. These are the stations that are used for Spearman's correlation and subsequently for training the Gaussian processes.
We then filter those stations that start taking measurements at a later point in time, within our time period, or stations that stop taking measurements at a certain point in time and thus have missing data during our time period. 
For each of these stations, an individual Gaussian Process is trained and then stored on the hard disk. The folder structure for a successful execution of the data generation is already given by the repository.

In the following step, the previously generated data is loaded from the intermediate folders on the hard drive, are merged and stored again as a compact data set with the name ds_gaussian.csv. 
For time series for which we could not inferr data successfully, we save an error frame for the given station on the hard drive. In a later step we drop all those error frames such that we remain only with those stations for which we could successfully estimate missing data. This dataset is called ds_gaussian_clean.csv.

To run this notebook the [GPy library from the University of Sheffield][GPyGit] needs to be installed. 
To do so run the following command in the Juptyer Notebook 
```sh
pip install gpy
```
or look for further information about the installation and usage of GPy on [their homepage][GPyHome]


## GeneralAnalysis.ipynb
This notebook is for a general analysis of the data and contains some additional plots that could not all be included in the work. The plots give insight to the temporal distribution of the dataset. Furthermore some additional features provided by the GSIM, like the absolute daily maximum streamflow or the maximum 7-day mean streamflow etc. are highlighted in this notebook.  
The last section of the notebook contains the RMSE analysis per dimension, mentioned in the thesis. Beforehand we ran the same code for dimensions ranging from 2 - 200, to narrow it down and further analysed the RMSE values from 5 to 15 as we chose a dimensionality of 10 for this work.
Warning: Running the cell of the RMSE analysis might take some time (roughly one hour per dimension).

## Similarity Analysis.ipynb
In order to cluster ENSO events we undertook a similarity analysis of the impact patterns of the individuel events. The Jaccard distance between the set of stations affected during the ENSO event were used a distance measure for hierarchical clustering in a later step. This analysis as well as the cross validation of those results are done in the SimilarityAnalysis notebook.

## Maps.ipybn

This document generates the impact maps of the different ENSO events and illustrates again the difference between the original data from the GSIM dataset and the extended dataset with the previously inferred data. It contains some additional impact maps of South America during ENSO events and group of ENSO events which could not all be included in the paper due to a lack of space. 
The function
```sh
plotStations(stations_inf, stations_raw, label_inf, label_raw, color_inf , color_raw, save=False, nameOfFigure="")
```
is rendering the plots, for given stations and labels. The parameter save enables or disables the function to save the rendered plot on the hard drive. The parameter nameOfFigure is the fileName of the figure saved on the hard drive. In the case of saving plots an additional folder needs to be created on the level where the jupyter notebooks are saved with the name 'plots'.
Or the path in the function needs to be changed.

 
 [//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [GPyHome]: <https://sheffieldml.github.io/GPy/>
   [GPyGit]: <https://github.com/SheffieldML/GPy>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [Bedartha Goswami]: <https://machineclimate.de/people/goswami/>
   [Markus Deppner]: <https://machineclimate.de/people/deppner/>