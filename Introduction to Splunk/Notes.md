## Transforming commands

Commands that create statistics and vizualisations are called transforming commands

By default Splunk search job will remain active for 10 minutes, after 10 minutes, the job will need to be run again.
Shared search jobs remain active for 7 days

## Searching modes

In fast mode, the field discovery is disabled. It's only returning information on default fields and fields to fulfill your search

Verbose is slow but it returns as much fields and event data as possible

The smart mode do both but it depeding on your search (can be slow like verbose or fast as fast).

## Event Time
The time that are displayed after a search is based on the time zone defined in your account setting
