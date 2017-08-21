# sites_extractor_from_water-body

This package contains scripts to retrieve site IDs and other site information (locations where samples were collected) for water bodies (WB) from a state in the United States. 

It captures this WB to sites mapping in 6 csv files (<i>NHD-WQP Dataset</i>). These 6 tables hold the WB and their metadata, the bounding boxes and their metadata, the sites and their metadata, and the relationships among the WB, the bounding boxes, and the sites. It also captures things like the distance from a site to the edge of a WB, whether the site is inside or outside the WB etc.


The NHD (https://nhd.usgs.gov/NHD_High_Resolution.html) is digital geospatial dataset that maps the surface water of US. It represents the water drainage network of the US with features such as rivers, streams, canals, lakes, ponds, coastline, dams, and stream gages.
Details of water bodies in each state are obtained from NHD.

The Water Quality Data Portal (https://www.waterqualitydata.us/) provides an effortless way to access data stored in various large water quality databases. The site information is retrieved from here for each water body. 


## <i>NHD-WQP Dataset</i> ##

The 6 csv files generated in the dataset are: 

1. Waterbody - Table that stores details of each WB.
2. Bounding Box - Table that stores details about the bounding box - coordinates of each WB
3. Sites - Table that stores details of the sites (obtained from WQP)
4. W2B - Relation Table from Water Body to Bounding-Box
5. B2S - Relation Table from Bounding-Box to Sites
6. W2S - Relation Table from Water Body to Sites

## Usage Guide ##

To retrieve site information for water bodies in a state, following steps are to be done.

1. Obtain the water bodies (WB) data from NHD

The NHD High Resolution is available on the NHD web-site as a shapefile or file geodatabase. These can be downloaded by state. Here the scripts use them in shapefile format. Download shapefiles for water bodies of the state of interest from here and store locally in the path NHD_High_Resolution/NHD_state. 




2. Partition the WB data into smaller chunks

There are roughly about 100,000 water bodies that belong to each state. Obtaining the NHD-WQP Dataset for such a large dataset is a costly operation. Partitioning this large data into chunks (each chunk contains at most 1000 water bodies) eases the processing of it in later steps. For this, run the notebook <b>partitioning_wb_chunks_size_1000.ipynb</b>. This notebook partitions the WB data stored in the previous step into chunks of size at most 1000 and stores these data chunks locally in the path Partitioned/Partitioned-DFS-state.



3. Retrieve the dataset (6 tables) for WBs in the state

In this step run the notebooks download_data_state.ipynb and nhd_to_wqp_process10.ipynb. 

The notebook <b>download_data_state.ipynb</b> iterates through the folder containing the partitioned data chunks and passes as input, a list of 10 chunks file paths each time to the script nhd_to_wqp_process10.py internally.

The notebook <b>nhd_to_wqp_process10.ipynb</b> generates the <i>NHD-WQP Dataset</i> parallelly for the water bodies in those 10 chunks.


