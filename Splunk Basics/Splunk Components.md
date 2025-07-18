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
Hot buckets are buckets in which you write actively the data when the indexation step, the indexation data are written inside the hot buckets. These buckets have some time and size constraints



