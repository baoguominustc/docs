# Important Notes<a name="EN-US_TOPIC_0244801140"></a>

For details about technical specifications, see the  _Technical White Paper_.

Currently, a maximum of four standby nodes are supported. If one primary node and multiple standby nodes are used and the primary node is faulty, promote a standby node with more logs to the primary, preventing other standby nodes from being rebuilt.

You are advised to deploy one primary node and two standby nodes to ensure reliability and availability.

This is the second release, and the version number is 1.0.1. The ODBC is not modified, and the 1.0.0 version is still used.

