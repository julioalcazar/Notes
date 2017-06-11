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

### Distributed System  
A distributed system is a model in which components located on networked computers communicate and coordinate their actions by passing messages. The components interact with each other in order to achieve a common goal. Three significant characteristics of distributed systems are:
  * concurrency of components  
  * lack of a global clock 
  * independent failure of components

### MapReduce  
A MapReduce program is composed of a Map() procedure (method) that performs filtering and sorting (such as sorting students by first name into queues, one queue for each name) and a Reduce() method that performs a summary operation (such as counting the number of students in each queue, yielding name frequencies). The "MapReduce System" (also called "infrastructure" or "framework") orchestrates the processing by marshalling the distributed servers, running the various tasks in parallel, managing all communications and data transfers between the various parts of the system, and providing for redundancy and fault tolerance.

### MapReduce Scheduler  
This will focuse on YARN Scheduler (Yet Another Resource Negotiator)
![YARN Scheduler](https://github.com/amroibrahim/Notes/blob/master/Images/CloudComputingConcepts/YARN_Scheduler.png)
* Resource Manger  
   * Global resource shceduler  
   * Hierarchical queues  
   * Application managment  
* Node Manager  
   * Per-machine agent  
   * Manages the life-cycle of container  
   * container resource monitoring  
* Application Master  
   * Per-application  
   * Manages application scheduling and task execution  
   * E.g. MapReduce Application Master  

### Fault Tolerance
* Server failure
   * Heart beats 
      * NM heartbeats to RM  
      * NM keeps track of each task running at its server  
      * AM heartbeats to RM  
   * RM failure
      * use old checkpoint and bring up secondary RM
* Slow Servers
   * Straggelers (slow nodes)
      * Keep track of progress
      * replicate execution of straggler trask (speculative execution)
* Locality

## Protocols  
### Multicast  
* Challenges  
   * Fault tolerant  
   * Scalability  

* Implementation  
   * Centralized: A node send data to all other noded on network (hight overhead)  
   * Tree-Based: Nodes send data to its child node only (a tree hierarchical nodes connection need to be built)  
   * Gossipe: A node picks a random P number of nodes and send them a copy of the gossip. Infecting other nodes in group  
      * __Push__: Once you have a multicast message, you start gossiping about it.
      * __Pull__: Periodically poll a few randomly selected processes for new multicast messages the you haven't received
      * __Hybrid Push-Pull__

## Failure Detection
What could g o wrong without a faliur detector?
* Data lose
* Data inconsistency (poor service quality)

### Failure Types
* Crash-stop/Fail-stop
* Crash-recovery

### Group Membership Service
A group membership service should give surviving processes a consistent view of which nodes that are alive.  

### Distributed Failure Detectors: Desirable Properties
* Completeness: Each failure is detected
* Accuracy: there is no mistaken detection
* Speed: Time to first detection of a faliure
* Scale: Equal load on each member, and Network Message load.

### Failure Detectors
* Centralized Heartbeating
* Ring Heartbeating
* All to All Heartbeating
* Swim Failure Detector Protocol

### Gossip Style Heartbeating (variant of All to All Heartbeating)
* Protocol
   * Periodically gossip their membership list
   * On receipt, the local list membership list is updated
   * We must label the local time, since this is asynchronous system
   * If the heartbeat has not increased for more than T_failed seconds, the member considered as failed.
   * After T_cleanup seconds, it will be deleted from the list.

### Swim Failure Detector Protocol
* Protocol
   * Send a direct ping message.
   * If no ACK send and inderect ping message.
   * If no ACK mark the target (PJ) as fail

### P2P Systems  
* Napster
   * Has Servers and Peers (servers store index of which clinet has has which files, Peers has the actule files)
   * Servers uses Ternary tree to index information
* Gnutella  
   * No Servers  
   * Client act as servers too are called servants  
   * 5 Message Types
      * Query (search)  
      * QueryHit (response to query)  
      * Ping (to probe network for other peers)  
      * Pong (reply to ping, sontains address of another peer)  
      * Push (used to initiate file transfer)  
* FastTrack
   * Kazaa, KazaaLite  
   * Similar to Gnutella, but has some nodes act as super nodes  
   * Super nodes store directories information  
   * User has reputation, and depends on upload.  
* BitTorrent  
   * Tracker per file  
   * Peers are seeds if they have full file  
   * Peers are leecher if they have parts of the file  
   * Peers uses Local Rarest First Policy  
* Chord
   * Uses DHT
   * Peer Pointers (Successors) Peer know the colockwise successors in a ring topology.  
   * Peer Pointers (Finger Tables) Peer
* Pastry
   * Each node knows its successors and predecessors, multiple successors, multiple predecessors
   * Routing Tables use prefix matching (prefix routing) O(log (N))
   
### DHT (Distributed Hash Table)
* Performance Concerns
   * Load Balancing
   * Fault-tolerance
   * Efficiency of lookups and inserts
   * Locality
   
