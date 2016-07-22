IOT/MICROSTATS
At a certain level of data production, devices both passively scan swaths of the earth, like drones and satellites, and also generate data which we will increasingly need to process, geocode, and coalate in real time. Image analsysis and feature extraction will become increasingly important, as the kind of integrity and detail we glean from images is so much more thorough than collections of geocoordinates for the plotting


TOOLS

* TensorFlow (""which can crudely be accurately described as a raster-to-semantic-vector converter"")
* AWS 
* Hadoop / Hive / Presto / 
* Spark OS - not particularly useful by default for geo, but can be extended with GeoTrellis and other utilities that will like evolve.
* R + Python for analysis
* Tableau + Stamen
* PostgreSQL/PostGIS
* Mapnik
* CartoDB
* OpenLayers
* ArcGIS / QGIS 
* TatukGIS
* Satellite Data: PostGIS, GDAL, OpenCV and Numpy
* Kubernetes is an open source container cluster manager originally designed by Google and donated to the Cloud Native Computing Foundation. It aims to provide a "platform for automating deployment, scaling, and operations of application containers across clusters of hosts"
* GeoTrellis for raster,  provides geospatial capabilities to Scala and the Apache Spark framework
	* Raster: Spark, Hadoop, Accumulo, Amazon Web Services features like S3 and EC2
* Magellen is an option for vector but overlooking topological problems and onley doing points stuff
* GeoServer/Networ, OL, LeafLet, OpenGIS, PostGIS, Oracle + Geo cartridge, JSTS
* City/Govt: Google Fusion Tables + Google Maps + Windows OS

TECHNIQUES

* Inverse Distance Weighting - interpolate for areas with few samples (IDW)
* PostGIS function extension
* Geohashing
* OGC = Open Geospatial Consortium
* TINs are vector-based models depicting three-dimensional elevation surface terrains. Using three dimensional coordinates (x, y and z), TINs connect vertices and form non-overlapping planar triangles.

**Boris Shimanovsky, Factual**

IOT/SAT/MICROSTAT

"It will also create more uncharted territory where security, privacy laws, and tools to understand the data will lag behind."

EVOLUTION FROM SMALL BEGINNINGS

"Several of our core products started as a hackathon project.  One of my hackathon projects evolved to process billions of geo annotations every day."


**Tyler Bell, Factual (referred by DJ Patil), now Mapbox**

"The problems really boil down coverage, quality, and creation: how we analyze global coverage and quality to prioritize engineering and BD energies; how we develop software that better joins human- and machine-based efforts to correct and protect the map; and how we work with sensor and probe data to enhance the and update the map in real-time.
"

TOOLS
"This is a gross and certianly unfair categorization [between non-spatial and spatial data organizations], of course, but frames my answer: **the geohash (https://en.wikipedia.org/wiki/Geohash)** is the most powerful tool of the non-spatial companies, while the purely spatial camp can benefit hugely from Mapbox's tile-reduce libraries (https://github.com/mapbox/tile-reduce).  **From a purely GIS-POV I remain blown-away by the capabilities of PostGIS, and never touch a GUI where I don't have to (but when I do it is always QGIS)**."

IOT/SAT/MICROSTAT
""**All of these devices are capturing data and annotating it geographically, or capturing geo data and annotating it contextually;  In one sense these are all 'maps that move', but really their availability is both enriching the quality and multiplying the breadth sensor coverage.**""

EVOLUTION
**"Open data is the big wave though: we have OSM for the map, and OpenAddress for addresses (and AU is the latest country to relaize the power of open, geocoded addresses: https://blog.data.gov.au/news-media/blog/geocoded-national-address-data-be-made-openly-available  POI data is likely to be that last to fall, for a number of differnt reasons."**

**Riley Newcomb, Airbnb**

ANALYTICS
"the phenomena surrounding and complicating what is interestin gabout eodata naturally draws us to want more processing power, the ability to aggregate and compare more disparate datasets, the ability to inform one mapped trend with another...."it’s at the heart of the information revolution underway.""

**Stefan Avesand, Ericsson Smartphone Labs**
OPENDATA
"
The most **important contribution needed from these parties is open data**. This involves basic data such as administrative levels to all particular domains managed by the government, e.g. transport, demographical and environmental data."

**Robin Kraft, Space.Ninja and GlobalForestWatch.org**

OPEN DATA
"ESRI is the Microsoft of the geospatial world, for better or for worse, and it’s very expensive stuff. You can do a lot of great stuff with OSS, and gov’t agencies should be more open to that.
"

