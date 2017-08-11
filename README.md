# nhd_to_wqp
Retrieving site IDs data from Water Quality Data Portal for water bodies in NHD state by state 

Shapefiles for water bodies are available in NHD (https://nhd.usgs.gov/data.html) and are accessible by state. <br>
There are roughly about 100,000 water bodies in each state. Partitioning this large data into chunks eases the processing of it.
Shapefiles of states of interest are downloaded from here and are stored in the path NHD_High_Resolution/NHD_state locally. 

<b>partitioning_wb_chunks_size_1000.ipynb</b> partitions water bodies of a given state of interest into chunks of size at most 1000.<br> 
<b>nhd_to_wqp_process10.ipynb</b> forms the dataset of 6 csv files for 10 chunks for a given state after querying the WQP<br>
<b>download_data_state.ipynb</b> forms the 6 csv files dataset for a given state.<br>

The 6 csv files generated in the dataset are:
<br>
1. WaterBody - Table that stores details of Water Body<br>
2. BoundingBox - Table that stores details about the bounding box<br>
3. W2B - Relation Table from Water Body to Bounding-Box<br>
4. B2S - Relation Table from Bounding-Box to Sites<br>
5. W2S - Relation Table from Water Body to Sites<br>
6. Sites - Table that stores details of the Sites

