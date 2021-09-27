****************************************************************************
** A compilation of global daily streamflow indices and metadata (G-SIM)
****************************************************************************
**
** Part 2: Time Series Indices and Homogeneity Assessment
**
** Author of this file: Lukas Gudmundsson
**
****************************************************************************

****************************************************************************
** (1) Introduction **
****************************************************************************

This is a readme file for data accompanying following paper:

Gudmundsson, L.; Do, H.; Leonard, M.; Westra, S.; Senevirante, S.I
(2017): The Global Streamflow Indices and Metadata Archive (GSIM) 
- Part 2: Quality Control, Time-series Indices and Homogeneity 
Assessment; submitted to Earth System Sciences Data.

please refer to the paper for details on data sources, methods and
algorithms 

****************************************************************************
** (2) Content **
****************************************************************************

**
** (2.1) Time series
**

The folders

TIMESERIES/yearly
TIMESERIES/seasonal
TIMESERIES/monthly

contain text files with time-series indices for yearly, seasonal and
monthly resolution. Each file corresponds to one station.  The file 
names are based on the station identifiers used in the GSIM collection
(gsim.no, see below) with an extension corresponding to the time resolution. 
Example: gsim.no: AR_0000006; yearly file "AR_0000006.year"; seasonal 
file "AR_0000006.seas"; monthly file: "AR_0000006.mon".

The files contain: 

** (a) **
A header for which each line starts with a hash character (#). The
header contains the following information on the station meta data:

gsim.no   : station number of the GSIM database.
river     : name of the river.
station   : name (or location) of station.
country   : the country.
latitude  : latitude in decimal degrees.
longitude : longitude in decimal degrees.
altitude  : altitude in meters.
area      : catchment area in metres.


** (b) ** 
Comma separated time series of the index values, with rows corresponding to individual
yearly, monthly or seasonal timesteps.


** The first column ("date") contains the date, which is by convention
   the *last day* of the respective yearly, seasonal or monthly 
   time-step. Date format: yyyy-mm-dd.

** The subsequent columns contain the index values, with column names
   corresponding to the abbreviations introduced in the above
   mentioned article. 

** The column "n.missing" contains the number of missing (and/or
   suspect) daily values for the respective time step.

** The column "n.available" contains the number of used (neither
   missing nor suspect) daily values.

Note that "n.missing" + "n.available" equals the total number days in
the respective yearly, seasonal or monthly time period (e.g. 365 or
366 (leap years) for yearly resolution.


**
** (2.2) Homogeneity information
**

The folder

HOMOGENEITY

contains three comma separated text files that contain information on
the homogeneity of all indices at each station for yearly, seasonal and
monthly resolution.

The first columns contain some meta-data:

gsim.no                : station number of the G-SIM data base.
river                  : name of the river.
station                : name (or location) of the station.
country                : the country.
latitude               : latitude in decimal degrees.
longitude              : longitude in decimal degrees.
altitude               : altitude in meters.
area                   : catchment area in meters.
first.time.step        : first yearly/seasonal/monthly time step with data.
last.time.step         : last yearly/seasonal/monthly time step with data.
total.time.steps       : total number of yearly/seasonal/monthly time steps.
number.good.time.steps : total number of yearly/seasonal/monthly time
                         steps that are classified as reliable (see paper).
frac.good.time.steps   : fraction of reliable time steps

The remaining columns contain the results of four homogeneity tests
that are descried in the paper. For a given INDEX the following options
are available: 

INDEX.SNHtest : standard normal homogeneity test 
INDEX.BHRtest : Buishand range test
INDEX.PETtest : Pettitt test 
INDEX.VONtest : Neumann ratio test

were INDEX is substituted with the abbreviation of each considered
index, yielding for the example of the Pettitt test being applied to the
minimum daily streamflow index: MIN.PETtest

For each homogeneity test the following six values are possible:

NS    : not significant, no inhomogeneity was detected.
p5    : inhomogeneity detected at the 5% confidence level.
p1    : inhomogeneity detected at the 1% confidence level.
NSD   : Not sufficient data for homogeneity testing (less than 20 data
        points with reliable index values) 
CONST : The values of all the time-steps with reliable index values are
        equal. 
ERROR : An unknown error occurred in the processing. 
