The process of indexation time in splunk is devided in 3 phases. 

- Input Phase
  - Handled at the source of the data :
    - From Universal Forwarder
    - From Heavy Forwarder
  - Data sources are open and read (data from files or network sources)
  - Configuration are applied to entire streams (when you read data from sources it's only some blocs of informations because at this time data are not parsed).
  - Data sent out for indexing

- Parsing Phase
  - Handled at :
    - Indexer
    - Havy Forwarder
  - Data broken up into events.
  - Extract default metadata fields :
    - Host
    - source
    - sourcetype
    - index (defaults to main)
  - Identify or create timestamps.
 
- Indexes Phase
  - Handled at :
    - Indexer
  - Write data to disk
  - Run license meter 
