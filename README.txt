TWITTER DATA ANALYSIS
---------------------



CONTENTS OF THIS FILE
---------------------

 * Introduction
 * Data Collection
 * Analysis
 * Application



INTRODUCTION
------------

This assignment has three modules, namely, 
 
 * Data Collection
 * Analysis
 * Application



DATA COLLECTION
---------------

There are three parts to this module. 


 * Collection of random tweets

	- In this section, the tweets have been gathered using 
	  Twitter Streaming API that provides real time tweets.

	- In this case, tweets have been collected at some time-interval
	  due to the restricted processing power of my system. But 
	  on a system with better processing power and memory, 10000
	  tweets can be streamed in a single go.
 
	- The gathered tweets have been stored in a MongoDB 
	  MongoDB database 'EngTweetsDb' collection 'en_tweets_col'


 * Entity Recognition of Tweets
	
	- System Requirement: Download the models and a jar file, since the NER
	  classifier is written in Java (specificaly, v1.8).

	- Using Stanford NER tagger to recognise named entities in the 
	  tweet text. The result is then stored in a MongoDB database 'Entity' 
	  collection 'entity_record'.	

	- Once the entities are recognised, five most frequently occurring  	     
	  named entities are identified.

	- System Restrictions: Due to low processing power and memory of my system, 
	  entity recognition process was very time-consuming and often, failed. 
	  Thus, for the purpose of analysis, entity recognition process was carried for 
	  1000 tweets. The list of five most frequently occurring entities obtained in the step 
	  is a result of 1000 tweets. 
	
	- Note: When run on a system with better processing power and more memory, the code
	  written will work smoothly.


 * News Articles Collection
	
	- For each entity out of five, 10 news articles per entity have been collected 
	  using a AYLIEN News API.
	
	- These articles have been stored in a MongoDB database 'News' collection 'articles'.

 
	
ANALYSIS
--------

There are four kinds of analysis that have been carried out on the collected data.


 * Sentiment Analysis

	- Using 'textblob' package, sentiment analysis has been performed on all 10000 tweets 
	  and 50 news articles collected in the previous module. 

	- Comparison of twitter and news sentiments analysis for the common-named entities 
	  identified in the previous module, plotted in 'plotly'. 

	- As for a qualitative comparison between predicted versus original sentiment of the 
	  tweet and news, the results can be accessed in an Excel file named, qualitative comparison. 



 * Content Analysis

	- As part of content analysis of tweets, the following attributes have been showcased. 
		
		# Word Cloud using 'wordcloud' package, post removing stopwords 
		
		# Bigrams using 'NLTK' package

		# TF-IDF using 'sklearn'

		# Hashtags extracted from tweet data 
	
		# Followers_count of twitter user


 * Spatial Analysis

	- Location information has been extracted from the tweets information
	  stored in a list.

	- Using 'geopy' package, the coordinates and complete address of the 
	  locations in the location list which are then stored in a MongoDB 
	  database 'tweet_coord'.

	- Then, coordinates (latitude and longitude, separately, are stored in a 
	  DataFrame. 

	- From this DataFrame, values (coordinates) and locations of the places are 
	  plotted on a world map using 'Folium', which works as a wrapper for 
	  Leaflet.js

	- The map, thus created is interactive and has various features like zoom, pan and hover. 

	- This map can be viewed in the Jupyter NOtebook as well as saved in a .html file. 

	- The above approach remains the same for plotting locations. The only difference is
	  that plottin ghere takes place at the country level because of the lack of information about 
	  city and state. 


 * Temporal Analysis

	- Timestamp in ms is provided in tweet information. It is first, converted into seconds.

	- Using 'datetime' package, the timestamp (in seconds) is converted into Datetime format
	  YYYY-MM-DD HH:MM:SS:MS

	- Location information, as obtained in the previous section is to be showcased in the plot. 

	- Location and Datetime data is then stored in a DataFrame. 

	- Using 'plotly' package, an interactive time series scatter plot has been created. This plot has 
	  the featurs of zoom (upto millisecond level), pan and hover. Consolidated data for 2 days, 3 days, 
	  1 month can be viewed using the buttons shown above the plot on the left. 

	- For news articles, since the datetime information is not available in desired format YYYY-MM-DD HH:MM:SS:MS, 
	  functions were created.

	- Once the date time information is available in the aforementioned format, the process of plotting remains the same. 



APPLICATION
-----------

	- The application can be prepared using Flask and then deployed on Heroku. 

	- In the web application, there are three tabs, namely, 

		# Home 
	
		# About 

		# Analysis

	- In Analysis, there are three views, namely, 

		# Sentiment Analysis where an entity is input and the output is a graph showing a comparison of twitter and news sentiments. 

		# Spatial Analysis where there are two world maps depicting the spatiality of tweets and news, respectively. 

		# Temporal Analysis where there are two scatter plots showing when tweets and news were generated/streamed.








