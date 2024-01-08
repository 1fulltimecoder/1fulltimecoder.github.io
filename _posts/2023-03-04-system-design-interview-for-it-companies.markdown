---
layout: post
title: "System design interview for IT companies"
description: "System design interview for IT companies"
categories: [System Design]
tags: [blog, system-design]
published: true
sitemap: true
pin: false
---

![system development life cycle](/assets/img/system-design/systemcycle.png)

> How to prepare system design questions for an IT company

Original source and Credit: [github.com/checkcheckzz/system-design-interview](https://github.com/checkcheckzz/system-design-interview)

---

System design is a very broad topic. Even a software engineer with many years of working experience at a top IT company may not be an expert on system design. If you want to become an expert, you need to read many books, articles, and solve real large scale system design problems.

This repository only teaches you how to handle the system design interview with a systematic approach in a short time. You can dive into each topic if you have time. Of course, welcome to add your thoughts!


### System Design Interview Tips:

**Clarify the constraints and identify the user cases**

Spend a few minutes questioning the interviewer and agreeing on the scope of the system.
Remember to make sure you know all the requirements the interviewer didn't tell you about in the beginning.

User cases indicate the main functions of the system, and constraints list the scale of the system such as requests 
per second, requests types, data written per second, data read per second.

**High-level architecture design**

Sketch the important components and the connections between them, but don't go into some details. 
Usually, a scalable system includes webserver (load balancer), service (service partition), database (primary/secondary database cluster plug cache).
 
**Component design**

For each component, you need to write the specific APIs for each component. You may need to finish
the detailed OOD design for a particular function. You may also need to design the database schema for the database.

###  Basic Knowledge about System Design:

Here are some articles about system design related topics.  

* [The Anatomy Of A System Design Interview](https://blog.pramp.com/system-design-interview-process-e91aae2dbe83)
* [How to Succeed in a System Design Interview](https://blog.pramp.com/how-to-succeed-in-a-system-design-interview-27b35de0df26)
* [How to Rock a Systems Design Interview](https://www.palantir.com/2011/10/how-to-rock-a-systems-design-interview/)
* [System Interview](https://www.hiredintech.com/app#system-design)
* [Scalability for Dummies](https://www.lecloud.net/tagged/scalability)
* [Scalable Web Architecture and Distributed Systems](https://www.aosabook.org/en/distsys.html)
* [Numbers Everyone Should Know](https://everythingisdata.wordpress.com/2009/10/17/numbers-everyone-should-know/)
* [Fallacies of distributed systems](https://pages.cs.wisc.edu/~zuyu/files/fallacies.pdf)
* [Scalable System Design Patterns](https://horicky.blogspot.com/2010/10/scalable-system-design-patterns.html)
* [Introduction to Architecting Systems for Scale](https://lethain.com/introduction-to-architecting-systems-for-scale/)
* [Transactions Across Datacenters](https://snarfed.org/transactions_across_datacenters_io.html)
* [A Plain English Introduction to CAP Theorem](https://ksat.me/a-plain-english-introduction-to-cap-theorem)
* [The CAP FAQ](https://github.com/henryr/cap-faq)
* [Paxos Made Simple](https://research.microsoft.com/en-us/um/people/lamport/pubs/paxos-simple.pdf)
* [Consistent Hashing](https://www.tom-e-white.com/2007/11/consistent-hashing.html)
* [NOSQL Patterns](https://horicky.blogspot.com/2009/11/nosql-patterns.html)
* [Scalability, Availability & Stability Patterns](https://www.slideshare.net/jboner/scalability-availability-stability-patterns)

Of course, if you want to dive into system related topics, here is a good collection of reading list about [services-engineering](https://github.com/mmcgrana/services-engineering), and
a good collection of material about [distributed systems](https://dancres.github.io/Pages/).

### Company Engineering Blogs:

If you are going to have an onsite with a company, you should read their engineering blog. 

* [High Scalability](https://highscalability.com/)
* [The GitHub Blog](https://github.com/blog/category/engineering)
* [Engineering at Quora](https://engineering.quora.com/)
* [Yelp Engineering Blog](https://engineeringblog.yelp.com/)
* [Twitter Engineering](https://engineering.twitter.com/)
* [Facebook Engineering](https://www.facebook.com/Engineering)
* [Yammer Engineering](https://eng.yammer.com/blog/)
* [Etsy Code as Craft](https://codeascraft.com/)
* [Foursquare Engineering Blog](https://engineering.foursquare.com/)
* [Airbnb Engineering](https://medium.com/airbnb-engineering)
* [WebEngage Engineering Blog](https://engineering.webengage.com/)
* [LinkedIn Engineering](https://engineering.linkedin.com/blog)
* [The Netflix Tech Blog](https://techblog.netflix.com/)
* [BankSimple Simple Blog](https://www.simple.com/engineering/)
* [Square The Corner](https://corner.squareup.com/)
* [SoundCloud Backstage Blog](https://developers.soundcloud.com/blog/)
* [Flickr Code](https://code.flickr.net/)
* [Instagram Engineering](https://instagram-engineering.tumblr.com/)
* [Dropbox Tech Blog](https://tech.dropbox.com/)
* [Cloudera Developer Blog](https://blog.cloudera.com/)
* [Bandcamp Tech](https://bandcamptech.wordpress.com/)
* [Oyster Tech Blog](https://tech.oyster.com/)
* [THE REDDIT BLOG](https://www.redditblog.com/)
* [Groupon Engineering Blog](https://engineering.groupon.com/)
* [Songkick Technology Blog](https://devblog.songkick.com/)
* [Google AI Blog](https://ai.googleblog.com/)
* [Google Developers Blog](https://developers.googleblog.com/)
* [Pinterest Engineering Blog](https://engineering.pinterest.com/)
* [Twilio Engineering Blog](https://www.twilio.com/engineering)
* [Bitly Engineering Blog](https://word.bitly.com/)
* [Uber Engineering Blog ](https://eng.uber.com/)
* [Godaddy Engineering](https://engineering.godaddy.com/)
* [Splunk Blog](https://blogs.splunk.com/)
* [Coursera Engineering Blog](https://building.coursera.org/)
* [PayPal Engineering Blog](https://www.paypal-engineering.com/)
* [Nextdoor Engineering Blog](https://engblog.nextdoor.com/)
* [Booking.com Development Blog](https://blog.booking.com/)
* [Microsoft Engineering Blog](https://engineering.microsoft.com/)
* [Scalyr Engineering Blog](https://blog.scalyr.com/)
* [Myntra Engineering Blog](https://medium.com/myntra-engineering)
* [Fastly Blog](https://www.fastly.com/blog/)
* [AWS Architecture Blog](https://aws.amazon.com/blogs/architecture/)
* [Lyft Engineering Blog](https://eng.lyft.com/)
* [Wish Engineering](https://medium.com/wish-engineering)
* [Doordash Engineering](https://doordash.engineering/)
* [SnowFlake Blog](https://community.snowflake.com/s/blog) 
* [Palantir Blog](https://medium.com/palantir/tech/home)

### Products and Systems:

The following papers/articles/slides can help you to understand the general design idea of different real products and systems. 

* [MapReduce: Simplified Data Processing on Large Clusters](https://static.googleusercontent.com/media/research.google.com/zh-CN/us/archive/mapreduce-osdi04.pdf)
* [Bigtable: A Distributed Storage System for Structured Data](https://www.read.seas.harvard.edu/~kohler/class/cs239-w08/chang06bigtable.pdf)
* [The Google File System](https://static.googleusercontent.com/media/research.google.com/zh-CN/us/archive/gfs-sosp2003.pdf)
* [The Chubby lock service for loosely-coupled distributed systems](https://static.googleusercontent.com/external_content/untrusted_dlcp/research.google.com/en/us/archive/chubby-osdi06.pdf)
* [Dynamo: Amazon's Highly Available Key-value Store](https://www.read.seas.harvard.edu/~kohler/class/cs239-w08/decandia07dynamo.pdf)
* [Introduction to Memcached](https://www.slideshare.net/oemebamo/introduction-to-memcached)
* [Cassandra Introduction Features](https://www.slideshare.net/planetcassandra/cassandra-introduction-features-30103666)
* [Introduction to HBase](https://www.slideshare.net/alexbaranau/intro-to-hbase)
* [Introduction to MongoDB](https://www.slideshare.net/mdirolf/introduction-to-mongodb)
* [Introduction to Redis](https://www.slideshare.net/dvirsky/introduction-to-redis)
* [Storm](https://www.slideshare.net/previa/storm-16094009)
* [Introduction to Zookeeper](https://www.slideshare.net/sauravhaloi/introduction-to-apache-zookeeper)
* [Kafka](https://www.slideshare.net/mumrah/kafka-talk-tri-hug)
* [YouTube Architecture](https://highscalability.com/youtube-architecture)
* [Scaling Pinterest](https://highscalability.com/blog/2013/4/15/scaling-pinterest-from-0-to-10s-of-billions-of-page-views-a.html)
* [Google Architecture](https://highscalability.com/google-architecture)
* [Scaling Twitter](https://highscalability.com/scaling-twitter-making-twitter-10000-percent-faster)
* [The WhatsApp Architecture](https://highscalability.com/blog/2014/2/26/the-whatsapp-architecture-facebook-bought-for-19-billion.html)
* [Flickr Architecture](https://highscalability.com/flickr-architecture)
* [Amazon Architecture](https://highscalability.com/amazon-architecture)
* [Stack Overflow Architecture](https://highscalability.com/blog/2009/8/5/stack-overflow-architecture.html)
* [Pinterest Architecture](https://highscalability.com/blog/2012/5/21/pinterest-architecture-update-18-million-visitors-10x-growth.html)
* [Tumblr Architecture](https://highscalability.com/blog/2012/2/13/tumblr-architecture-15-billion-page-views-a-month-and-harder.html)
* [Instagram Architecture](https://highscalability.com/blog/2011/12/6/instagram-architecture-14-million-users-terabytes-of-photos.html)
* [TripAdvisor Architecture](https://highscalability.com/blog/2011/6/27/tripadvisor-architecture-40m-visitors-200m-dynamic-page-view.html)
* [Scaling Mailbox](https://highscalability.com/blog/2013/6/18/scaling-mailbox-from-0-to-one-million-users-in-6-weeks-and-1.html)
* [Salesforce Architecture ](https://highscalability.com/blog/2013/9/23/salesforce-architecture-how-they-handle-13-billion-transacti.html)
* [ESPN Architecture](https://highscalability.com/blog/2013/11/4/espns-architecture-at-scale-operating-at-100000-duh-nuh-nuhs.html)
* [Uber Architecture](https://highscalability.com/blog/2015/9/14/how-uber-scales-their-real-time-market-platform.html)
* [DropBox Design](https://www.youtube.com/watch?v=PE4gwstWhmc)
* [Splunk Architecture](https://www.splunk.com/view/SP-CAAABF9)

### Hot Questions and Reference:

There are some good references for each question. The references here are slides and articles. 

**Design a CDN network**  
Reference:  
* [Globally Distributed Content Delivery](https://kilthub.cmu.edu/articles/journal_contribution/Globally_distributed_content_delivery/6605972)

**Design a Google document system**  
Reference:  
* [google-mobwrite](https://code.google.com/p/google-mobwrite/)
* [Differential Synchronization](https://neil.fraser.name/writing/sync/)

**Design a random ID generation system**  
Reference: 
* [Announcing Snowflake](https://blog.twitter.com/2010/announcing-snowflake) 
* [snowflake](https://github.com/twitter/snowflake/)

**Design a key-value database**  
Reference:   
* [Introduction to Redis](https://www.slideshare.net/dvirsky/introduction-to-redis)

**Design the Facebook news feed function**   
Reference:   
* [What are best practices for building something like a News Feed?](https://www.quora.com/What-are-best-practices-for-building-something-like-a-News-Feed) 
* [What are the scaling issues to keep in mind while developing a social network feed?](https://www.quora.com/Activity-Streams/What-are-the-scaling-issues-to-keep-in-mind-while-developing-a-social-network-feed) 
* [Activity Feeds Architecture](https://www.slideshare.net/danmckinley/etsy-activity-feeds-architecture)

**Design the Facebook timeline function**   
Reference: 
* [Building Timeline](https://www.facebook.com/note.php?note_id=10150468255628920) 
* [Facebook Timeline](https://highscalability.com/blog/2012/1/23/facebook-timeline-brought-to-you-by-the-power-of-denormaliza.html)

**Design a function to return the top k requests during past time interval**   
Reference:  
* [Efficient Computation of Frequent and Top-k Elements in Data Streams](https://www.cse.ust.hk/~raywong/comp5331/References/EfficientComputationOfFrequentAndTop-kElementsInDataStreams.pdf)
* [An Optimal Strategy for Monitoring Top-k Queries in Streaming Windows](https://davis.wpi.edu/xmdv/docs/EDBT11-diyang.pdf)

**Design an online multiplayer card game**   
Reference:  
* [How to Create an Asynchronous Multiplayer Game](https://www.indieflashblog.com/how-to-create-an-asynchronous-multiplayer-game.html)   
* [How to Create an Asynchronous Multiplayer Game Part 2: Saving the Game State to Online Database](https://www.indieflashblog.com/how-to-create-async-part2.html)  
* [How to Create an Asynchronous Multiplayer Game Part 3: Loading Games from the Database](https://www.indieflashblog.com/how-to-create-async-part3.html)  
* [How to Create an Asynchronous Multiplayer Game Part 4: Matchmaking](https://www.indieflashblog.com/how-to-create-async-part4-html.html#comment-4447)  
* [Real Time Multiplayer in HTML5](https://buildnewgames.com/real-time-multiplayer/)  

**Design a graph search function**   
Reference:   
* [Building out the infrastructure for Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-building-out-the-infrastructure-for-graph-search/10151347573598920)
* [Indexing and ranking in Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-indexing-and-ranking-in-graph-search/10151361720763920) 
* [The natural language interface of Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-the-natural-language-interface-of-graph-search/10151432733048920) and [Erlang at Facebook](https://www.erlang-factory.com/upload/presentations/31/EugeneLetuchy-ErlangatFacebook.pdf)

**Design a picture sharing system**   
Reference:   
* [Flickr Architecture](https://highscalability.com/flickr-architecture) 
* [Instagram Architecture](https://highscalability.com/blog/2011/12/6/instagram-architecture-14-million-users-terabytes-of-photos.html)

**Design a search engine**   
Reference:  
* [How would you implement Google Search?](https://programmers.stackexchange.com/questions/38324/interview-question-how-would-you-implement-google-search)  
* [Implementing Search Engines](https://www.ardendertat.com/2012/01/11/implementing-search-engines/)

**Design a recommendation system**  
Reference:  
* [Hulu’s Recommendation System](https://tech.hulu.com/blog/2011/09/19/recommendation-system.html)  
* [Recommender Systems](https://ijcai13.org/files/tutorial_slides/td3.pdf)

**Design a tinyurl system**    
Reference: 
* [System Design for Big Data-tinyurl](https://n00tc0d3r.blogspot.com/) 
* [URL Shortener API](https://developers.google.com/url-shortener/?csw=1)

**Design a garbage collection system**    
Reference:   
* [Baby's First Garbage Collector](https://journal.stuffwithstuff.com/2013/12/08/babys-first-garbage-collector/)
 
**Design a scalable web crawling system**    
Reference:  
* [How can I build a web crawler from scratch?](https://www.quora.com/How-can-I-build-a-web-crawler-from-scratch)

**Design the Facebook chat function**    
Reference:   
* [Erlang at Facebook](https://www.erlang-factory.com/upload/presentations/31/EugeneLetuchy-ErlangatFacebook.pdf)  
* [Facebook Chat](https://www.facebook.com/note.php?note_id=14218138919&id=9445547199&index=0)

**Design a trending topic system**    
Reference:  
* [Implementing Real-Time Trending Topics With a Distributed Rolling Count Algorithm in Storm](https://www.michael-noll.com/blog/2013/01/18/implementing-real-time-trending-topics-in-storm/)   
* [Early detection of Twitter trends explained](https://snikolov.wordpress.com/2012/11/14/early-detection-of-twitter-trends/)
 
**Design a cache system**    
Reference:   
* [Introduction to Memcached](https://www.slideshare.net/oemebamo/introduction-to-memcached)

### Good Books:

* [Big Data: Principles and best practices of scalable realtime data systems](https://www.amazon.com/Big-Data-Principles-practices-scalable/dp/1617290343)
* [Real-Time Analytics: Techniques to Analyze and Visualize Streaming Data](https://www.amazon.com/Real-Time-Analytics-Techniques-Visualize-Streaming/dp/1118837916)
* [Building Microservices: Designing Fine-Grained Systems](https://www.amazon.com/Building-Microservices-Sam-Newman/dp/1491950358)
* [Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321)

###  Object Oriented Design:

#### Tips for OOD Interview

**Clarify the scenario, write out user cases**

Use case is a description of sequences of events that, taken together, lead to a system doing something useful. Who is going to use it and how they are going to use it. The system may be very simple or very complicated.

Special system requirements such as multi-threading, read or write oriented.

**Define objects**

Map identity to class: one scenario for one class, each core object in this scenario for one class.

Consider the relationships among classes: certain class must have unique instance, one object has many other objects (composition), one object is another object (inheritance).

Identify attributes for each class: change noun to variable and action to methods.

Use design patterns such that it can be reused in multiple applications.

#### Useful Websites

* [101 Design Patterns & Tips for Developers](https://sourcemaking.com/design-patterns-and-tips)



