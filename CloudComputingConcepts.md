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
