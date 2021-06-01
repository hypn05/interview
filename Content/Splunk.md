## SIEM Tool(Security incident and event mangement tool)
* Splunk is a software platform that allows users to analyze machine-generated data.
* It processes and analyzes machine data and converts it for accurate visualizations.

### Name the components of Splunk architecture.

Search Head – It provides GUI for searching
Indexer – It indexes the machine data. Data transformation is performed here.
Forwarder – Collects data from different servers and forwards logs to the Indexer
Deployment Server: Manges Splunk components in a distributed environment


CIM
In most splunk deployments data comes from multiple sourcestypes. As a result the same values of data can occur under different field names. Like ClientIP and userIP.
At search time we may want to normalize these to correlate events from both source types.
CIM(Common information modal can be used for this purpose)
CIM adon can be used. Should be installed on search-heads.

Checkpoints
Spluck will index the same data again and again, to fix that a checkpoint can be added. If data is indexed don't index it again.


Indexer ack: To check for failure(A channel id is added to distiguish(Check for status to ack))

