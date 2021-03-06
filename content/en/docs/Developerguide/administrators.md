# Administrators<a name="EN-US_TOPIC_0246507959"></a>

## Initial Users<a name="en-us_topic_0237121100_section41994915210"></a>

The account automatically generated during openGauss installation is called an initial user. An initial user is the system, monitoring, O&M, and security policy administrator who has the highest-level permissions in the system and can perform all operations. This account has the same name as the OS user used for openGauss installation. You need to manually set the password during the installation. After the first login, change the initial user's password in time.

An initial user bypasses all permission checks. You are advised to use an initial user as a database administrator only for database management other than service running.

## System Administrators<a name="en-us_topic_0237121100_section441452135814"></a>

A system administrator is an account with the  **SYSADMIN**  attribute. By default, a database system administrator has the same permissions as object owners but does not have the object permissions in  **dbe\_perf**  mode.

To create a system administrator, connect to the database as the initial user or a system administrator and run the  **[CREATE USER](create-user.md)**  or  **[ALTER USER](alter-user.md)**  statement with  **SYSADMIN**  specified.

```
CREATE USER sysadmin WITH SYSADMIN password "Bigdata@123";
```

or

```
ALTER USER joe SYSADMIN;
```

To run the  **ALTER USER**  statement, the user must exist.



