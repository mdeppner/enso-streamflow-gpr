*********************************************************************************************************
** The Global Streamflow Indices and Metadata Archive (GSIM)
*********************************************************************************************************
** Part 1: The production of daily streamflow archive and metadata
** Author: Hong X. Do, 2017 (email: hong.do@adelaide.edu.au)
*********************************************************************************************************

*********************************************************************************************************
** (1) Introduction **
*********************************************************************************************************

This file provide descriptions for data accompanying following paper:

Do, H.; Gudmundsson, L.; Leonard, M.; Westra, S.; Senevirante, S.I (2017): The Global Streamflow Indices 
and Metadata Archive (GSIM) - Part 1: The production of daily streamflow archive and metadata; 
submitted to Earth System Sciences Data.

Please refer to the paper for details on data sources, methods and algorithms

*********************************************************************************************************
** (2) Content **
*********************************************************************************************************
** (2.1) Folder "GSIM_catalogue"
**

There are three files within this folder that contain information associated to each streamgauges that is 
available in GSIM archive.

(a) GSIM_catalogue/GSIM_metadata.csv
(b) GSIM_catalogue/GSIM_catchment_characteristics.csv
(c) GSIM_catalogue/GSIM_suspect_coordinates_stations.csv

** (a) GSIM_metadata.csv**
*PURPOSE:
This file provides three sets of information: (1) metadata obtained from original data sources; 
(2) information on linking original data bases; and (3) a set of metrics extracted from the time series 
representing data availablity.

*STRUCTURE:
The file was organised as a table with 30,959 rows (header excluded) and 27 columns. 

*MISSING VALUE:
"NA" character was used to represent missing value.

*FIELD DEFINITION:
(1) gsim.no                     :GSIM station id
(2) reference.db                :indicate database of original time series 
(3) reference.no                :station id of the reference database
(4) grdc.merge                  :indicate whether the de-duplication process was involved ('yes' value) 
                                 or not ('no' value)
(5) grdc.no                     :number of GRDC station (if available)
(6) paired.db                   :database of duplication station (if applicable)
(7) paired.db.no                :station id of duplication station (if applicable)
(8) river                       :river name 
(9) station                     :station name 
(10)country                     :2-letter country code (ISO 3166)
(11)latitude                    :reported latitude of station (decimal degree) 
(12)longitude                   :reported longitude of station (decimal degree)
(13)altitude                    :height of gauge (m) above sea level (if available)
(14)area                        :catchment size reported from data sources (if available) in km2
(15)unit                        :unit of time series - in m3/s
(16)river.dist                  :string distance between "river" metadata of time series 
                                 (if de-duplication process was used)
(17)station.dist                :string distance between "station" metadata of time series 
                                 (if de-duplication process was used)
(18)latlon.dist                 :geodistance (km) estimated from coordinates of time series 
                                 (if de-duplication process was used)
(19)bin.latlon.dist             :binary 0/1 determined by comparing latlon.dist with 5km cut-off value 
                                 (if de-duplication process was used)
(20)mean.dist                   :mean value of item (16), (17) and (19) 
                                 (if de-duplication process was used)
(21)number.overlap              :number of overlap days between two time series 
                                 (if de-duplication process was used)
(22)number.available.days       :number of available data point (daily) of GSIM time series 
(23)number.missing.days         :number of missing value of GSIM time series 
(24)frac.missing.days           :fraction of missing value = (24)/[(24)+(23)]
(25)year.start                  :year of the first available datapoint
(26)year.end                    :year of the final available datapoint
(27)year.no                     :length of time series (year) = (27) - (26) + 1


** (b) GSIM_catchment_characteristics.csv** 
* PURPOSE:
This file provides two set of information: (1) quality of delienated catchment boundary; and (2) catchment 
characteristics extracted from global data-products .

* STRUCTURE:
These information was organised as a table of 30,959 rows (header excluded) and 84 columns. 

* MISSING VALUE:
"NA" character was used to represent missing value.

* FIELD DEFINITION:
(1) gsim.no                     :GSIM station id
(2) long.org                    :reported longitude of station
(3) lat.org                     :reported latitude of station
(4) long.new                    :longitude of 'best outlet' location that was used to delineate 
                                 catchment boundary
(5) lat.new                     :latitude of 'best outlet' location that was used to delineate 
                                 catchment boundary
(6) dist.km                     :distance between 'best outlet' location (fields 4 and 5) and location 
                                 reported in original metadata (fields 2 and 3)
(7) area.meta                   :catchment size information from metadata in km2 (if available)
(8) area.est                    :catchment size estimated from boundary shapefile in km2 (if available)
(9) quality                     :quality flag of catchment boundary (identify from field 7 and 8),
                                 please refer to original paper for more information
(10)altitude.meta               :height of gauge above sea level (m) reported from metadata
(11)altitude.dem                :altitude of original gauge location (m) extracted from DEM products
(12)climate.type                :catchment climate (major groups of Koppen-Geiger system) if one Climate
                                 type present over more than 50% catchment area, otherwise 'No dominant
                                 class' value was assigned
(13)no.dams                     :number of dams presents within the catchment boundary
(14)sto.volume                  :total storage volumes for all dams presents within the catchment boundary
(15-20)dr. metrics              :average (dr.mean), minimum (dr.min), first quartile (dr.q1), second
                                 quartile (dr.q2), third quartile (dr.q3), and maximum (dr.max) values of
                                 catchment drainage density 
(21-26)ele. metrics             :average (ele.mean), minimum (ele.min), first quartile (ele.q1), second
                                 quartile (ele.q2), third quartile (ele.q3), and maximum (ele.max) values
                                 of catchment elevation
(27-32)ir. metrics              :average (ir.mean), minimum (ir.min), first quartile (ir.q1), second
                                 quartile (ir.q2), third quartile (ir.q3), and maximum (ir.max) values
                                 of catchment irrigation area
(33)landcover.type              :catchment land-cover (UN Classification System for 2015) if one single 
                                 land-cover type present over more than 50% catchment area, otherwise 
                                 'No dominant class' value was assigned
(34)lithology.type              :catchment lithology (16 classes by Dürr et al. [2005] (*)) if one single 
                                 lithology type present over more than 50% catchment area, otherwise 'No 
                                 dominant class' value was assigned
(35-40)nl. metrics              :average (nl.mean), minimum (nl.min), first quartile (nl.q1), second
                                 quartile (nl.q2), third quartile (nl.q3), and maximum (nl.max) values
                                 of Nightlight Development Index within catchment boundary
(41)pop.count                   :total population within catchment boundary (GPWv4 - 2010)
(42-47)pd. metrics              :average (pd.mean), minimum (pd.min), first quartile (pd.q1), second
                                 quartile (pd.q2), third quartile (pd.q3), and maximum (pd.max) values
                                 of population density within catchment boundary (GPWv4 - 2010)
(48-53)slp. metrics             :average (slp.mean), minimum (slp.min), first quartile (slp.q1), second
                                 quartile (slp.q2), third quartile (slp.q3), and maximum (slp.max) values
                                 of slope within catchment boundary
(54-59)sb. metrics              :average (sb.mean), minimum (sb.min), first quartile (sb.q1), second
                                 quartile (sb.q2), third quartile (sb.q3), and maximum (sb.max) values
                                 of bulk density in kg/cubic–meter within catchment boundary
(60-65)scl. metrics             :average (scl.mean), minimum (scl.min), first quartile (scl.q1), second
                                 quartile (scl.q2), third quartile (scl.q3), and maximum (scl.max) values
                                 of clay content in soil profile within catchment boundary
(66-71)snd. metrics             :average (snd.mean), minimum (snd.min), first quartile (snd.q1), second
                                 quartile (snd.q2), third quartile (snd.q3), and maximum (snd.max) values
                                 of sand content in soil profile within catchment boundary
(72-77)slt. metrics             :average (slt.mean), minimum (slt.min), first quartile (slt.q1), second
                                 quartile (slt.q2), third quartile (slt.q3), and maximum (slt.max) values
                                 of silt content in soil profile within catchment boundary
(78)soil.type                   :catchment soil class (WRB) if one single soil class present over more than
                                 50% catchment area, otherwise 'No dominant class' value was assigned
(79-84)tp. metrics              :average (tp.mean), minimum (tp.min), first quartile (tp.q1), second
                                 quartile (tp.q2), third quartile (tp.q3), and maximum (tp.max) values
                                 of topographic index within catchment boundary

** (c) GSIM_suspect_coordinates_stations.csv**
*PURPOSE:
This file is the subset of file GSIM metadata to provide information of 24 stations with "suspect coordinates"
and thus have been excluded from the catchment delineation procedure.

*STRUCTURE:
The file was organised as a table with 24 rows (header excluded) and 27 columns (with identical fields as 
in file "GSIM_metadata.csv"). 

*MISSING VALUE:
"NA" character was used to represent missing value.


** (2.2) Folder "GSIM_catchments"
**
* PURPOSE:
This folder contains catchment boundaries corresponding to 30,935 GSIM stations that have reasonable geographic coordinates. 

* STRUCTURE:
Each GSIM station is accompanied by a catchment boundary, GSIM station IDs were used to name the files.
Catchment outlines were produced with smoothed edges and delivered in ESRI shapefile format, and thus
each catchment is represented by four different files (same name with different in extensions):
(1) '.shp': provides geometry of the catchment polygon. 
(2) '.shx': provides shape index position.
(3) '.dbf': provides attribute table assoaciated to a specific catchment.
(4) '.prj': provides the metadata associated with the shapefiles coordinate and projection system

* ATTRIBUTE TABLE:
GSIM ID of gauge was attached as the attribute table for a specific catchment shapefile.

* SPATIAL REFERENCE INFORMATION
The latest version of Geographical Coordinates System of World Geodetic System (GCS_WGS_1984) was used.


(*) Dürr, H. H., M. Meybeck, and S. H. Dürr (2005), Lithologic composition of the Earth's continental surfaces 
derived from a new digital map emphasizing riverine material transfer, Global Biogeochem. Cycles, 19, GB4S10, 
doi:10.1029/2005GB002515.