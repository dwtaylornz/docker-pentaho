Pentaho - Rapid Deployment with Docker 
=====================

##Pentaho
[Pentaho](http://www.pentaho.com/) addresses the barriers that block your organization's ability to get value from all your data.  The platform simplifies preparing and blending any data and includes a spectrum of tools to easily analyze, visualize, explore, report and predict. Open, embeddable and extensible, Pentaho is architected to ensure that each member of your team -- from developers to business users -- can easily translate data into value. 

##Docker
[Docker](http://www.docker.com/) is an open platform for developers and sysadmins to build, ship, and run distributed applications. Consisting of Docker Engine, a portable, lightweight runtime and packaging tool, and Docker Hub, a cloud service for sharing applications and automating workflows, Docker enables apps to be quickly assembled from components and eliminates the friction between development, QA, and production environments. As a result, IT can ship faster and run the same app, unchanged, on laptops, data center VMs, and any cloud.

###Running Pentaho with PostgreSQL
<pre>
git clone https://github.com/wmarinho/docker-postgresql.git
cd docker-postgresql
docker build -t wmarinho/postgresql:9.3 .
docker run --name postgresql -d -p 5432:5432 -d wmarinho/postgresql:9.3
</pre>
<pre>
docker run --name pentaho -d -p 8080:8080 -e PGHOST={postgres_hostname} wmarinho/pentaho-biserver:5.1-TRUNK
</pre>
<pre>
docker logs -f pentaho
</pre>

* Running an interactive container

`sudo docker run -i -t wmarinho/pentaho-biserver:5.1-TRUNK /bin/bash`

* Now we can easily run multiples containers and versions of Pentaho using only one server

##Building your image

###Clone and edit Dockerfile template

<pre>
sudo git clone https://github.com/wmarinho/docker-pentaho.git
cd docker-pentaho
sudo vi Dockerfile
sudo docker build -t myimage/pentaho:mytag .
sudo docker images
sudo docker run -p 8080:8080 -d myimage/pentaho:mytag
</pre>

Or run in interactive mode

<pre>
sudo docker run -p 8080:8080 -i -t myimage/pentaho:mytag /bin/bash
</pre>

