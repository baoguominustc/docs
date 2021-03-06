# Primary Server<a name="EN-US_TOPIC_0242371503"></a>

## synchronous\_standby\_names<a name="en-us_topic_0237124713_en-us_topic_0059777578_sed4ef11504b74982b8b64ce158bf0f0e"></a>

**Parameter description**: Specifies a comma-separated list of names of potential standby servers that support synchronous replication.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

>![](public_sys-resources/icon-notice.gif) **NOTICE:**   
>-   The current synchronous standby server is on the top of the list. If the current synchronous standby server is disconnected, it will be replaced immediately with the next-highest-priority standby server. Name of the next-highest-priority standby server is added to the list.  
>-   The standby server name can be specified by setting the environment variable  **PGAPPNAME**.  

**Value range**: a string.  **\***  means to match the name of any standby machine that provides synchronous replication.

![](public_sys-resources/icon-note.gif) **NOTE:**   
ANY N (node1, node2,...) means that N host names can be selected in the brackets as a list of standby machine names for synchronous replication. For example, ANY 1 (node1, node2) means that you can choose one of node1 and node2 as the name of the standby machine for synchronous replication.

**Default value**:  **\***

## most\_available\_sync<a name="en-us_topic_0237124713_en-us_topic_0059777578_se53a9bce83414d17b84a9beb44dd0dda"></a>

**Parameter description**: When all synchronization backup machines fail, whether the host waits for the backup machine to recover and synchronize logs before submitting. When a synchronized standby machine is restored, the host submits and needs to wait for the standby machine to synchronize.

This parameter is a POSTMASTER parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: Boolean

-   **on**  indicates that the host will not be blocked when all synchronous standby machines fail.
-   **off**  indicates that the host is blocked when all synchronous standby machines fail.

**Default value**:  **off**

## enable\_stream\_replication<a name="en-us_topic_0237124713_en-us_topic_0059777578_s13e647ddc37142dfa8ed01044f51030b"></a>

**Parameter description**: Specifies whether data and logs are synchronized between primary and standby servers, and between primary and secondary servers.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

>![](public_sys-resources/icon-notice.gif) **NOTICE:**   
>-   This parameter is used for performance testing in scenarios where data synchronization to standby server is enabled and where it is disabled. If this parameter is set to  **off**, tests on abnormal scenarios, such as switchover and faults, cannot be performed to prevent inconsistency between the primary, standby, and secondary servers.  
>-   This parameter is a restricted parameter, and you are advised not to set it to  **off**  in normal service scenarios.  

**Value range**: Boolean

-   **on**  indicates that data and log synchronization is enabled.
-   **off**  indicates that data and log synchronization is disabled.

**Default value**:  **on**

## enable\_mix\_replication<a name="en-us_topic_0237124713_section1037113185420"></a>

**Parameter description**: Specifies how WAL files and data are replicated between primary and standby servers, and between primary and secondary servers.

The default value of this parameter is  **off**  and cannot be modified.

>![](public_sys-resources/icon-notice.gif) **NOTICE:**   
>This parameter cannot be modified in normal service scenarios. That is, the WAL file and data page mixed replication mode is disabled.  

**Value range**: Boolean

-   **on**  indicates that the WAL file and data page mixed replication mode is enabled.
-   **off**  indicates that the WAL file and data page mixed replication mode is disabled.

**Default value**:  **off**

## vacuum\_defer\_cleanup\_age<a name="en-us_topic_0237124713_en-us_topic_0059777578_sc622a7b295d1479dbc80f95d50aff8de"></a>

**Parameter description**: Specifies the number of transactions by which  **VACUUM**  will defer the cleanup of invalid row-store table records, so that  **VACUUM**  and  **VACUUM FULL**  do not clean up deleted tuples immediately.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: an integer ranging from 0 to 1000000.  **0**  means no delay.

**Default value**:  **0**

## data\_replicate\_buffer\_size<a name="en-us_topic_0237124713_en-us_topic_0059777578_sc3dd3b16705f4fbfb54c665ce00ef966"></a>

**Parameter description**: Specifies the amount of memory used by queues when the sender sends data pages to the receiver. The value of this parameter affects the buffer size used during the replication from the primary server to the standby server.

This parameter is a POSTMASTER parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: an integer ranging from 4096 to 1047552. The unit is KB.

**Default value**:  **128MB**  \(131072 KB\)

## walsender\_max\_send\_size<a name="en-us_topic_0237124713_en-us_topic_0059777578_sbef7a545706e4995b7028b980cdcb35a"></a>

**Parameter description**: Specifies the size of the WAL or Sender buffers on the primary server.

This parameter is a POSTMASTER parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: an integer ranging from 8 to  _INT\_MAX_. The unit is KB.

**Default value**:  **8MB**  \(8192 KB\)

## enable\_data\_replicate<a name="en-us_topic_0237124713_en-us_topic_0059777578_sa5d3c2e3d3954dd9a4b9c84024c7b63c"></a>

**Parameter description**: Specifies how data is synchronized between primary and standby servers when the data is imported to a row-store table.

This parameter is a USERSET parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: Boolean

-   **on**  indicates that the primary and standby servers synchronize data using data pages when the data is imported to a row-store table. When  **replication\_type**  is set to  **1**, this parameter cannot be set to  **on**. If this parameter is set to  **on**  using the GUC tool, its value will be forcibly changed to  **off**.
-   **off**  indicates that the primary and standby servers synchronize data using Xlogs when the data is imported to a row-store table.

**Default value**:  **off**

## ha\_module\_debug<a name="en-us_topic_0237124713_section143006151135"></a>

**Parameter description**: Specifies the replication status log of a specific data block during data replication.

This parameter is a USERSET parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: Boolean

-   **on**  indicates that the status of each data block is recorded in logs during data replication.
-   **off**  indicates that the status of each data block is not recorded in logs during data replication.

**Default value**:  **off**

## enable\_incremental\_catchup<a name="en-us_topic_0237124713_section710318493419"></a>

**Parameter description**: Specifies the data catchup mode between the primary and standby servers.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: Boolean

-   **on**  indicates that the standby server uses the incremental catchup mode. That is, the standby server scans local data files on the standby server to obtain the list of differential data files between the primary and standby servers and then performs catchup between the primary and standby servers.
-   **off**  indicates that the standby server uses the full catchup mode. That is, the standby server scans all local data files on the primary server to obtain the list of differential data files between the primary and standby servers and performs catchup between the primary and standby servers.

**Default value**:  **on**

## wait\_dummy\_time<a name="en-us_topic_0237124713_section761015504410"></a>

**Parameter description**: Specifies the maximum duration for the primary server to wait for the standby and secondary servers to start and send the scanning lists when incremental data catchup is enabled in openGauss.

This parameter is a SIGHUP parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: an integer ranging from 1 to  _INT\_MAX_. The unit is second.

**Default value**:  **300**

>![](public_sys-resources/icon-note.gif) **NOTE:**   
>The unit can only be second.  

## catchup2normal\_wait\_time<a name="en-us_topic_0237124713_section710318493419"></a>

**Parameter description**: Control the data catchup method between master and slave. In the case of a single synchronous standby machine, control the maximum time that the standby machine data catchup blocks the host.

This parameter is a POSTMASTER parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**: Integer, range -1~10000, in milliseconds.

-   **-1** means the host is blocked until the data catch-up of the standby machine is completed.
-   **0** means that the host will never be blocked when the standby data is chasing.
-   The remaining value represents the longest time that the host will be blocked when the backup data catches up. For example, a value of 5000 means that when the backup data catch-up time is 5 seconds left, the host is blocked and waits for it to complete.

**Default value**:  **-1**

## sync\_config\_strategy

**Parameter description**：Synchronization strategy for configuration files between host and standby, standby and cascade standby。

This parameter is a POSTMASTER parameter. Set it based on instructions provided in  [Table 1](resetting-parameters.md#en-us_topic_0237121562_en-us_topic_0059777490_t91a6f212010f4503b24d7943aed6d846).

**Value range**：**enum**

-   all\_node: When the host is configured as all\_node, it allows the host to actively synchronize the configuration files to all standby nodes. When the standby node is configured as all\_node, it allows the current standby to send synchronization request to its host, and allows the current standby to actively synchronize configuration files to all its cascade standby; When a cascade standby is configured as all\_node, it allows the current cascade standby to send synchronization request to its standby.
-   only\_sync\_node: When the host is configured as only\_sync\_node, it means that only the host is allowed to actively synchronize the configuration files to all the synchronous standby nodes; When the standby machine is configured as only\_sync\_node, it allows the current standby machine to send synchronization request to its host, and does not allow the current standby to actively send synchronization configuration files to all its cascade; When the cascade standby is configured as only\_sync\_node, it allows the current cascade standby to send synchronization requests to its standby.
-   none\_node: When the host is configured as none\_node, it means that the host is not allowed to actively synchronize the configuration files to any standby;When the standby machine is configured as none\_node, it means that the current standby machine is not allowed to send synchronization request to its host, and does not allowe to actively synchronize configuration files to all its cascade standby nodes. When the cascade standby is configured as none\_node, it means that the current cascade standby is not allowed to send synchronous requests to its standby machine.

**Default value**：**all\_node**

>![](public_sys-resources/icon-notice.gif) **NOTE:**
>The sending side actively synchronizes the configuration file with the receiving side, and the receiving side requests the sending side synchronizes the configuration file, which are two separate events that cause the configuration file to synchronize.If you do not want configuration file synchronization, you must configure it to none\_node on the receiving end;The sender can only be configured as none\_node if it is a standby machine;If the sending end is a host, the host is not synchronized with all the standby machines when configured as none\_node; if configured as only\_sync\_node, it is only synchronized with the synchronous standby, not with the asynchronous standby.
