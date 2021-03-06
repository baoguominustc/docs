# EXPLAIN<a name="ZH-CN_TOPIC_0242370627"></a>

## 功能描述<a name="zh-cn_topic_0237122163_zh-cn_topic_0059777774_sd22ce4e4c8c14244afb6492e84f92d80"></a>

显示SQL语句的执行计划。

执行计划将显示SQL语句所引用的表会采用什么样的扫描方式，如：简单的顺序扫描、索引扫描等。如果引用了多个表，执行计划还会显示用到的JOIN算法。

执行计划的最关键的部分是语句的预计执行开销，这是计划生成器估算执行该语句将花费多长的时间。

若指定了ANALYZE选项，则该语句会被执行，然后根据实际的运行结果显示统计数据，包括每个计划节点内时间总开销（毫秒为单位）和实际返回的总行数。这对于判断计划生成器的估计是否接近现实非常有用。

## 注意事项<a name="zh-cn_topic_0237122163_zh-cn_topic_0059777774_s9667906bf0d748b38b576a8e40549816"></a>

- 在指定ANALYZE选项时，语句会被执行。如果用户想使用EXPLAIN分析INSERT，UPDATE，DELETE，CREATE TABLE AS或EXECUTE语句，而不想改动数据（执行这些语句会影响数据），请使用这种方法：


```
START TRANSACTION;
EXPLAIN ANALYZE ...;
ROLLBACK;
```

- 在指定ANALYZE选项时，由于参数DETAIL，NODES，NUM_NODES是属于分布式模式的功能，因此在单机模式中是被禁止使用的。假如在单机模式中使用，会产生如下所示的错误：

  ```
  postgres=# create table student(id int, name char(20));
  CREATE TABLE
  postgres=# explain (analyze,detail true)insert into student values(5,'a'),(6,'b');
  ERROR:  unrecognized EXPLAIN option "detail"
  postgres=# explain (analyze,node true)insert into student values(5,'a'),(6,'b');
  ERROR:  unrecognized EXPLAIN option "nodes"
  postgres=# explain (analyze,num_nodes true)insert into student values(5,'a'),(6,'b');
  ERROR:  unrecognized EXPLAIN option "num_nodes"
  ```

  

## 语法格式<a name="zh-cn_topic_0237122163_zh-cn_topic_0059777774_sfa16ba6ad51c455aa79e9602a5998838"></a>

-   显示SQL语句的执行计划，支持多种选项，对选项顺序无要求。

    ```
    EXPLAIN [ (  option  [, ...] )  ] statement;
    ```

    其中选项option子句的语法为。

    ```
    ANALYZE [ boolean ] |
        ANALYSE [ boolean ] |
        VERBOSE [ boolean ] |
        COSTS [ boolean ] |
        CPU [ boolean ] |
        DETAIL [ boolean ] |
        NODES [ boolean ] |
        NUM_NODES [ boolean ] |
        BUFFERS [ boolean ] |
        TIMING [ boolean ] |
        PLAN [ boolean ] |
        FORMAT { TEXT | XML | JSON | YAML }
    ```

-   显示SQL语句的执行计划，且要按顺序给出选项。

    ```
    EXPLAIN  { [  { ANALYZE  | ANALYSE  }  ] [ VERBOSE  ]  | PERFORMANCE  } statement;
    ```


## 参数说明<a name="zh-cn_topic_0237122163_zh-cn_topic_0059777774_se66550d2d643408ebe3189e751499cd5"></a>

-   **statement**

    指定要分析的SQL语句。

-   **ANALYZE boolean | ANALYSE boolean**

    显示实际运行时间和其他统计数据。

    取值范围：

    -   TRUE（缺省值）：显示实际运行时间和其他统计数据。
    -   FALSE：不显示。

-   **VERBOSE boolean**

    显示有关计划的额外信息。

    取值范围：

    -   TRUE（缺省值）：显示额外信息。
    -   FALSE：不显示。

-   **COSTS boolean**

    包括每个规划节点的估计总成本，以及估计的行数和每行的宽度。

    取值范围：

    -   TRUE（缺省值）：显示估计总成本和宽度。
    -   FALSE：不显示。

-   **CPU boolean**

    打印CPU的使用情况的信息。

    取值范围：

    -   TRUE（缺省值）：显示CPU的使用情况。
    -   FALSE：不显示。

-   **DETAIL boolean**

    打印数据库节点上的信息。

    取值范围：

    -   TRUE（缺省值）：打印数据库节点的信息。
    -   FALSE：不打印。

-   **NODES boolean**

    打印query执行的节点信息。

    取值范围：

    -   TRUE（缺省值）：打印执行的节点的信息。
    -   FALSE：不打印。

-   **NUM\_NODES boolean**

    打印执行中的节点的个数信息。

    取值范围：

    -   TRUE（缺省值）：打印数据库节点个数的信息。
    -   FALSE：不打印。

-   **BUFFERS boolean**

    包括缓冲区的使用情况的信息。

    取值范围：

    -   TRUE：显示缓冲区的使用情况。
    -   FALSE（缺省值）：不显示。

-   **TIMING boolean**

    包括实际的启动时间和花费在输出节点上的时间信息。

    取值范围：

    -   TRUE（缺省值）：显示启动时间和花费在输出节点上的时间信息。
    -   FALSE：不显示。

-   **PLAN**

    是否将执行计划存储在plan\_table中。当该选项开启时，会将执行计划存储在PLAN\_TABLE中，不打印到当前屏幕，因此该选项为on时，不能与其他选项同时使用。

    取值范围：

    -   ON（缺省值）：将执行计划存储在plan\_table中，不打印到当前屏幕。执行成功返回EXPLAIN SUCCESS。
    -   OFF：不存储执行计划，将执行计划打印到当前屏幕。

-   **FORMAT**

    指定输出格式。

    取值范围：TEXT，XML，JSON和YAML。

    默认值：TEXT。

-   **PERFORMANCE**

    使用此选项时，即打印执行中的所有相关信息。


## 示例<a name="zh-cn_topic_0237122163_zh-cn_topic_0059777774_s7175356f914d4ca1954f9c87c4b1e349"></a>

```
--创建一个表tpcds.customer_address_p1。
postgres=# CREATE TABLE tpcds.customer_address_p1 AS TABLE tpcds.customer_address;

--修改explain_perf_mode为normal
postgres=# SET explain_perf_mode=normal;

--显示表简单查询的执行计划。
postgres=# EXPLAIN SELECT * FROM tpcds.customer_address_p1;
QUERY PLAN
--------------------------------------------------
Data Node Scan  (cost=0.00..0.00 rows=0 width=0)
Node/s: All dbnodes
(2 rows)

--以JSON格式输出的执行计划（explain_perf_mode为normal时）。
postgres=# EXPLAIN(FORMAT JSON) SELECT * FROM tpcds.customer_address_p1;
              QUERY PLAN              
--------------------------------------
 [                                   +
   {                                 +
     "Plan": {                       +
       "Node Type": "Data Node Scan",+
       "Startup Cost": 0.00,         +
       "Total Cost": 0.00,           +
       "Plan Rows": 0,               +
       "Plan Width": 0,              +
       "Node/s": "All dbnodes"     +
     }                               +
   }                                 +
 ]
(1 row)

--如果有一个索引，当使用一个带索引WHERE条件的查询，可能会显示一个不同的计划。
postgres=# EXPLAIN SELECT * FROM tpcds.customer_address_p1 WHERE ca_address_sk=10000;
QUERY PLAN
--------------------------------------------------
Data Node Scan  (cost=0.00..0.00 rows=0 width=0)
Node/s: dn_6005_6006
(2 rows)

--以YAML格式输出的执行计划（explain_perf_mode为normal时）。
postgres=# EXPLAIN(FORMAT YAML) SELECT * FROM tpcds.customer_address_p1 WHERE ca_address_sk=10000;
           QUERY PLAN            
---------------------------------
 - Plan:                        +
     Node Type: "Data Node Scan"+
     Startup Cost: 0.00         +
     Total Cost: 0.00           +
     Plan Rows: 0               +
     Plan Width: 0              +
     Node/s: "dn_6005_6006"
(1 row)

--禁止开销估计的执行计划。
postgres=# EXPLAIN(COSTS FALSE)SELECT * FROM tpcds.customer_address_p1 WHERE ca_address_sk=10000;
       QUERY PLAN       
------------------------
 Data Node Scan
   Node/s: dn_6005_6006
(2 rows)

--带有聚集函数查询的执行计划。
postgres=# EXPLAIN SELECT SUM(ca_address_sk) FROM tpcds.customer_address_p1 WHERE ca_address_sk<10000;
                                      QUERY PLAN                                       
---------------------------------------------------------------------------------------
 Aggregate  (cost=18.19..14.32 rows=1 width=4)
   ->  Streaming (type: GATHER)  (cost=18.19..14.32 rows=3 width=4)
         Node/s: All dbnodes
         ->  Aggregate  (cost=14.19..14.20 rows=3 width=4)
               ->  Seq Scan on customer_address_p1  (cost=0.00..14.18 rows=10 width=4)
                     Filter: (ca_address_sk < 10000)
(6 rows)

--删除表tpcds.customer_address_p1。
postgres=# DROP TABLE tpcds.customer_address_p1;
```

## 相关链接<a name="zh-cn_topic_0237122163_zh-cn_topic_0059777774_scfac1ca9cbb74e3d891c918580e6b393"></a>

[ANALYZE | ANALYSE](ANALYZE-ANALYSE.md)

