# Sending Server<a name="EN-US_TOPIC_0251900940"></a>

## max\_wal\_senders<a name="en-us_topic_0242371502_en-us_topic_0237124712_en-us_topic_0059777860_s197194d979964a63a01b4b9fc15b0053"></a>

**Parameter description**: Specifies the maximum number of simultaneously running WAL sender processes. The value cannot be greater than or equal to that of  **[max\_connections](connection-settings.md#en-us_topic_0242371485_en-us_topic_0237124695_en-us_topic_0059777636_sa723b719fa70453bb7ec27f323d41c79)**.

This parameter is a POSTMASTER parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

>![](public_sys-resources/icon-notice.gif) **NOTICE:** 
>**[wal\_level](settings.md#en-us_topic_0242371497_en-us_topic_0237124707_en-us_topic_0059778393_s2c76f5957066407a959191148f2c780f)**  must be set to  **archive**  or  **hot\_standby**  to allow the connection from standby servers.

**Value range**: an integer ranging from 0 to 262143

**Default value**:  **4**  for a single-server system and  **8**  for a primary/standby environment

## wal\_keep\_segments<a name="en-us_topic_0242371502_en-us_topic_0237124712_en-us_topic_0059777860_sf1f97e9d2e034746932686e8578c975e"></a>

**Parameter description**: Specifies the number of Xlog file segments. Specifies the minimum number of transaction log files stored in the  **pg\_xlog**  directory. The standby server obtains log files from the primary server for streaming replication.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: an integer ranging from 2 to  _INT\_MAX_

**Default value**:  **65**

**Setting suggestions**:

-   During WAL archiving or recovery from a checkpoint on the server, the system may retain more log files than the number specified by  **wal\_keep\_segments**.
-   If this parameter is set to an excessively small value, a transaction log may have been overwritten by a new transaction before requested by the standby server. As a result, the request fails and the connection between the primary and standby servers is terminated.
-   If the HA system uses asynchronous transmission, increase the value of  **wal\_keep\_segments**  when data greater than 4 GB is continuously imported in COPY mode. Take T6000 board as an example. If the data to be imported reaches 50 GB, you are advised to set this parameter to  **1000**. You can dynamically restore the setting of this parameter after data import is complete and the WAL synchronization is proper.

## wal\_sender\_timeout<a name="en-us_topic_0242371502_en-us_topic_0237124712_en-us_topic_0059777860_s909a994d7a9044d89d62e7028cf3bb65"></a>

**Parameter description**: Specifies the maximum duration that the sending server waits for the WAL reception in the receiver.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

>![](public_sys-resources/icon-notice.gif) **NOTICE:** 
>-   If the data volume on the primary server is huge, the value of this parameter must be increased for the database rebuilding on a standby server. For example, if the data volume on the primary server reaches 500 GB, you are advised to set this parameter to 600 seconds.
>-   This parameter cannot be set to a value larger than the value of  **wal\_receiver\_timeout**  or the timeout parameter for database rebuilding.

**Value range**: an integer ranging from 0 to  _INT\_MAX_. The unit is ms.

**Default value**:  **6s**

## replconninfo1<a name="en-us_topic_0242371502_en-us_topic_0237124712_en-us_topic_0059777860_se4d237ddf6e7410182aa0936da9d54ed"></a>

**Parameter description**: Specifies the information about the first node to be listened to and authenticated by the current server.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: a string. An empty string indicates that no information about the first node is configured.

**Default value**: empty

## replconninfo2<a name="en-us_topic_0242371502_en-us_topic_0237124712_en-us_topic_0059777860_s01420b1b22454611b55a523555429058"></a>

**Parameter description**: Specifies the information about the second node to be listened to and authenticated by the current server.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: a string. An empty string indicates that no information about the second node is configured.

**Default value**: empty

## replconninfo3<a name="en-us_topic_0242371502_en-us_topic_0237124712_section8514121012410"></a>

**Parameter description**: Specifies the information about the third node to be listened to and authenticated by the current server.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: a string. An empty string indicates that no information about the third node is configured.

**Default value**: empty

## replconninfo4<a name="en-us_topic_0242371502_en-us_topic_0237124712_section961005915410"></a>

**Parameter description**: Specifies the information about the fourth node to be listened to and authenticated by the current server.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: a string. An empty string indicates that no information about the fourth node is configured.

**Default value**: empty

## replconninfo5<a name="en-us_topic_0242371502_en-us_topic_0237124712_section1573419505515"></a>

**Parameter description**: Specifies the information about the fifth node to be listened to and authenticated by the current server.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: a string. An empty string indicates that no information about the fifth node is configured.

**Default value**: empty

## replconninfo6<a name="en-us_topic_0242371502_en-us_topic_0237124712_section1136279965"></a>

**Parameter description**: Specifies the information about the sixth node to be listened to and authenticated by the current server.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: a string. An empty string indicates that no information about the sixth node is configured.

**Default value**: empty

## replconninfo7<a name="en-us_topic_0242371502_en-us_topic_0237124712_section10707131718617"></a>

**Parameter description**: Specifies the information about the seventh node to be listened to and authenticated by the current server.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0242370406_en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: a string. An empty string indicates that no information about the seventh node is configured.

**Default value**: empty

