# nhd_to_wqp
Retrieving site IDs data from Water Quality Data Portal of water bodies in NHD state by state 

Shapefiles for water bodies are available in NHD (https://nhd.usgs.gov/data.html) and are accessible by state. There are roughly about 100,000 water bodies in each state. Partitioning this large data into chunks eases the processing of it.
Shapefiles of states of interest are downloaded from here and are stored in the path NHD_High_Resolution/NHD_state locally. 
<b>partitioning_wb_chunks_size_1000.ipynb</b> partitions water bodies of a given state of interest into chunks of size at most 1000. 


