# Splunk Home Tour #
On this section we'll gonna talk about the Splunk Home and what you can find here. 
<img width="1647" height="438" alt="image" src="https://github.com/user-attachments/assets/b3f27586-a869-4bce-bc4a-1d8305a2a7ad" />

1) The Splunk Logo, can be clicked in every moment, it will return to the home page
2) Account Menu : Account settings and preferences
3) Settings : Configuration, Administration, Monitoring
4) Messages : System error messages
5) Activity Menu : Shortcut to jobs, Triggered Alerts
6) Apps Panel : List of installed and visible apps

<img width="1348" height="667" alt="image" src="https://github.com/user-attachments/assets/0996d60e-e253-4eeb-8033-2cbd352e6a3d" />

7) Explore Splunk Pannel
8) Dashboard : Imagine that you have a super important metric that you want as a primary dashboard you can have it there
9) Search History : Allows you to see recent searches that you made.

## Account Menu : Account settings and preferences ##
### Update your account settings ###
<img width="151" height="131" alt="image" src="https://github.com/user-attachments/assets/63c4864b-c613-42ee-a9c9-3619c78e2133" />
---
<img width="740" height="390" alt="image" src="https://github.com/user-attachments/assets/d6231ddb-ea13-4af4-88d6-6201bc712996" />

----
### Change Account Preferences ### 
<img width="152" height="132" alt="image" src="https://github.com/user-attachments/assets/8b3f1fb1-ee69-4c8a-a875-98839d253c16" />

When you'll go to this menu you'll have 2 important tabs : 
<img width="699" height="583" alt="image" src="https://github.com/user-attachments/assets/04f519a1-de34-4d7a-8740-c5924ebcc445" />

----

#### Global Menu :

<img width="699" height="583" alt="image" src="https://github.com/user-attachments/assets/5c7360ee-03a0-4eea-a788-2caa2bd2796d" />

  - Time Zone : You can choose your own timezone
  - Default App : Instead of spawning into the home all the time (Default App on the menu) you can choose an other app to spawn
  - Theme : You can set Splunk to Dark Mode


#### SPL Editor (Readability Settings) : #### 

<img width="701" height="687" alt="image" src="https://github.com/user-attachments/assets/68dd3cbb-39ad-49c4-ace8-c424480609cb" />

  - Configure Search Assistant : it's like a tool that assists you when you do searches
  - Choose a Theme : Only for the searchbar
  - Add line number : When you are writing long search you want it organized to see Line1, Line2, Line3
  - Search auto format : If for exemple when each time you type enter on a search it will do a second line with a | (pipe)
----

Question : Which of the following is true about user account settings and preferences?
-> Full Name, Time Zone, Default APpp can be defined by clicking the login name in Splunk bar.


## Settings ## 

<img width="609" height="572" alt="image" src="https://github.com/user-attachments/assets/bac4503c-5478-4463-b20e-78d6d2d1e15a" />

1) Knowledge tab :
   - Create and manage knwoledge objects : **Knowledge Objects** are tools that you can use for discover and analyze aspects of data that you ingest like (reports, alerts, models of data, event types, tags, fields)...
   - It's the major menu item available to user and power roles (because they won't see system menu, data, distribuded env, user and auth
  
2) System Menu :
   - System settingsµ
   - Licensing
   - Restart Splunk from GUI

3) Data Menu :
   - Create indexes and configure Data inputs
   - Configure data forwarding and receiving (ex: if you use this instance as a heavy forwarders, you can receive data, doing modification as parsing... And send the data to an other instance for indexing.
  
4) Distributed Environment :
   - Frowarder Management Interface : imagine that you have splunk forwarders on multiple machines and you wanted to manage them from the UI you'll use this menu.
   - Indexer Clustering : For high availability you can configure a cluster of index, to ensure that if an indexer is down an other one will take the lead.
   - Distribued Search : When a search head is talking to multiple indexers in the backend.
  
5) Users and authentication :
   - Create and Manage users.
   - Configure authentication types.

<img width="611" height="572" alt="image" src="https://github.com/user-attachments/assets/fe5cf5ed-9682-4aa3-9c42-339ba4b20fbb" />

6) You can add data
7) Explore your data
8) Monitoring Console : if something is going wrong, it will be displayed on this dashboard (based on internal indexes within Splunk).
