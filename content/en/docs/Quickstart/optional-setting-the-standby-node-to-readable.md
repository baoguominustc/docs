# \(Optional\) Setting the Standby Node to Readable<a name="EN-US_TOPIC_0270171710"></a>

Readable standby node is an optional feature. You need to modify the configuration parameters and restart the primary and standby nodes before using this feature. After the readable standby node function is enabled, the standby node is readable, meeting data consistency requirements.

## Procedure<a name="en-us_topic_0249784573_section1726123816195"></a>

1.  If the openGauss database instance is running on the primary and standby nodes, stop the database instance on both nodes.
2.  Open the  **postgres.conf**  configuration files of the primary and standby nodes based on the corresponding paths in  [Table 2](configuring-primary-database-node-information.md#en-us_topic_0249784583_en-us_topic_0241802596_table15838192510429), find the corresponding parameters, and change the parameter values to  **wal\_level=hot\_standby**,  **hot\_standby = on**, and  **hot\_standby\_feedback = on**.
3.  After the modification, start the primary and standby nodes.
