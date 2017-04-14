# Cloud Computing Concepts

* A single-site cloud (aka "datacenter") consists of
    * Compute nodes (grouped into racks)
    * Switches, connecting the racks
    * A network topology, e.g., hierarchical
    * Storage (backend) nodes connected to the network
    * Front-end for submitting jobs and receiving client requests
    * Software services

* A geographically distributed cloud consists of
    * Multiple such sites
    * Each site perhaps with a different structure and services

### Four Features New in Today’s Clouds  
1. __Massive scale__  
2. __On-demand access__: Pay-as-you-go, no upfront commitment.  
    * Anyone can access it  
3. __Data-intensive Nature__: What was MBs has now become TBs, PBs and XBs.  
    * Daily logs, forensics, Web data, etc.  
    * Humans have data numbness: Wikipedia (large) compress is only about 10 GB!  
4. __New Cloud Programming Paradigms__: MapReduce/Hadoop, NoSQL/Cassandra/MongoDB and many others.  
    * High in accessibility and ease of programmability  
    * Lots of open-source  

### Services Classification
* __HaaS__: Hardware as a Service
* __IaaS__: Infrastructure as a Service
    * Ex: Amazon Web Services (AWS: EC2 and S3), Eucalyptus, Rightscale, Microsoft Azure
* __PaaS__: Platform as a Service
    * Ex: Google’s AppEngine (Python, Java, Go)
* __SaaS__: Software as a Service
    * Ex: Google docs, MS Office on demand

### Cloud 
1. A cloud consists of  
    * Hundreds to thousands of machines in a datacenter (server side)  
    * Thousands to millions of machines accessing these services (client side)  
2. Servers communicate amongst one another  
3. Clients communicate with servers  
4. Clients also communicate with each other  

### Cloud is a Distributed System
* Servers communicate amongst one  
* Clients communicate with servers  
* Clients may also communicate with each other  
   * In peer-to-peer systems like BitTorrent  
