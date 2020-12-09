# Question 1

I have always been interested in Application Stacks and I have always admired
one particular organisation: Airbnb and the way they:
• Seamlessly allow users from over 81,000 cities to rent out their homes to other people who are looking for accomidation
* Allow users to invite other friends to see the same places they are looking to book
• Use bots for customer support


Presentation Layer
Ruby on Rails - Airbnb uses this web-application framework for database-backed web applications. It deals well with HTTP requests and scales horizontally very well.
ReactJS - this advanced Javascript library is for creating UIs like that of Airbnb. 
It provides great rendering performance which improves the user experience. It does this by eliminating the usage of code-heavy frameworks and implements reusable code.

React Native - this technology is used for mobile app development. It is platform agnostic so Airbnb can leverage all of its engineers to build and support their mobile app and 
it can be deployed in both iOS in Android code bases.
Its also lean because the one repository can be deployed across all mobile platforms.


Business/Application Layer

Nginx: This is a web server that Airbnb uses to provide services using a RESTful API. It speeds up content delivery by using a proxy server. This proxy server ensures Airbnb's security and scalability.
Additionally, Nginx can load balance, allows for both reverse and mail proxy, and can handle static files, index files and auto-indexing. 



Data Access Layer

MYSQL - Airbnb uses MySQL to manage core business data. The databases are broken down by application which allows for easy capacity planning.
Users' messaging threads and calendar listings are stored seperately to the core booking flow data. They are managed in their own seperate databases.

AWS - Within this, Airbnb uses Elastic Load Balancing to automatically distribute incoming traffic between EC2 instances. This allows for Airbnb's system to still perform well
even during sudden traffic spikes or unexpected traffic fluctuations. Furthermore, to monitor their servers and their resources, Airbnb uses Amazon CloudWatch.
CloudWatch collects the operational data in the form of logs, metrics and events. Morevoer, it allows supervision of EC2 assets via the Amazon Management Console. This is made up of automated dashboards
which gives a view of their resources, applications and services on AWS.

Redis - This is a no SQL scalable, key-value pair database that Airbnb uses. It allows Airbnb to store cache infrastructure which is transient and needs to be served up fast.

Amazon RDS - This helps to simplify time consuming adminitration tasks associated with databases. Difficult procedures that Airbnb does such as replication and scaling can be easily completed with a basic API call 
or through the AWS management console. Airbnb further uses Multiple Avaliable Zones to automate database replication and augment data durability.

References:
https://www.forbes.com/sites/quora/2018/02/20/what-technology-stack-does-airbnb-use/?sh=9eeb2484025c
https://yalantis.com/blog/the_technology_stack_behind_airbnb/
https://medium.com/@poojaseenu1999/the-technology-stack-behind-airbnb-6b23fe425612
https://dev.to/tyler032/tech-stack-to-build-marketplaces-like-airbnb-1ne1
https://softwareengineeringdaily.com/2018/09/24/show-summary-react-native-at-airbnb/
https://enqueuezero.com/airbnb-architecture.html
https://hub.packtpub.com/what-software-stack-does-airbnb-use/
https://medium.com/airbnb-engineering/unlocking-horizontal-scalability-in-our-web-serving-tier-d907449cdbcf


# Question 2

Airbnb collects data from users over the world and has flunctations in demand due to the different holiday seasons.
The data comes from both those looking for rental accomidation as well as those trying to rent their property.
Users can use Airbnb both from their computer or from mobile devices such as iOS and Android.
Therefore, there is a lot of data to both store and analyse.

The Hadoop Distributed File System (HDFS) is what Airbnb uses this as their core data platform the drives the site and their analytics. 
Airbnb stores unstructured data such as room info, room owners, locations of the room etc. 
Hadoop is a framework for stores and processing this big data. It split data into chunks and saves across many servers. It also uses the MapReduce algorithm which allows for processing and generating big data sets in a parallel manner. 
The name MapReduce comes from reading data into a database, mapping it for analysis and performing maths operations to reduce it. This is what is done to bigdata in hadoop.
Airbnb uses Hadoop to store users data across large files and replicates their data across multiple hosts to achieve reliable information retrieval.
In addition to the Hadoop File System, Airbnb has a data warehouse that uses Hive. Airbnb has over 1.5 petabytes of data in Hive-managed tables within its Hadoop Distributed File System which is hosted on EC2 instances.


Airbnb has millions of photos to store from its users. They are important as they show off the accomidation being rented. 
Another technology used by Airbnb is S3 or Simple Storage Service which is a part of AWS. Airbnb stores its images for its website in S3 and stores backup data in Hadoop clusters along with using the Presto SQL query engine.
Presto is high performance and distributed. As a distributed query engine, its treats the entire database cluster as a single, logical SQL database. It can use multiple servers for querying so that no single server becomes a bottleneck. Airbnb uses this to combine data from multiple sources and to allow analytics
to be performed across the entire organisation.

The Presto query is critical for many of Airbnb's features. For example, Airbnb price feature continuously tells hosts what the probability is of them getting a booking at the price they have chosen.
Hosts can see what dates are likely sold out and the current price offering and which ones are not. 
Employees are taught SQL so that all can query the data warehouse it maintains. In addition Airbnb has created a tool called Airpal so that it is easy to design SQL queries and dispath them to 
the Presto layer of the data warehouse.

Also Airbnb's price recommendation engine pulls in over 5 billion training data points and trains a model to predict the price of a listing depending on various factors like the neighbourhood, house size etc.
The machine learning package that Airbnb use is Aerosolve and was built by their own data science team.
Additionally, it can produce models based on conditional probability. It created a user data driven search model which 

https://www.dezyre.com/article/how-data-science-increased-airbnbs-valuation-to-25-5-bn/199
https://medium.com/airbnb-engineering/using-chatbots-to-provide-faster-covid-19-community-support-567c97c5c1c9

https://www.nextplatform.com/2015/09/10/airbnb-shares-the-keys-to-its-infrastructure/#:~:text=The%20core%20data%20platform%20employed,the%20Hadoop%20Distributed%20File%20System.&text=On%20top%20of%20the%20HDFS,and%20open%20sourced%20by%20Facebook.
https://www.nextplatform.com/2015/09/10/airbnb-shares-the-keys-to-its-infrastructure/

# Question 3
On the back-end, Airbnb uses:

5000 AWS EC2 instances. They are all 3.8xlarge machines and are each backed up by 3 Terrabytes of Elastic Block Storage. All the Hadoop Data File System data is stored in this mounted EBS.
1500 of the EC2 instances are deployed for the web-facing parts of the applications and the remaining 3,500 for analytics and ML alogrithms
Elastic Load Balancing is used to distrubte the incoming traffic between multiple EC2 instances.
Airbnb holds around 1.5 petabytes of data in their Hive-managed tables in Hadoop Distributed File System clusters.

Simple Storage Service (S3). This service houses backup fata and static files. Airbnb uses this service to store over 10 terabytes of user photos.
Amazon Elastic MapReduce - To process all of the data that Airbnb receives, MapReduce is used. It helps process and analyse 50 GB of data daily in the AWS cloud.
Specifically, the mapreduce framework breaks down the input data into smaller fragments or shards, that distribute it to the nodes that compose the cluster.

Amazon CloudWatch - this is a tool for supervising all of the EC2 assets from the AWS Management Console.

Amazon RDS

https://ngenioussolutions.com/blog/role-played-by-amazon-web-services-aws-in-growth-of-airbnb/
https://www.nextplatform.com/2015/09/10/airbnb-shares-the-keys-to-its-infrastructure/
https://medium.com/airbnb-engineering/data-infrastructure-at-airbnb-8adfb34f169c
https://medium.com/@abhiraj19000/aws-airbnb-case-study-43e34e9fb8b3
https://ngenioussolutions.com/blog/role-played-by-amazon-web-services-aws-in-growth-of-airbnb/



# Question 4

Spotify provides developers with a total of 13 different APIs. Three of the main APIs available are below:

1. User Library API
The endpoints in this API are for retrieving information about and managing tracks that a current user has saved in their "Your music"  library.
This API can be used to get, save and remove the albums, shows and tracks for the current user library. This is done by calling the API endpoint and providing the requests parameter and header fields.

2. Playlists API
This API allows playlists to be created by the user. In addition items can be added, removed and replaced in each of the playlists and the playlist can have a photo and details both added or removed.
These endpoints allow the user to customise their own playlist with their favourite songs.

3. Playback API
This API gives functionality to the User's Playback. The User's Playback plays the user's tracks. In this playlist are a queue of items.
The API allows you to play and pause the user's playback, repeat a track, seek to a position in a current track, shuffle or skip tracks, and many more different functionality. 

The following entities help to fulfill the functions of the organisation.

1. Track 

The track entity stores the the details of the particular song. 
The API can retrieve attributes such as its name, duration, artist who created it, duration, album it is from, created at time and genre.
The track object in full contains a simplified album object, an array of simplified artist objects, its name and popularity, track number, available markets and its spotify URI.

2. Episode 

The episode entity has all the details of a particular episode. This is so that the user can find out all the information about a particular episode they are interested in.
The objects includes information such as the eposide description, duration in milliseconds, an audio preview in mp3 format, images from the episode, the languages used in the episode, 
the show that the episode belongs to and the Spotify URI of the episode

3. Album

The album API allows developers to get information such as the artist's name who wrote the album, the album name, the markets its available in, the year it was released, images from the album and tracks on that album
The entity itself has information about the album such as the type of album, an array of simplified artist objects, an array of simplified track objects name, popularity, label, a release date and the spotify URI of the album.


4. Artist

The Artist API gives back information on the number of followers for that artist, the genres for the artist, images of their songs, their name and their popularity. 
The Artist entity itself contains the artists array of genres, an array of images of the artist, their number of followers, their name, popularity and spotify URI.
Users can find an artists they like and listen to their songs on Spotify. They can also find links to their social media pages, a bio of the artist, how many people monthly listeners that artist has and where in the world those listeners are from.

5. Playlist object

The Playlist entity contains information about one of the user's playlists. Information it has include the name of the playlist, an array of up to three images for the playlists, an array of playlist track objects,
the spotify URI of the playlist and an followers object which has info on the followers of the playlists. The playlist API can be used to retrieve, modify and even delete tracks from a user's playlist.
This object allows users to give a group of similar songs a name, images and added to that playlist.
Also the songs can be ordered which allows them to listen to each track in the order that they choose.

6. Playlist track object.

Playlist objects have their own playlist track objects within them. This allows a user to access particular tracks within their playlist. The playlist object stores a track or episode object but
also stores additional information which are the timestamp it was added at, who added it and whether the track or episode is local.

7. User object (public)

The entity contains information about a user that is publically available. It has the user's display name, a followers object with information about their follows, the user's pofile image
the user's id and their Spotify URI. This user object allows other users to see which artists their friends have been listening to as well as their public playlists.

8. User object (private)

The entity contains the private information about a user that only they and Spotify itself have access too. The private information includes information not in the public user object.
This includes the country of the user, their email address and their Spotify subscription level eg. "premium", "free".
This information is used by Spotify to check whether to charge a user (premium vs free), what shows they may like to see (country) and send promotional material and billing information to them
via their email address.

9. Show object (full)

Show object is the entity that stores show details. This is required so that users can find out information about a show such as the name, description and images of it.
Furthermore, if they are interested in the show they can access the array of episode objects and choose a particular episode that they would like to watch.

# Question 5

![](ERD_Question6.png)

# Question 6

First process
https://api.spotify.com/v1/artists/{id}/top-tracks is Spotify's endpoint for retrieving the top tracks of an artist by country.
A user may wish to see what are the top tracks of one of their favourite artists in their home country. This API endpoint gives them that information.

The input data to the artist top tracks API endpoint is 
- a valid access token (Header field)
- the spotify id of the artist (path parameter)
- country to look at for the artist's top tracks (query parameter)

The output data from this endpoint are an array of track objects for the particular artist in the inputed country.
Each track object in the array has the following data:

album -  The album on which the track appears
available_markets - A list of the countries in which the track can be played
duration_ms - The track length in milliseconds
explicit - Whether or not the track has explicit lyrics
name - 	The name of the track.
popularity - A value between 0 and 100, with 100 being the most popular
preview_url - A link to a 30 second preview of the track

Achieving Organisational Objectives:

This API endpoint helps users be entertained by listening to tracks from their favourite artists.
Spotify users can use this API endpoint to view all the top tracks of their favourite artists.
If they like, they can find the most popular track of their favourite artist and then hear a 30 second preview of the track to see if they like it.
The track objects also let users know which album the track is from in case the user wants to find out what other tracks are on that same Album.

Helping users navigate to tracks by their favourite helps improve the experience of users and encourages them to listen to more tracks.
The more tracks the user listens to, the more advertisements they will also listen too between those tracks.
The more advertisements they hear, the more likely the user will hear about a product or service they like that is being advertised to them.
This in turn makes Spotify more valuable for advertisers and generate revenue.

Also, if Users find the tracks they hear but really don't like listening to ads, then they may pay a subscription to upgrade to a premium spotify account.
This is another revenue stream for Spotify.


Second process

https://api.spotify.com/v1/episodes/{id} is a spotify endpoint for receiving information about a particular episode.
Each episode has a unique Spotify ID and that must be passed through as a path parameter.

Spotify users can use this API endpoint to get details on and view a particular episode that they are interested in.

The input data to the artist top tracks API endpoint is 
- a valid access token (Header field)
- the spotify id of the episode (path parameter)
- market within which to look for the episode (query parameter)

The output data from this endpoint is a single episode object which matches the id within the path.
The episode object has the following data:

audio_preview_url -  A link to a 30 second preview of the episode
description - A description of the episode.
duration_ms - The episode length in milliseconds
explicit - Whether or not the episode has explicit content
name - 	The name of the episode
languages - A list of the languages used in the episode
release_date - The date the episode was first released
show - The show on which the episode belongs


Achieving Organisational Objectives:

This API endpoint helps users get details about and watch their favourite episodes. 
Additionally the API endpoint gives information about the show that the episode is from, so users can see the entire series of that show.
The episode also has description so users can learn what the episode is about without having to watch it.

The API helps users quickly find out what episode they want to watch as well as similar episode to watch once they have watched the first one.
This helps keep users engaged and continue watching episodes from a series.
The more users watch episodes, the more advertisements they will being watching during those episodes.
This makes Spotify more valujable to advertisers and generates higher advertisement revenue.
Also users may pay to have ads removed which comes with the premium user upgrade.
This also generates revenue for Spotify and covers the cost of licensing the show and developing the Spotify software.

# Question 7

As a way to improve the data model, Spotify could implement the following extension.

- Referal Discounts
If a Spotify user upgrades to a premium account, then they could be given a referral code to send to users friends.
If a friend of theirs also upgrades to a premium Spotify account and enters in the referral code then they can receive a 15% discount on their subscription.
Overall, this initiative can only improve the number of users who upgrade to premium. Some of the referred friends may have signed up anyway but overall it should improve revenue.
Even if the friend doesn't sign up, it serves as free word-of-mouth advertising for Spotify.
In addition, Spotify has very little expense increase per new premium user so referrals are more effective than compared to other products.
For example, selling an extra car has direct material, manufacturing and labor costs attached to it. The product cost per car is at least a few hundred dollars.
On the other hand, each new premium Spotify user has very little expense attached it. The cost of running the server and network stay the same.
Only when millions of new users are added, will the cost of running Spotify's servers and networks need to increase and that is relatively negligible compared to the additional revenue from new users.

Additional entity:
- referral_codes
The important property of a referral code is their status. Their status should say whether it has been offered to a friend or not, and whether it has been used.
Once a referral code is used, it should no longer be valid.
Also referral codes should be unique and not null. This way there are no ambiguity in the database table about the status of a referral code.

Additional relationships between entities:
One user can send out multiple referral codes but a referral code belongs to only one user.
Therefore referral_code_owner will be a foreign key in the referral_codes table
The foreign key referral_code_owner will reference the id field of the Users table.
Additionally a discount rate column will need to be added to the user entity so that Spotify knows to charge them at a
15% discount on the usual amount.

Additional inputs and processes:

Spotify will need to generate unique referral_codes and inserting a very large number of them into the referral_codes table.
Once a user decides to refer a friend then this input from the user will be used to trigger the process of assigning them a unique referral code
and changing the status of the referral code to pending. If the referred friend upgrades to premium then they have their user entity updated
with membership status of 'premium' and discount rate of 15%. The referral_code is now invalid and the referral_codes table must be updated.




