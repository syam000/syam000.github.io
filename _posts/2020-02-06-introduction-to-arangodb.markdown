---
layout: post
title:  "An introduction to ArangoDB"
date:   2020-02-06 12:43:16 +0800
categories: graph database
---

While I was working on a way finding solution, I had to search for a graph database. After some research I have found out few as below:

* https://neo4j.com/ 
* https://www.arangodb.com/
* https://orientdb.com/
And the list goes on

As one of the best in the market, I have started with neo-4j and then I realised that if I wanna use it in a commercial project, I have to pay a huge license fee 😑. In my opinion neo-4j is one of the best graph database with developer friendly tools and documentation. But the price was not something I could afford. Thus I continued my search and found ArangoDB 😄🕺.

Before this project I never heard of this platform at all. But once started learning it was quite easy to set up and prove the basic concepts. Also price wise suitable for me too; its an open source apache 2.0 distribution.

I have learned a lot while working with ArangoDB, so I thought write a simple blog on this to help others who may have to use similar platforms in their projects.

Lets jump in…

What is ArangoDB?
Its an open source multi-model database for graph , document , key-value and search needs. In other words it has the features of Neo4J / Couch DB and Cassandra DB. Thats sounds something interesting, isn’t it.

Which are the operating systems it supports?
Basically every where - Windows / Mac / Linux / Kubernetes & Docker. 😎

How about drivers for programming languages ?
Almost all the modern main stream languages - Java, JS, Go, Python, R , Rust & Elixir 🤠

How to install?
I am using Mac, so I decided to install via Homebrew ❤️ and also installed the cli tools.

{% highlight zsh %}
	brew install arangodb
{% endhighlight %}

Thats it 🤩 you have got the arangodb on you mac if everything goes well.

I have also installed the cli tools to make it easier for me. This is not needed if you don’t want this extra app on your machine.

Start the server

I have started the server using following command.

{% highlight zsh %}
	sudo brew services start arangodb
{% endhighlight %}

If you want to stop at any time, you may use the following:

{% highlight zsh %}
	sudo brew services stop arangodb
{% endhighlight %}

Lets play via web user interface

Now you have started the arangodb server, we can start accessing it via either arango web user interface or arango shell. Here I am gonna show how to use the arango web interface as its more visual. 🤓

Open your favourite browser and type in the following url

http://localhost:8529/

Boom!🤘

![Web interface landing screen](/assets/arango_db_post_1.png)

Initially there won’t be any password for the ‘root’ user, so you can login first with ‘root’ as username and empty password. If you face any issue, you can reset the password following these steps here.

Then you will be prompted to select the database.

![Select database screen](/assets/arango_db_post_2.png)

Now you will be taken to the dashboard screen.

![Dashboard](/assets/arango_db_post_3.png)

Sweet!!! 💪💪💪

Finally you have setup the arangodb on your machine.

For more information click here.

Hope it useful for someone 😃

I will write another tutorial on some practical exercises using arangodb and shortest path finding solution with nodejs.

Till then see ya! 🤘



