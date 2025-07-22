# Overview of Splunk Components #

You can install Splunk on different type of host like :
- Physical Machine
- Virtual Machine
- Container

Once you downloaded Splunk and installed it on a machine, each machine contains a Splunk Instance, when these instance are installed you need to configure them.

# Components Types #

**Processing Components** : 
- Indexers
- Forwarders
- Search Heads

**Management Components** : 
- Deployment Server
- Indexer Cluster Manager
- Search Head Cluster Deployer
- License Manager
- Monitoring Console

Note : Each instance can be configured into one or more Splunk Components, for exemple the trial version of Splunk is configured to be an indexer and a search head

-> Question : Three basic components of Splunk are ? 
Answer : Forwarder, Indexer, Search head


## Splunk Components - Forwarder ##

**To send data** to Splunk, you need to use the Splunk component called **Forwarders**
1) You need to install forwarders on Host machines
2) configure the forwarders to collect and send data to Splunk for indexing

Note : It's the primary way to send data to splunk (other methods exists such as HTTP, event collector)...

When data are sent and available in Splunk it means that Splunk is ready to use

### Two Types of Forwarders ###
- **Universal Forwarders** : it's a seperate executable with reduced functionnality
  - "Separate" because his main function is to collect and send data

- **Heavy Forwarders** :
  - Configured from full Splunk enterprise installation (When you install Splunk Enterprise on an instance you'll configure it as a heavy forwarders), it's not like an agent (a seperated .exe) as Universal forwarders).
  - Can parse and make changes to data before forwarding
  

---------------------------------------------------------------------------------------------------------

Question : Which of the following Splunk components typically resides on machines where data originates ? 
- Answer : Forwarders

Question : Which of the following Splunk can perform log filtering / parsing ? 
- Answer : Heavy Forwarders


## Splunk Components - Indexers ##

When data comes from the host and enters in splunk, the component which retrieve the data and will processing the data is called an indexer. Various things can happen when indexers will process the data. 

- First of all the indexer will parse the data, that will allows him to split data into separate events. 
If you remember, the heavy forwarder can parse the data but not the Universal Forwarders, so when indexer will receive data from Universal forwarder he'll need to split data into individual events.

- Indexer can assign metadata
Metadas are fields which describes the data that is comming into Splunk.
When you have data that are coming into splunk you want to know which host is sending data so you'll assign a host value to the data (it's a metadata field).
Of course, you can attribute a souce and a sourcetype. The source can be a folder directory were the data cames from. Sourcetype is the type of the data, it describes which type of data it is.

You can extract timestamp in index time, you can perform a configuration to attribute timestamp to events, it's happening during the indexing.

When the data finished to be processed, the processed data will be write to disks. So to be precise you write data into references on the disks that it is called **Indexes**

-> The **indexer** processes and writes incoming data into repositories known as **indexes**

Indexes on Disk Exemples : 
- Main : when you install Splunk Enterprise and you did not specify any index, every data will be placed into this index.
  - The **main** index is the primary index.
    
- ' _ internal : Indexes that begins with " _ " are designed to be internal logs related to Splunk (like errors in Splunk...).
- Custom index : It's possible to define custommised index

### Index Structure ### 
When you dive into index, you'll find repositories with initial files which contain the index data -> called **Buckets**. So when you indexing data into Splunk, these data are in fact written inside buckets.
**Buckets are repositories containing files with the indexed data**

Two types of buckets that are in the home path: 
- Hot Bucket
- Warm bucket

#### Hot Buckets #### 
Home path (need explanation)

Hot buckets are buckets in which you write actively the data when the indexation step, the indexation data are written inside the hot buckets. These buckets have some time and size constraints
You can say that when these datas hit these size or when the bucket hit this size or when he doesn't hit this size in a certain time, then move that bucket to a warm bucket.

In this case it's call roll over, you roll over a hot bucket to a warm bucket

#### Cold Path ####

cold bucket (need explanation)


#### Important note ####
When you are indexing data into splunk you can only write datas into a hot bucket but when you are searching, you can do search into Hot / Warm and cold bucket

How many time can you save data into cold bucket -> unlimited, cold bucket does not have size constraints (of course it depends how many storage space do you have or if internal company policies retains the data ).

Imagine that you impose a data limitation of six months, if you reach this limit of time your datas are called "Frozen Data", two types of scenario exists :
- Delete all the data
- Archive the data (save the data into an external storage).

In the future, if you need these data again, you'll archive these data into a third path called the 'Thawed Path', when the datas are inside this path, you can do search on it.

### What if your indexer is broken ###
In the context of your company needs data availability, you'll need to setup an indexer cluster. 

Indexer Cluster : 
- Group indexers together to provide data replication
- Cluster Manager coordinates replication activities and manages the cluster.

For exemple indexer 1 will replicate his data to the indexer 2 and indexer 3

---------------------------------------------------------------

Questions : 
Which Splunk component transforms raw data into events and distributes the results to an index ? 
-> Indexer

Which component of Splunk is primarily responsible for saving data ? 
-> Indexer


## Splunk Components - Search Head ##

Now that data are available on the disk, how can we search them ?

For searching the data we need a search head. Search head is a component in which user will connect to do searches data indexed into splunk

Search Head : 
- Search management and presentation for results retrieved from indexers.
- Distributes search requests to the indexers and merges results back to the user.

### What if the search head is broken ? ###

Same process as the indexer, you can create a search head cluster

Search Head Cluster :
- /!\ Group search heads with identical configuration.
- Search requests from users are balanced across SH group (for exemple is important to use a load balancer to divide the search work with for ex 5 search heads).
- Managed by Cluster Captain : When you create a search head cluster one of the search head will act as a Cluster Captain
  - Coordinates job scheduling among SH members
  - Coordinates replication activities (data are replicatied across the search heads to make sure that all of them get a identical configuration).
- Search head deployer :
  - It's a management component, the role is to distributes apps and other configurations to Cluster members. Imagine that you have a new application to install on all the search head, you can deploy this app to each search head using the Search Head Deployer.

Difference between Cluster Captain and a Cluster Manager : 
The Cluster manager is a seperate splunk component but the Cluster Captain is not. Cluster Captain is just one of the search head that play the role of the captain and coordinates job scheduling among SH members.

---------------------------------------------------------------------

Questions : 
Which component of Splunk let us write SPL queries to find the required data ? 
-> Search Head

## Deployment Server ## 
Imagine that you deployed Splunk, imagine that your needs begin to grow and your deployment grow, multiple Search head clusters, multiple Indexer Cluster and so on... If you need to manage every servers every search heads it will be a big loss of data. So then you'll need a Deployment Server ! 

The rôle of the Deployment server is to distribute the contents, configurations, apps to other groups of Splunk Instances (Deployment clients)

The clients can be indexers that are not in part of a cluster, it's not necessary to clusterise to apply configuration on an index, search head or other

Distributed content is known colletively as deployment apps
Each time that you see deployment application mentionned, it's related to a group of contents that you want to deploy on your instances

Mostly used to distribute apps to Splunk Forwarders

Think about : How many host you'll gona have compared of the number of instances that you have in Splunk himself like indexers or search heads.
-> you'll have thousand of host and this number will continue to grow, you won't be able to update every Simple forwarders installed on your hosts, that's why we use deployment servers to do these updates with the deployment apps
