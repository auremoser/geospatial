

Contact Riley about Sister Neighborhood idea - actually exists, visualized project, how would you deal with the sizing issue (brooklyn is a borough, it has many neighborhoods like kreuzberg, but the whole thing isn't that)


Among practitioners there's a clear preference for open source tools and an evolving distain for their proprietary counterparts. Despite assumptions about the lesser quality of open source in the general community, QGIS performs relatively comparably to ArcGIS, with web-based open source libraries as a clear winner in implementation accross companies and geo-spatial challenges. Even the assumption that Open Source does not provide industrial grade analysis or development is being disproven by improvements in Postgres and the adaptation of PostGIS functionality to open source products like Pyro, in tandem with the prevalance of Apache tools like Hadoop, Hive in "big" data stacks.

Web scripting for data processing and display, PostGRES for storage at small to moderate scale, PostGIS for processing and mobile for collection and distribution are bold trends in the industry, with an increasing favoratism toward open source, and open access data formats.
***

In this ecosystem of pro-open it seems strange that anyone might find a way to monetize geo, but many companies have. Mapbox has a component of their software this is proprietary, and subscription levels for map tool usage, yet they release open source libraies like Tile Reduce, CartoCSS, Turf, Carmen, Mapnik, the tile server, and the iD Editor. Likewise they've built significant support systems for OSM. Airbnb despite it's proprietary data model has open sourced two projects in the past year, Airpal and Airflow. In general, the guilt of reliance on open source for infrastructure (Postgres, Hadoop, Hive, Prsto, Spark) or data (OSM) prompts even private companies to give back, and so the open source ecosystem continues to be fed by pretty remarkable developer talent. The future isn't now however, and much of the open source and scripting language stack could benefit from performance build for large scale data. "Most developers use simple web based tools, but these scale very badly due to the low performance of JavaScript, lack of caching and the time it takes to transfer the raw data." ~ Stefan Avesand

When you're thinking of processing and standardizing data for the globe, you're also recognizing as a default that these data, if available, will come from different countries, with different formats, metadata typologies and application profiles. To that end, the Open Geospatial Consortium (OGC), an international consortium of companies, goverment agencies and universities developing concensus around geo standards, has done decent work to create and propogate interface guides throughout the industry. Still, open source still has a lot of room to grow in big data processing and distributed systems. Much of the unsolved industrial problems in geo involve constructing geographic indices, dealing with complex geometries and costly queries, and the specialized problems of photogrammetry, or satellite work. "As usual, research is required to solve that problem which is a mix of a math problem (mainly topology) and a computer problem (right structure and replication/distribution). Others problems include streaming of satellite images or pictures taken from plane --" ~Andy Petrella of Data Fellas and Spark Notebook


PROCESS
"The analytical process typically starts with a business problem that needs an answer, which gives rise to several hypotheses that we might want to test. We then collect and join data from relevant sources. The data is inspected using different methods to understand characteristics and quality.
We can now start developing the pipeline that will convert data into visual information. Many times the data needs to be transformed, filtered and aggregated. After that we can apply map algebra, such as clustering of points, calculating geodistance or joining with shapes (e.g. administrative areas of different levels). The final result can be presented visually using a map or in tabular format."


PRIMERS

* CartoDB (http://academy.cartodb.com/) 
* Mapbox (https://www.mapbox.com/tilemill/docs/crashcourse/introduction/). 
* Boundless has some good material algebraic + postgis (http://workshops.boundlessgeo.com/postgis-intro/). 

EVENTS

* State of the Map
* FOSS4G
* Strata
* Local/State GIS Conferences: CalGIS conference, WLIA




"**The world still needs a consistent, current and multilingual gazetter** -- a list of place-names that are well-typed and related in a poly-hierarchical relationship.  We started this with Geoplanet at Yahoo (which I maintain in one version at https://github.com/twbell/GPLplanet) and Geonames is a similar option.  Mapzen's 'Who's On First' project is closest to what I would like to see conceptually, however one may feel about the product name." 


Prior to the evolution of web or even desktop mapping tools, libraries carried print maps in large texts often partnered as pairs: the Atlas, showing landscapes and coordinates, points and forms, and the Gazeteer, providing those places with standard naming, points of interest, version history and semantic or relational context.

Perhaps companies like Planet OS, geared toward a goal "to index the real world, to provide the tools for humanity to create a Planetary Nervous System using Earth observation and geospatial sensor data." or Planet Labs which attempts to collect and store daily global imagery of the world will push citizen cartographers to the brink of big geospatial needs. The collection volume and goals in both cases grow diurinally, processing that much information meaninfully, and with context, is a challenge that everyone is struggling to meet. As Rob Emanuele, lead on GeoTrellis at Azavea asserts, "the deluge of imagery is going to really push forward the tooling, because otherwise there will be a great sea of data and no way to navigate or explore it."

In many ways, the volume, profusion, and formating of data continues to complicate while the general need to sort and semantically contextualize those data grows, and the tools to do so are diverse but tend toward open source, and methodologies for breaking "big data" and massive challenges into smaller sets. "PostGIS is great, but PostgreSQL can’t scale in the way that Cassandra, Hadoop, and Spark can. We need geospatial capabilities added to those scalable frameworks, and that’s what will be happening." ~ Rob Emanuele, Azavea + GeoTrellis

##INTERVIEWS



**Boris Shimanovsky, Factual**

STACK

"We use Postgres/Postgis and Solr/Lucene a lot.  We use geo-sharded Lucene indices even in Hadoop and Spark jobs."

OPEN SOURCE

"I actually hope it [open source] will be the only game in town.  In our big data efforts, we exclusively use open source software and the tech we built ourselves.  We’ve never even considered a commercial package for general purpose analysis."

"**The open source ecosystem is great, and is, in fact, likely superior to the commercial offerings which seem behind the times.  Tools like Postgis, Solr, and Elasticsearch should not be overlooked as people overestimate the big-ness of their data.**"

GOVT + DATA + TOOLS

"PDFs are not data.  Government has slowly been getting better at this, but it’s fractured and inconsistent."

"Obviously, data should be released in open formats like shapefiles, KML, and geojson while proprietary, antiquated formats like ArcGis should be shunned."

"**It’s hard for me to imagine a general purpose big data tool that can abstract away the geo-specific knowledge required to analyze this data efficiently.**"

IOT/SAT/MICROSTAT

"It will also create more uncharted territory where security, privacy laws, and tools to understand the data will lag behind."

UNCERTAINTY/2D

"There’s a great deal of uncertainty in places and mobile data.  2D coordinates alone can’t pinpoint that one is at a Starbucks -- there is substantial and unquantified GPS error, fraud, altitude, and many unknowns.  **Our world is probabilistic.**
"

FUTURE

"**Apps that fail to understand your context will soon seem quaint.**"

EVOLUTION FROM SMALL BEGINNINGS

"Several of our core products started as a hackathon project.  One of my hackathon projects evolved to process billions of geo annotations every day."

PRINCIPLES OF BIG DATA ANALYSIS

"https://en.wikipedia.org/wiki/Geohash
Hash functions
Sorting
Geo-sharding
"

**Tyler Bell, Factual (referred by DJ Patil), Mapbox**

STACK

OPEN SOURCE

"Open Source development is the rule rather than the exception"

"Mapbox and Mapbox employees maintain or contribute to open data, open specifications, and open software include the Mapbox Vector Tile Specification, Carmen and Mapnik, Tile-Reduce, Turf, the iD Editor, and massive fixes and contribtions to OSM (OpenStreetMap  -- http://www.openstreetmap.org/).  We talk about it more here: https://www.mapbox.com/about/open/.
"

"**Remember: geo data is not just points, lines, and polygons, it is anything with a spatial component, so we're looking at mobile, traffic, parking, at tech, routing, geocoding, place disambiguation, logistics, asset tracking, macro economic analysis, topographical analysis, biomass analysis, etc.**"

GOVT + DATA + TOOLS

"The problems really boil down coverage, quality, and creation"

"This is a gross and certianly unfair categorization [between non-spatial and spatial data organizations], of course, but frames my answer: **the geohash (https://en.wikipedia.org/wiki/Geohash)** is the most powerful tool of the non-spatial companies, while the purely spatial camp can benefit hugely from Mapbox's tile-reduce libraries (https://github.com/mapbox/tile-reduce).  **From a purely GIS-POV I remain blown-away by the capabilities of PostGIS, and never touch a GUI where I don't have to (but when I do it is always QGIS)**."

"Governments **increasingly see the advantages of open geo data, but not uniformly**: the US' removing Selective Availability from GPS is possibly the most productive open data initiative in the history of the world (not least because data begets data, so it is still giving us returns), while on the other end of the spectrum in China you still have a proprietary coordinate system (known as Mars, formally as GCJ-02) designed to obfuscate WGS-84 by applying a semi-random offset of between 100-700m to every coordinate."

"**Remember: geo data is not just points, lines, and polygons, it is anything with a spatial component**, so we're looking at mobile, traffic, parking, at tech, routing, geocoding, place disambiguation, logistics, asset tracking, macro economic analysis, topographical analysis, biomass analysis, etc."

Paraphrase: 
"But generally the news is good: the UK EA has made their national lidar coverage open, Australia is releasing its addresses as open, and the US Government has publicly committed to supporting Open Mapping as part of the Open Government Partnership https://www.whitehouse.gov/blog/2015/10/27/advancing-open-and-citizen-centered-government."

NGOs have been making great strides in support of open data for solving human problems. 
"A great data-point for the immediate and tangible benefits of Open Data is the work that the Humanitarian OpenstreetMap Team (HOT) has been doing: https://hotosm.org/, most recently mapping the data in the path of Hurricane Patricia in Mexico *in advance* of the hurricane, in anticipation of humanitarian need https://www.mapbox.com/blog/mapping-mexico/: Better maps make for better disaster response."

IOT/SAT/MICROSTAT

"...we -- technologists, but humans more broadly -- are moving away from the world of monolithic data collection, to one where small signals, each one perhaps insignificant by itself, are combined to create the spatial intelligence of the future.  Every car is becoming a Google Streetview car and every consume a sensor."

"Mobile has taken us from a read-dominated world to a write-dominated world --  we are now creating more data than we consume, even if we are still termed 'consumers'.
"
""**All of these devices are capturing data and annotating it geographically, or capturing geo data and annotating it contextually;  In one sense these are all 'maps that move', but really their availability is both enriching the quality and multiplying the breadth sensor coverage.**""

UNCERTAINTY/2D

FUTURE + EVOLUTION

"Open data is the big wave though: we have OSM for the map, and OpenAddress for addresses (and AU is the latest country to relaize the power of open, geocoded addresses: https://blog.data.gov.au/news-media/blog/geocoded-national-address-data-be-made-openly-available  POI data is likely to be that last to fall, for a number of differnt reasons."


PRINCIPLES OF BIG DATA ANALYSIS

**Big data and spatial have lived at opposite ends of the sector's toolset for far too long, and have only recently begun to stop glaring at each other across the room.**

" **Big Data' as a thing was still being defined when I was at Factual, but we used traditional map-reduce approaches to distill data into coherent, consistent, and ultimately valuable products, and later as a mechanism to pre-index content for high-performance queries in the ad-tech stack.** "


****

**Riley Newcomb, Airbnb**

STACK

""AWS/hadoop/hive/presto/spark (data infrastructure), R & Python for analysis, **Tableau for run-of-the-mill visualizations (especially since their collaboration with Stamen design for geo plotting)**, and then specialized tools for custom visualizations (Rbnb/Airpy, D3, Processing, Tilemill)""

OPEN SOURCE

we’ve open-sourced two tools that we use here regularly (Airpal and Airflow)

GOVT/TOOLS/DATA

"Why are bars and car dealerships always clustered together? Why hasn’t nomadism taken off? Silicon valley hasn’t become silicon country.. **Location is a hugely important factor in understanding the world around us**
" and the phenomena surrounding and complicating what is interestin gabout eodata naturally draws us to want more processing power, the ability to aggregate and compare more disparate datasets, the ability to inform one mapped trend with another...."it’s at the heart of the information revolution underway."

IOT/SAT/MICROSTAT

FUTURE + EVOLUTION

"**Geography is such a critical lens for understanding the world around us** that I expect geo tools and datasets to continue to improve"


PRINCIPLES OF BIG DATA ANALYSIS

****
**Rainer Sternfeld and Tom Faulhaber, Planet OS**

STACK 

(OSS)

* Apache Spark lets us do the analysis we need to to understand and index some of the massive datasets we process.
* HBase gives us a platform for storing and retrieval the results of distributed computations
* ElasticSearch gives us a nice platform for free-text and polygonal retrieval
* Mesos and various projects built on Mesos give us a stable compute infrastructure.


OPEN SOURCE
"the open source tools for geospatial processing in the big data arena have been very limited in scope and not really “industrial grade” <-

"
While members of our team contribute to various open source projects (such as D3 and Clojure), our contributions in the geo/big data have been small so far.""

"https://planetos.com/blog/cirrus-js/" < visualization

GOVT

IOT/SAT/MICROSTAT

"[They] have been focused on two problem spaces: **data supply infrastructure for government agencies that publish massive-scale data to the industries**, and data dashboards for the energy industry. Specifically, how do you make it easy for users to discover, access and use weather, climate, environmental, fisheries data in a machine-readable way"

UNCERTAINTY/2D

"the more unpredictable the weather, climate and the surrounding environment is, the more their people, plants and technology are exposed to external risk. More data doesn’t necessarily help, but the combination of having relevant data elegantly combined in one system in the cloud opens up completely new opportunities in analytics, mobility and collaboration."

FUTURE + EVOLUTION

"
The one that is closest to our mission at Planet OS are projects that help us understand and address the issues created by climate change"

* NASA Eonnet
* Earth Exchange team


PRINCIPLES OF BIG DATA ANALYSIS

****

**Stefan Avesand, Ericsson Smartphone Labs**

**SMARTPHONES**

****
STACK

OPEN SOURCE

"I think that the dynamics and speed within the open source community will be able to handle this [development of IoT as the major industry driver] when the time comes, as long as the community is large enough."

GOVT

"
The most **important contribution needed from these parties is open data**. This involves basic data such as administrative levels to all particular domains managed by the government, e.g. transport, demographical and environmental data."

IOT/SAT/MICROSTAT

UNCERTAINTY/2D

"**Just putting a few million points on a map doesn’t give much information. By aggregating, interpolating and joining data we can deliver deeper and more accurate visualizations.**
"

FUTURE + EVOLUTION

"A good example is how **Flowminder has managed to improve emergency response to natural disasters by linking data collection directly with the decision making process***, e.g. during the Haitian earthquake of 12 January 2010 emergency response staff was able track population displacement in real time by using data from telecom networks."

And Ushahidi + HOT OSM


PRINCIPLES OF BIG DATA ANALYSIS


****


**Robin Kraft, Space.Ninja and GlobalForestWatch.org**

**SATELLITES**

STACK

OPEN SOURCE
"Open source is key. Everyone I know depends heavily on open source for projects and to build their businesses, and I don’t see that changing."


GOVT
"ESRI is the Microsoft of the geospatial world, for better or for worse, and it’s very expensive stuff. You can do a lot of great stuff with OSS, and gov’t agencies should be more open to that.
"

IOT/SAT/MICROSTAT
"I expect IoT will make it easier to collect data. A lot of science data is collected at very low spatial and temporal resolution."

"All in all, with these technologies you’ve got some amazing opportunities for improving transparency. That is great in many ways, but there are obviously privacy issues"

UNCERTAINTY/2D

"Scaling up sophisticated image processing algorithms is hard. And deep learning is a potentially revolutionary technology that is very hard to use. But tech like Docker and Kubernetes makes the former easier, and there are frameworks and services coming out that make training and visualizing and modifying deep learning algorithms easier (see vitruvianscience.com)."

FUTURE + EVOLUTION


PRINCIPLES OF BIG DATA ANALYSIS

****
**Andy Petrella, Data Fellas plus Spark Notebook creator**

**SPARK**

STACK

OPEN SOURCE

GOVT

IOT/SAT/MICROSTAT

UNCERTAINTY/2D

FUTURE + EVOLUTION


PRINCIPLES OF BIG DATA ANALYSIS

****
STACK

OPEN SOURCE

"Although they need to take the distributed computing turn correctly, and it’s not easy"

"Regarding users, I’d say that the current standards from OGC are pretty well done, and are evolving in interesting directions. So, user should just keep using them and leave the rest as a black box behind."

GOVT / TOOLS

"I experimented GeoTrellis for raster, and I’m still looking for a good lib for vector (Magellan is an option, but again, after talking with the creator, this Magellan is overlooking the topological problems and are only doing points stuff)"


IOT/SAT/MICROSTAT
"Sort of problems that we can foresee… probably the emergence of LiDAR combined with drones. Drones can take a great place in our future, hence we’ll need them to be asap autonomous and process what they have efficiently. And what they have are geodata gathered live (cams, pics), weather data including topography. "

"These drones will then be scanning the earth constantly, like satellites…, but at a lower level, where the details are interpretable efficiently. But they will also generate predictions and other kind of data geolocalized too which we’ll want to be able to process."

UNCERTAINTY/2D

FUTURE + EVOLUTION
"**Maybe saying that two components are always part the data we process: Geo and Time** (minkowski discovered that a while ago :-D)." Libraries like Torque work to integrate the two


PRINCIPLES OF BIG DATA ANALYSIS

"**Really geo in Big Data is not really well known, understood at the trivial level."**

"I never talk about Big Data, I always talk about distributed systems.
Distributed systems are known to be most welcomed in the majority of geo-oriented use cases. If only even considering the pyramid construction of a battery of landsat images, considering the rendering of a multitude of combination of 3 layers -- it takes a lot of time, and is then rarely done.
"

"Distributed systems are these days accessible for the crowd, open source solutions are ready for production and should be considered in many cases, like LiDAR generalization, archives crawling, raster vectorization and the list goes on.
There are also opportunities to take a place in the market, specially building distributed-friendly spatial indices (like SD-Tree), data partitioner with optimized and multi level hilbert curves and so on are not really accessible yet."

****
**John Thayer, City of Palo Alto**
**GOVT GIS**

"Within a City most of the information used for the City to properly service the residents is spatial in nature."

STACK

Google Fusion Tables and Google Maps, Windows OS

OPEN SOURCE

GOVT

"Local Government is responsible for the creation of geospatial and big data within the jurisdiction.  State and Federal government should support the Local Government data gathering and creation efforts.
"

IOT/SAT/MICROSTAT

UNCERTAINTY/2D

FUTURE + EVOLUTION


PRINCIPLES OF BIG DATA ANALYSIS

****
**Rob Emanuele, Azavea plus lead on GeoTrellis**

**GEOTRELLIS**

STACK
"open source geospatial library GeoTrellis. GeoTrellis was a Scala library for doing large scale raster operations. I wasn’t exactly sure what that meant, but I became determined to work for them" (using Spark as our distributed computation engine)

OPEN SOURCE

GOVT

IOT/SAT/MICROSTAT

"The Landsat satellite program, which has been taking images of the earth since 1970, has an archive that is most certainly big data. The size of the imagery hosted to the public for free on Amazon Web Services, which only hosts 2015 Landsat data as well as select scenes from 2014 and 2013, amounts to over 250 Terabytes. If you imagine the largest hard drive you’ve heard of, you can try to think of how many of those hard drives it would take to hold all of Landsat’s entire imagery set."

"With the number of microsat and UAV’s taking imagery, there is only going to be more and more we can do with that data. I think that the deluge of imagery is going to really push forward the tooling, because otherwise there will be a great sea of data and no way to navigate or explore it.
"

UNCERTAINTY/2D

"I’ve **mostly been working with the general problem: how do we process large sets of rasters**. More specifically, I’ve been working with imagery, and how to create simple mosaics of large sets of imagery into tiles that can be served out on web maps such as leaflet."

FUTURE + EVOLUTION


PRINCIPLES OF BIG DATA ANALYSIS

"But “Big Data” is not just about how large the data set is. It’s about how we deal with it. How we store it, and how we process it. There’s a whole ecosystem of tools for dealing with data at this scale, and are known as “Big Data” frameworks or “Big Data” platforms.
"