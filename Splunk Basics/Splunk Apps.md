# What is Splunk Apps ? #
Splunk Apps are custom solutions that allow you to extend the functionality of the Splunk plateform


## Why using Splunk Apps ? ##

When Splunk is installed let's imagine that you have some cloud infrastructures or any security devices, Splunk won't be able to index these data with his basics Apps 

<img width="728" height="378" alt="{917DE8C9-50A0-4A99-944E-81733A332944}" src="https://github.com/user-attachments/assets/49c6db8b-d05e-4214-b1e4-9fa82c9aeb05" />

## Some use cases of Splunk Apps
- Custom configurations to index data :
  - For exemple constructors of equipments that have some specifics data sources with specific formats can be collaborate with Splunk to creates Apps that you can install to index the data into Splunk, that have configruation to retrive the data for you.
  - Some of them have configurations into Splunk for knowledge objects that can be used to do fields extraction

- Seperates workspaces for different use cases to co-exist on Single Splunk Instance
  - Imagine that if you have multiple departements in your company that are using the same deployment, will you collect every departements logs into one app ?
    -> no it will be very big to ingest and not relevant for the others departements
    -> you can create multiple apps that will have specific permissions that won't allow other departements to read data.

## Collections of : ## 
Apps are collections of 

- Data Inputs
  -> Data inputs mean that a portion of the data will allow you to be able to index data

- UI Elements
  -> Some of them have menu, dashboards, UI elements are User Interface elements that will allows you to use the application easier.

  Knowledge Objects
  -> Some Apps have knwoledge objects that can helps you do to fields extraction and sometimes create dashboards for you.

## How to view and manage Splunk Apps ? ##
<img width="300" height="392" alt="image" src="https://github.com/user-attachments/assets/72349da7-3710-41ff-b864-981a03720536" />

On the Second Number it shows application that are installed and visible on your Splunk instance / deployment

/!\ Sometimes apps are installed but not visible !

If you want to manage apps, you'll need to go on the Manage App button (1), it will show you the complete list of all applications installed on your instance / deployment

<img width="1643" height="730" alt="{79783AE1-790E-45F6-9035-44407B8F4B08}" src="https://github.com/user-attachments/assets/cc8763b3-18cb-4efe-a90a-6233c0520547" />


Question : A Collection of items containing things such as data inputs, UI elements, and knwoledge objects is know as 
-> An App

## How to find apps for Splunk 

1) You can directly find application with the manage app + browse more apps
2) You can download them directly from Splunk Base Website.

### Default Apps in Splunk ###
- Home Page (it's a default application)
- Search & reporting

Question : Which is a default app for Splunk Enterprise ? 
-> Search & reporting
