Historical Maps

* How to celebrate the Ordnance Survey anniversary making an old looking map
https://www.ordnancesurvey.co.uk/blog/2016/06/recreating-historic-maps-interview-with-christopher-wesson/

Meteomap - website exploring historical weather with Wikipedia data: https://github.com/simlmx/meteomap

Old weather and torque. 

A few years ago, CartoDB (now Carto) debuted a project in partnership with the citizen science, Zooniverse, called "Old Weather." The objective of the project was to leverage crowdsourcing for the transcription historical shipping log books to identify weather patterns. During this project, a need for respresenting time-series data on maps evolved into a javascript library called Torque.js. The moral of the OSStory is that often open data and citizen science beget additional open source developments and innovations in mapping, and often what pushes the boundaries of modern map development are the companies working on the bleeding edge of the open web. Boris Shimanofsky of Factual admits that "several of their core products started as a hackathon project...[o]ne of my hackathon projects evolved to process billions of geo annotations every day," increasingly short-sprint web projects build to handingly heavy geo-data on and off-line.



Small-Medium Quick Analysis

In a recent travel blog called "Glimpses of the Future," AUTHOR I, part of the humanitarian company BLAHBLAH created a list of things to know when traveling in the third world. Both technical and anecdotal, the list included a two-bullet interlude on maps including the following: 

* Maps.me is the closest thing to decent offline maps.
* The most interesting places have map coordinates, but no names.
https://medium.com/todays-office/6-1-glimpses-of-the-future-e3fdb510dcc1#.n1km6xdcn

Whether or not you are familiar with Maps.me, an online platform for making quick web-maps, the first bullet introduces the ever-complicating issue of making maps of the global world, when not every part of the world can effectly access or save your mapped projects with loading and connectivity limitations . The second bullet introduces another issue: that geodata despite best efforts, has feeble coverage in much of the world, and solutions to this latter issue must become increasingly creative or rely on commercial partners to patch the un-mapped portions of the world.

In this effort, it’s important to remember that though geospatial data formats might seem opaque, most geo-data is increasingly trending toward increased availability, open licensing and open platforms. The opportunities in open data are myriad; with Open Street Map providing a dynamic map canvas fueled by global community, and increasing support for open geocoders and the Open Addresses project, “point of interest (POI) data is likely to be that last to fall, for a number of different reasons.” 

The mechanics of map rendering in open street map historically involved a tile renderer called Mapnik, with an XML data configuration. Around 2013, Andy Allan's openstreetmap-carto displaced Mapnik as a default, and Mapbox's development of the Cascadenik toward a CartoCSS reference resource for webmaps made it quite possible to style and serve webmaps with open source tools. This brief bit of history provides a high-level gloss for how citizen cartography can flourish on the web via open data formats and OSS. And even still, desktop GIS companies like Esri maintain robust open data platforms and provide low-grade access to their subscription tools via developer, student and beginner accounts.

In section 2 we discussed the structure of a basic webmap, and presuming you’re working with basemaps, tiles, feature (or data) layers, and any languages to get that to render on the web, or tools to generate a high-fidelity print of your map project. For low to medium scale projects, you might be looking to satisfy the demands of both print and web so we’ll talk about now to negotiate that as well. Let’s start with some open data and see what kinds of maps can be made with the a few common tools for backend and frontend development.

DATA

Riley Newcomb, Airbnb
"SF’s OpenData project is a great example. Making data public can lead to all kinds of projects that benefit the community without requiring public resources. It lowers the barrier to entry for NGOs and crowdsources innovative solutions to public issues. The more of this we can do, the better."

**Stefan Avesand, Ericsson Smartphone Labs**
OPENDATA
"
The most **important contribution needed from these parties is open data**. This involves basic data such as administrative levels to all particular domains managed by the government, e.g. transport, demographical and environmental data."

More OSM Data (from slides)
You have several options for downloading
this ever-evolving data set.
the whole planet from Planet OSM. Set aside a week or more to download and import.
metro extracts
from Mapzen. These supersede those previously maintained by Michal Migurski. Updated weekly.
from Geofabrick GmbH. Updated daily.
from BBBike.org. Updated weekly.

a customizable area export from OpenStreetMap.

Mapzen offers hundreds of metro extracts, and you
can easily request that they add a new one.
Download the OSM PBF file for Portland (Oregon). 


Example: Point map - OSM point Data

Let’s take an example of some point data, and determine how best to map these data using some conventional open source tools. Say you have point data about OSM geological features.

**OUTCROPS IN OSM**

[Outcrops](http://wiki.openstreetmap.org/wiki/Tag:geological%3Doutcrop) are places where the bedrock or superficial deposits have become locally exposed and are directly accessible to analysis in OSM; let's map them!

![OSM Geo](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/osmgeo.jpg)

* OSM: Open StreetMap + [Overpass Turbo](http://overpass-turbo.eu/)

![Overpass](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/turbo.jpg)

You can read more about Overpass on the [Open Street Map Wiki](http://wiki.openstreetmap.org/wiki/Overpass_turbo).

Steps:
* Pan manually to an area in OverPass Turbo
* Go to the "Wizard"
* Look up the appropriate OSM tag in the OSM wiki
* Search for "geological=outcrop" or whatever
* Export your data as GeoJson or KML
* Upload into CartoDB or another interface

![outcrop search](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/outcrop.jpg)

OSM data has peculiarities in the schema that make the following considerations necessary as you build your map. Before extracting or deciding on data format, you might consider what entities to show, at what zoom level, and how your map design or style might highlight them. If extractions from overpass take too long, you might consider restricting nodes, ways or relations in the query, saving you processing time and power. Define or rather restrict your bounding box to search a dataset within the geographic realm you plan to map, as a default zoomed-out global view might cause overpass to crash.

![Turbo Output Interface](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/output.jpg)

Beyond overpass there are other OSM formats

#### Part 0: Outcrops

![Outcrop Data](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/outcrop-data.jpg)

So let's take a look at this outcrop data. You want to lead people to all of the outcrop stations globally. You can use the kml file [here in the data folder](https://github.com/auremoser/ipam-16/blob/master/data/outcrop.kml).

You can get the libraries from OSM or NYC Open Data but let's go with the KML from OSM that we extracted with OverPass.

`.kml` which is a notation for XML that first made popular by Google Earth before becoming standardized. Google Mapping Products happily use kml files. Check to see how the locations are described:

``` xml
<?xml version="1.0" encoding="UTF-8"?><kml xmlns="http://www.opengis.net/kml/2.2"><Document><name>overpass-turbo.eu export</name><description>Filtered OSM data converted to KML by overpass turbo.
Copyright: The data included in this document is from www.openstreetmap.org. The data is made available under ODbL.
Timestamp: 2015-09-14T14:05:02Z</description><Placemark><name>Sonnberg</name><Point><coordinates>9.43865,50.6228007</coordinates></Point><ExtendedData><Data name="@id"><value>node/428215780</value></Data><Data name="geological"><value>outcrop</value></Data><Data name="name"><value>Sonnberg</value></Data><Data name="note"><value>Rocky promontory, subject to erosion. Middle Triassic shallow marine limestone, Jena Formation (U.-Muschelkalk, Wellenkalk). Small outcrop within E-W trending graben structure. Contact to MIttlerer Buntsandstein exposed in river bed southwest of crag.</value></Data></ExtendedData></Placemark><Placemark><name>Monkey rock</name><Point><coordinates>177.127952,-17.7323069</coordinates></Point>
...
```

Notice that the point coordinates are in the format `<coordinates>`longitude, latitude`</coordinates>`. Some geoformats are lat, long and others are long, lat. This makes everyone sad.

When coordinates cannot easily be parsed they go to "[null island](https://raw.githubusercontent.com/auremoser/gdi-webmap/master/img/null_island.jpg)," a fictional place at coordinates (0,0).

In a bit, we'll show how you can convert, process and use a file like this to plot data on your map.


GDELT PROJECT AND GOOGLE STUFF FROM CURRENT DRAFT


**Rainer Sternfeld and Tom Faulhaber, Planet OS**
""Planet OS brings proprietary and public sensor data together into one backend system, provided with a Dashboard framework used by energy companies on running the world's second largest offshore wind farm and environmental surveys for oil companies.""

#### Backend

Using an open source geostack

"**Stefan Avesand, Ericsson Smartphone Labs**

"We use a large flora of tools at Ericsson, both commercial and open source. These include e.g. PostgreSQL/PostGIS, Hadoop/Hive, Mapnik, CartoDB, OpenLayers, ArcGIS, TatukGIS and Tableau."

Postgres and PostGIS: http://erictheise.github.io/geostack-deck/#/40

CartoDB is a Postgres database in the cloud, which means it handles a lot of your backend data needs and allows you to query for data and pull those data and basemap tiles into your front-end code, we'll be using this for part of the workshop to manage hosting easily. It's appropriate to deal with databases when you have multiple datasets you'd like to layer on your map. For single or simple datasets, you can load a file with JQuery/Leaflet. We'll demo both.

![architecture](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/architecture.png)

You can also store your data in Github, or in another service that makes it web accessible. Read more about [that here](https://github.com/blog/1541-geojson-rendering-improvements) and [here](https://github.com/blog/1528-there-s-a-map-for-that).

![github](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/github.png)

### Frontend
![Logos](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/logos.png)

Much of map development involves a mixture of map-tools for both quick desktop visualizations and dynamic web slippy maps. Riley Newcomb of Airbnb describes the company stack as leveraging AWS Hadoop and Spark for big data infrastructure, R and Python scripting for analysis, and Tableau for quick visualizations in both desktop and cloud implementations. A more sophisticated frontend setup might involve custom libraries like Rbnb/Airpy, open libraries/languages like D3 and Processing, and the now deprecated but still useful Tilemill for tile creation. On the tile-front, Mapbox also provides a map ti

There are loads of ways to approach a map here are a few approaches to mapping the same dataset.

We can make a map with the outcrop data, or other data in the [data folder](https://github.com/auremoser/foss4g-cdb/blob/master/outcrop.kml) by following a similar series of steps with both proprietary and open source tools as such:

**Using Google Maps**

* <https://www.google.com/maps/d/>
* create account if you don't already have a Gmail account
* click on Import Map in top left hand menu (or My Maps -> Create map in some Google Maps UIs)
* upload `outcrop.kml`
* explore changing the map features if you would like

**Using Mapbox**

* <https://mapbox.com/>
* create account if you don't already have a Mapbox account
* click on the Data tab at the top right hand corner of the screen
* click on import
* upload `outcrop.kml`
* select map features if you would like then click on Import Features
* explore changing the map features if you would like

**Using CartoDB**

* <https://cartodb.com/>
* create account if you don't already have a CartoDB account, [use this URL](https://cartodb.com/signup?plan=academy) to get boosted features
* click on Create Map; select Map View at the top of the screen
* click on the '+' or Add Layer option at the top of the right side menu
* upload `outcrop.kml`
* explore changing the map features, if you like

**Using Leaflet**

You can also make a map from scratch using [Leaflet.js](http://leafletjs.com/) to attach a set of points to a map made of tiles provided by OpenStreetMap.

You will first need to convert your kml file into GeoJSON (although I have both in the [data folder](https://github.com/copystar/ipam-16/blob/master/data/outcrop.kml)) for this workshop.

GeoJSON is a file format that is easily digestable by JavaScript. If you have a data format (shp, kml) that is not geojson you can convert it to the right format for your code with [GeoJSON.io](http://geojson.io/)/

* go to http://geojson.io/
* from the menu *Open* select *File* and upload our kml file: <https://github.com/copystar/foss4g-cdb/blob/master/outcrop.kml>
* notice how GeoJSON looks like in the side-menu

``` json

	{
	  "type": "FeatureCollection",
	  "generator": "overpass-turbo",
	  "copyright": "The data included in this document is from www.	openstreetmap.org. The data is made available under ODbL.",
	  "timestamp": "2015-09-14T14:05:02Z",
	  "features": [
	    {
	      "type": "Feature",
	      "id": "node/428215780",
	      "properties": {
	        "@id": "node/428215780",
	        "geological": "outcrop",
	        "name": "Sonnberg",
	        "note": "Rocky promontory, subject to erosion. Middle 	Triassic shallow marine limestone, Jena Formation (U.-	Muschelkalk, Wellenkalk). Small outcrop within E-W 	trending graben structure. Contact to MIttlerer 	Buntsandstein exposed in river bed southwest of crag."
	      },
	      "geometry": {
	        "type": "Point",
	        "coordinates": [
	          9.43865,
	          50.6228007
	        ]
	      }
	    },
	    {
	      "type": "Feature",
	      "id": "node/568331113",
	      "properties": {
	        "@id": "node/568331113",
	        "geological": "outcrop",
	        "name": "Monkey rock"
	      },
	      "geometry": {
	        "type": "Point",
	        "coordinates": [
	          177.127952,
	          -17.7323069
	        ]
	      }
	    },

```

* after the map is drawn, from the menu *Save*, select *GeoJSON*"
* refer to "Adding GeoJSON to Leaflet with Link Relations" : http://lyzidiamond.com/posts/osgeo-august-meeting to find the HTML that use can use as a template that will import GeoJSON into a map created by Leaflet.js
* use *http://{s}.tile.osm.org/{z}/{x}/{y}.png* for your map tiles
* use `outcrop.geojson` for your geojson layer: https://github.com/auremoser/ipam-16/blob/master/data/outcrop.geojson
* explore changing the map features if you would like using Leaflet.js: http://leafletjs.com/

![outcrop](https://raw.githubusercontent.com/auremoser/ipam-16/master/img/outcrop-pt.jpg)

Quick [outcrop map by type](http://cdb.io/1UPs2Nw).

TOOLS (Incorporate tools into table)

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


IOT/MICROSTATS
At a certain level of data production, devices both passively scan swaths of the earth, like drones and satellites, and also generate data which we will increasingly need to process, geocode, and coalate in real time. Image analsysis and feature extraction will become increasingly important, as the kind of integrity and detail we glean from images is so much more thorough than collections of geocoordinates for the plotting




###SYSTEMS OF SCALE
What's accross the ocean




**Boris Shimanovsky, Factual**

IOT/SAT/MICROSTAT

"It will also create more uncharted territory where security, privacy laws, and tools to understand the data will lag behind."

EVOLUTION FROM SMALL BEGINNINGS



"The open source ecosystem is great, and is, in fact, likely superior to the commercial offerings which seem behind the times.  Tools like Postgis, Solr, and Elasticsearch should not be overlooked as people overestimate the big-ness of their data.  Geospatial data, at true big data scale, doesn’t yet have an obvious silver bullet technology that makes everything great and easy.  It will, in any event, require very capable (and likely expensive) engineers to harness.  It’s hard for me to imagine a general purpose big data tool that can abstract away the geo-specific knowledge required to analyze this data efficiently."

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
"the phenomena surrounding and complicating what is interesting about geodata naturally draws us to want more processing power, the ability to aggregate and compare more disparate datasets, the ability to inform one mapped trend with another...."it’s at the heart of the information revolution underway.""

TOOLS

""Our standard set of tools and technologies are: AWS/hadoop/hive/presto/spark (data infrastructure), R & Python for analysis, Tableau for run-of-the-mill visualizations (especially since their collaboration with Stamen design for geo plotting), and then specialized tools for custom visualizations (Rbnb/Airpy, D3, Processing, Tilemill)
Also worth discussing: core_data, the knowledge repo, the ERF (all homegrown tools)
""

OPEN DATA

"SF’s OpenData project is a great example. Making data public can lead to all kinds of projects that benefit the community without requiring public resources. It lowers the barrier to entry for NGOs and crowdsources innovative solutions to public issues. The more of this we can do, the better."

**Stefan Avesand, Ericsson Smartphone Labs**
OPENDATA
"
The most **important contribution needed from these parties is open data**. This involves basic data such as administrative levels to all particular domains managed by the government, e.g. transport, demographical and environmental data."

**Robin Kraft, Space.Ninja and GlobalForestWatch.org**

OPEN DATA
"ESRI is the Microsoft of the geospatial world, for better or for worse, and it’s very expensive stuff. You can do a lot of great stuff with OSS, and gov’t agencies should be more open to that.
"

**Rainer Sternfeld, Founder + CEO, Planet OS**


TOOLS
""Apache Spark lets us do the analysis we need to to understand and index some of the massive datasets we process.
HBase gives us a platform for storing and retrieval the results of distributed computations
ElasticSearch gives us a nice platform for free-text and polygonal retrieval
Mesos and various projects built on Mesos give us a stable compute infrastructure.

While members of our team contribute to various open source projects (such as D3 and Clojure), our contributions in the geo/big data have been small so far. Hopefully we will increase our activity here over the next year or so. PlanetOS has begun releasing front-end code such as the cirrusjs library for visualization (https://planetos.com/blog/cirrus-js/) and we will continue to release visualization, data processing, and analytics code as we see the opportunity.""

**Stefan Avesand, Ericsson Smartphone Labs**

TOOLS

"We use a large flora of tools at Ericsson, both commercial and open source. These include e.g. PostgreSQL/PostGIS, Hadoop/Hive, Mapnik, CartoDB, OpenLayers, ArcGIS, TatukGIS and Tableau.
"
