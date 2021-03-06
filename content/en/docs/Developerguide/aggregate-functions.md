# Aggregate Functions<a name="EN-US_TOPIC_0242370446"></a>

## Aggregate Functions<a name="en-us_topic_0237121982_en-us_topic_0059778466_s6494488eb2824afa801304697cb740e4"></a>

-   sum\(expression\)

    Description: Sum of expression across all input values

    Return type:

    Generally, same as the argument data type. In the following cases, type conversion occurs:

    -   **BIGINT**  for  **SMALLINT**  or  **INT**  arguments
    -   **NUMBER**  for  **BIGINT**  arguments
    -   **DOUBLE PRECISION**  for floating-point arguments

    Example:

    ```
    postgres=# SELECT SUM(ss_ext_tax) FROM tpcds.STORE_SALES;
      sum      
    --------------
     213267594.69
    (1 row)
    ```

-   max\(expression\)

    Description: maximum value of expression across all input values

    Argument types: any array, numeric, string, or date/time type

    Return type: same as the argument type

    Example:

    ```
    postgres=# SELECT MAX(inv_quantity_on_hand) FROM tpcds.inventory;
    ```

-   min\(expression\)

    Description: minimum value of expression across all input values

    Argument types: any array, numeric, string, or date/time type

    Return type: same as the argument type

    Example:

    ```
    postgres=# SELECT MIN(inv_quantity_on_hand) FROM tpcds.inventory;
     min 
    -----
       0
    (1 row)
    ```

-   avg\(expression\)

    Description: Average \(arithmetic mean\) of all input values

    Return type:

    **NUMBER**  for any integer-type argument.

    **DOUBLE PRECISION**  for a floating-point argument,

    otherwise the same as the argument data type.

    Example:

    ```
    postgres=# SELECT AVG(inv_quantity_on_hand) FROM tpcds.inventory;
             avg          
    ----------------------
     500.0387129084044604
    (1 row)
    ```

-   count\(expression\)

    Description: number of input rows for which the value of expression is not null

    Return type: bigint

    Example:

    ```
    postgres=# SELECT COUNT(inv_quantity_on_hand) FROM tpcds.inventory;
      count   
    ----------
     11158087
    (1 row)
    ```

-   count\(\*\)

    Description: number of input rows

    Return type: bigint

    Example:

    ```
    postgres=# SELECT COUNT(*) FROM tpcds.inventory;
      count   
    ----------
     11745000
    (1 row)
    ```

-   median\(expression\) \[over \(query partition clause\)\]

    Description: Returns the median of an expression.  **NULL**  will be ignored by the median function during calculation. The  **DISTINCT**  keyword can be used to exclude duplicate records in an expression. The data type of the input expression can be numeric \(including integer, double, and bigint\) or interval. For other data types, the median cannot be calculated.

    Return type: double or interval

    Example:

    ```
    select median(id) from (values(1), (2), (3), (4), (null)) test(id);
     median
    --------
         2.5
    (1 row)
    ```

-   array\_agg\(expression\)

    Description: input values, including nulls, concatenated into an array

    Return type: array of the argument type

    Example:

    ```
    postgres=# SELECT ARRAY_AGG(sr_fee) FROM tpcds.store_returns WHERE sr_customer_sk = 2;
       array_agg   
    ---------------
     {22.18,63.21}
    (1 row)
    ```

-   string\_agg\(expression, delimiter\)

    Description: input values concatenated into a string, separated by delimiter

    Return type: same as the argument type

    Example:

    ```
    postgres=# SELECT string_agg(sr_item_sk, ',') FROM tpcds.store_returns where sr_item_sk < 3;
             string_agg         
    ---------------------------------------------------------------------------------
    ------------------------------
     1,2,1,2,2,1,1,2,2,1,2,1,2,1,1,1,2,1,1,1,1,1,2,1,1,1,1,1,2,2,1,1,1,1,1,1,1,1,1,2,
    2,1,1,1,1,1,1,2,2,1,1,2,1,1,1
    (1 row)
    ```

-   listagg\(expression \[, delimiter\]\) WITHIN GROUP\(ORDER BY order-list\)

    Description: aggregation column data sorted according to the mode specified by  **WITHIN GROUP**, and concatenated to a string using the specified delimiter

    -   **expression**: Mandatory. It specifies an aggregation column name or a column-based, valid expression. It does not support the  **DISTINCT**  keyword and the  **VARIADIC**  parameter.
    -   **delimiter**: Optional. It specifies a delimiter, which can be a string constant or a deterministic expression based on a group of columns. The default value is empty.
    -   **order-list**: Mandatory. It specifies the sorting mode in a group.

    Return type: text

    Example:

    The aggregation column is of the text character set type.

    ```
    postgres=# SELECT deptno, listagg(ename, ',') WITHIN GROUP(ORDER BY ename) AS employees FROM emp GROUP BY deptno;
     deptno |              employees               
    --------+--------------------------------------
         10 | CLARK,KING,MILLER
         20 | ADAMS,FORD,JONES,SCOTT,SMITH
         30 | ALLEN,BLAKE,JAMES,MARTIN,TURNER,WARD
    (3 rows)
    ```

    The aggregation column is of the integer type.

    ```
    postgres=# SELECT deptno, listagg(mgrno, ',') WITHIN GROUP(ORDER BY mgrno NULLS FIRST) AS mgrnos FROM emp GROUP BY deptno;
     deptno |            mgrnos             
    --------+-------------------------------
         10 | 7782,7839
         20 | 7566,7566,7788,7839,7902
         30 | 7698,7698,7698,7698,7698,7839
    (3 rows)
    ```

    The aggregation column is of the floating point type.

    ```
    postgres=# SELECT job, listagg(bonus, '($); ') WITHIN GROUP(ORDER BY bonus DESC) || '($)' AS bonus FROM emp GROUP BY job;
        job     |                      bonus                      
    ------------+-------------------------------------------------
     CLERK      | 10234.21($); 2000.80($); 1100.00($); 1000.22($)
     PRESIDENT  | 23011.88($)
     ANALYST    | 2002.12($); 1001.01($)
     MANAGER    | 10000.01($); 2399.50($); 999.10($)
     SALESMAN   | 1000.01($); 899.00($); 99.99($); 9.00($)
    (5 rows)
    ```

    The aggregation column is of the time type.

    ```
    postgres=# SELECT deptno, listagg(hiredate, ', ') WITHIN GROUP(ORDER BY hiredate DESC) AS hiredates FROM emp GROUP BY deptno;
     deptno |                                                          hiredates                                                           
    --------+------------------------------------------------------------------------------------------------------------------------------
         10 | 1982-01-23 00:00:00, 1981-11-17 00:00:00, 1981-06-09 00:00:00
         20 | 2001-04-02 00:00:00, 1999-12-17 00:00:00, 1987-05-23 00:00:00, 1987-04-19 00:00:00, 1981-12-03 00:00:00
         30 | 2015-02-20 00:00:00, 2010-02-22 00:00:00, 1997-09-28 00:00:00, 1981-12-03 00:00:00, 1981-09-08 00:00:00, 1981-05-01 00:00:00
    (3 rows)
    ```

    The aggregation column is of the time interval type.

    ```
    postgres=# SELECT deptno, listagg(vacationTime, '; ') WITHIN GROUP(ORDER BY vacationTime DESC) AS vacationTime FROM emp GROUP BY deptno;
     deptno |                                    vacationtime                                    
    --------+------------------------------------------------------------------------------------
         10 | 1 year 30 days; 40 days; 10 days
         20 | 70 days; 36 days; 9 days; 5 days
         30 | 1 year 1 mon; 2 mons 10 days; 30 days; 12 days 12:00:00; 4 days 06:00:00; 24:00:00
    (3 rows)
    ```

    By default, the delimiter is empty.

    ```
    postgres=# SELECT deptno, listagg(job) WITHIN GROUP(ORDER BY job) AS jobs FROM emp GROUP BY deptno;
     deptno |                     jobs                     
    --------+----------------------------------------------
         10 | CLERKMANAGERPRESIDENT
         20 | ANALYSTANALYSTCLERKCLERKMANAGER
         30 | CLERKMANAGERSALESMANSALESMANSALESMANSALESMAN
    (3 rows)
    ```

    When  **listagg**  is used as a window function, the  **OVER**  clause does not support the window sorting of  **ORDER BY**, and the  **listagg**  column is an ordered aggregation of the corresponding groups.

    ```
    postgres=# SELECT deptno, mgrno, bonus, listagg(ename,'; ') WITHIN GROUP(ORDER BY hiredate) OVER(PARTITION BY deptno) AS employees FROM emp;
     deptno | mgrno |  bonus   |                 employees                 
    --------+-------+----------+-------------------------------------------
         10 |  7839 | 10000.01 | CLARK; KING; MILLER
         10 |       | 23011.88 | CLARK; KING; MILLER
         10 |  7782 | 10234.21 | CLARK; KING; MILLER
         20 |  7566 |  2002.12 | FORD; SCOTT; ADAMS; SMITH; JONES
         20 |  7566 |  1001.01 | FORD; SCOTT; ADAMS; SMITH; JONES
         20 |  7788 |  1100.00 | FORD; SCOTT; ADAMS; SMITH; JONES
         20 |  7902 |  2000.80 | FORD; SCOTT; ADAMS; SMITH; JONES
         20 |  7839 |   999.10 | FORD; SCOTT; ADAMS; SMITH; JONES
         30 |  7839 |  2399.50 | BLAKE; TURNER; JAMES; MARTIN; WARD; ALLEN
         30 |  7698 |     9.00 | BLAKE; TURNER; JAMES; MARTIN; WARD; ALLEN
         30 |  7698 |  1000.22 | BLAKE; TURNER; JAMES; MARTIN; WARD; ALLEN
         30 |  7698 |    99.99 | BLAKE; TURNER; JAMES; MARTIN; WARD; ALLEN
         30 |  7698 |  1000.01 | BLAKE; TURNER; JAMES; MARTIN; WARD; ALLEN
         30 |  7698 |   899.00 | BLAKE; TURNER; JAMES; MARTIN; WARD; ALLEN
    (14 rows)
    ```

-   covar\_pop\(Y, X\)

    Description: overall covariance

    Return type: double precision

    Example:

    ```
    postgres=# SELECT COVAR_POP(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
        covar_pop     
    ------------------
     829.749627587403
    (1 row)
    ```

-   covar\_samp\(Y, X\)

    Description: sample covariance

    Return type: double precision

    Example:

    ```
    postgres=# SELECT COVAR_SAMP(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
        covar_samp    
    ------------------
     830.052235037289
    (1 row)
    ```

-   stddev\_pop\(expression\)

    Description: overall standard difference

    Return type:  **double precision**  for floating-point arguments, otherwise  **numeric**

    Example:

    ```
    postgres=# SELECT STDDEV_POP(inv_quantity_on_hand) FROM tpcds.inventory WHERE inv_warehouse_sk = 1;
        stddev_pop    
    ------------------
     289.224294957556
    (1 row)
    ```

-   stddev\_samp\(expression\)

    Description: sample standard deviation of the input values

    Return type:  **double precision**  for floating-point arguments, otherwise  **numeric**

    Example:

    ```
    postgres=# SELECT STDDEV_SAMP(inv_quantity_on_hand) FROM tpcds.inventory WHERE inv_warehouse_sk = 1;
       stddev_samp    
    ------------------
     289.224359757315
    (1 row)
    ```

-   var\_pop\(expression\)

    Description: population variance of the input values \(square of the population standard deviation\)

    Return type:  **double precision**  for floating-point arguments, otherwise  **numeric**

    Example:

    ```
    postgres=# SELECT VAR_POP(inv_quantity_on_hand) FROM tpcds.inventory WHERE inv_warehouse_sk = 1;
          var_pop       
    --------------------
     83650.692793695475
    (1 row)
    ```

-   var\_samp\(expression\)

    Description: sample variance of the input values \(square of the sample standard deviation\)

    Return type:  **double precision**  for floating-point arguments, otherwise  **numeric**

    Example:

    ```
    postgres=# SELECT VAR_SAMP(inv_quantity_on_hand) FROM tpcds.inventory WHERE inv_warehouse_sk = 1;
          var_samp      
    --------------------
     83650.730277028768
    (1 row)
    ```

-   bit\_and\(expression\)

    Description: the bitwise AND of all non-null input values, or null if none

    Return type: same as the argument type

    Example:

    ```
    postgres=# SELECT BIT_AND(inv_quantity_on_hand) FROM tpcds.inventory WHERE inv_warehouse_sk = 1;
     bit_and 
    ---------
           0
    (1 row)
    ```

-   bit\_or\(expression\)

    Description: the bitwise OR of all non-null input values, or null if none

    Return type: same as the argument type

    Example:

    ```
    postgres=# SELECT BIT_OR(inv_quantity_on_hand) FROM tpcds.inventory WHERE inv_warehouse_sk = 1;
     bit_or 
    --------
       1023
    (1 row)
    ```

-   bool\_and\(expression\)

    Description: Its value is  **true**  if all input values are  **true**, otherwise  **false**.

    Return type: bool

    Example:

    ```
    postgres=# SELECT bool_and(100 <2500);
     bool_and
    ----------
     t
    (1 row)
    ```

-   bool\_or\(expression\)

    Description: Its value is  **true**  if at least one input value is  **true**, otherwise  **false**.

    Return type: bool

    Example:

    ```
    postgres=# SELECT bool_or(100 <2500);
     bool_or
    ----------
     t
    (1 row)
    ```

-   corr\(Y, X\)

    Description: correlation coefficient

    Return type: double precision

    Example:

    ```
    postgres=# SELECT CORR(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
           corr        
    -------------------
     .0381383624904186
    (1 row)
    ```

-   every\(expression\)

    Description: equivalent to  **bool\_and**

    Return type: bool

    Example:

    ```
    postgres=# SELECT every(100 <2500);
     every
    -------
     t
    (1 row)
    ```

-   regr\_avgx\(Y, X\)

    Description: average of the independent variable \(**sum\(X\)/N**\)

    Return type: double precision

    Example:

    ```
    postgres=# SELECT REGR_AVGX(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
        regr_avgx     
    ------------------
     578.606576740795
    (1 row)
    ```

-   regr\_avgy\(Y, X\)

    Description: average of the dependent variable \(**sum\(Y\)/N**\)

    Return type: double precision

    Example:

    ```
    postgres=# SELECT REGR_AVGY(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
        regr_avgy     
    ------------------
     50.0136711629602
    (1 row)
    ```

-   regr\_count\(Y, X\)

    Description: number of input rows in which both expressions are non-null

    Return type: bigint

    Example:

    ```
    postgres=# SELECT REGR_COUNT(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
     regr_count 
    ------------
           2743
    (1 row)
    ```

-   regr\_intercept\(Y, X\)

    Description: y-intercept of the least-squares-fit linear equation determined by the \(X, Y\) pairs

    Return type: double precision

    Example:

    ```
    postgres=# SELECT REGR_INTERCEPT(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
      regr_intercept  
    ------------------
     49.2040847848607
    (1 row)
    ```

-   regr\_r2\(Y, X\)

    Description: square of the correlation coefficient

    Return type: double precision

    Example:

    ```
    postgres=# SELECT REGR_R2(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
          regr_r2       
    --------------------
     .00145453469345058
    (1 row)
    ```

-   regr\_slope\(Y, X\)

    Description: slope of the least-squares-fit linear equation determined by the \(X, Y\) pairs

    Return type: double precision

    Example:

    ```
    postgres=# SELECT REGR_SLOPE(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
         regr_slope     
    --------------------
     .00139920009665259
    (1 row)
    ```

-   regr\_sxx\(Y, X\)

    Description:  **sum\(X^2\) - sum\(X\)^2/N **\(sum of squares of the independent variables\)

    Return type: double precision

    Example:

    ```
    postgres=# SELECT REGR_SXX(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
         regr_sxx     
    ------------------
     1626645991.46135
    (1 row)
    ```

-   regr\_sxy\(Y, X\)

    Description:  **sum\(X\*Y\) - sum\(X\) \* sum\(Y\)/N**  \("sum of products" of independent times dependent variable\)

    Return type: double precision

    Example:

    ```
    postgres=# SELECT REGR_SXY(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
         regr_sxy     
    ------------------
     2276003.22847225
    (1 row)
    ```

-   regr\_syy\(Y, X\)

    Description:  **sum\(Y^2\) - sum\(Y\)^2/N**  \("sum of squares" of the dependent variable\)

    Return type: double precision

    Example:

    ```
    postgres=# SELECT REGR_SYY(sr_fee, sr_net_loss) FROM tpcds.store_returns WHERE sr_customer_sk < 1000;
        regr_syy     
    -----------------
     2189417.6547314
    (1 row)
    ```

-   stddev\(expression\)

    Description: alias of  **stddev\_samp**

    Return type:  **double precision**  for floating-point arguments, otherwise  **numeric**

    Example:

    ```
    postgres=# SELECT STDDEV(inv_quantity_on_hand) FROM tpcds.inventory WHERE inv_warehouse_sk = 1;
          stddev      
    ------------------
     289.224359757315
    (1 row)
    ```

-   variance\(expexpression,ression\)

    Description: alias of  **var\_samp**

    Return type:  **double precision**  for floating-point arguments, otherwise  **numeric**

    Example:

    ```
    postgres=# SELECT VARIANCE(inv_quantity_on_hand) FROM tpcds.inventory WHERE inv_warehouse_sk = 1;
          variance      
    --------------------
     83650.730277028768
    (1 row)
    ```

-   checksum\(expression\)

    Description: Returns the CHECKSUM value of all input values. This function can be used to check whether the data in the tables is the same before and after the backup, restoration, or migration of the openGauss database \(databases other than openGauss are not supported\). Before and after database backup, database restoration, or data migration, you need to manually run SQL commands to obtain the execution results. Compare the obtained execution results to check whether the data in the tables before and after the backup or migration is the same.

    ![](public_sys-resources/icon-note.gif) **NOTE:**  
    -   For large tables, the execution of CHECKSUM function may take a long time.  
    -   If the CHECKSUM values of two tables are different, it indicates that the contents of the two tables are different. Using the hash function in the CHECKSUM function may incur conflicts. There is low possibility that two tables with different contents may have the same CHECKSUM value. The same problem may occur when CHECKSUM is used for columns.  
    -   If the time type is timestamp, timestamptz, or smalldatetime, ensure that the time zone settings are the same when calculating the CHECKSUM value.  
    -   If the CHECKSUM value of a column is calculated and the column type can be changed to TEXT by default, set  _expression_  to the column name.  
    -   If the CHECKSUM value of a column is calculated and the column type cannot be converted to TEXT by default, set  _expression_  to  _Column name_**::TEXT**.  
    -   If the CHECKSUM value of all columns is calculated, set  _expression_  to  _Table name_**::TEXT**.  

    The following types of data can be converted into TEXT types by default: char, name, int8, int2, int1, int4, raw, pg\_node\_tree, float4, float8, bpchar, varchar, nvarchar2, date, timestamp, timestamptz, numeric, and smalldatetime. Other types need to be forcibly converted to TEXT.

    Return type: numeric

    Example:

    The following shows the CHECKSUM value of a column that can be converted to the TEXT type by default:

    ```
    postgres=# SELECT CHECKSUM(inv_quantity_on_hand) FROM tpcds.inventory;
         checksum      
    -------------------
     24417258945265247
    (1 row)
    ```

    The following shows the CHECKSUM value of a column that cannot be converted to the TEXT type by default. Note that the CHECKSUM parameter is set to  _Column name_**::TEXT**.

    ```
    postgres=# SELECT CHECKSUM(inv_quantity_on_hand::TEXT) FROM tpcds.inventory;
         checksum      
    -------------------
     24417258945265247
    (1 row)
    ```

    The following shows the CHECKSUM value of all columns in a table. Note that the CHECKSUM parameter is set to  _Table name_**::TEXT**. The table name is not modified by its schema.

    ```
    postgres=# SELECT CHECKSUM(inventory::TEXT) FROM tpcds.inventory;                    
         checksum      
    -------------------
     25223696246875800
    (1 row)
    ```


