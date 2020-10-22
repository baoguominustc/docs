# gs\_tar<a name="EN-US_TOPIC_0277825669"></a>

## Background<a name="section14892026417"></a>

After the backup is compressed using  **gs\_basebackup**, the primary data directory is written to a file named  **base.tar**, and other tablespaces are named after their OIDs. The generated data file needs to be decompressed using the  **gs\_tar**  command.

>![](public_sys-resources/icon-note.gif) **NOTE:** 
>-   Currently, the  **gs\_tar**  command can only be used to decompress archive files generated by  **gs\_basebackup**.
>-   If a compression level is specified by  **gs\_basebackup**, a file ended with gz will be generated. In this case, you need to run the  **gzip**  command to decompress the generated .tar package, and then run the  **gs\_tar**  command to decompress the generated .tar file.

## Syntax<a name="section253225804218"></a>

Display help information.

```
gs_tar -? | --help
```

Display version information.

```
gs_tar -V | --version
```

## Parameter Description<a name="section1675192014459"></a>

**gs\_tar**  parameters are as follows:

-   -F, –filename=FILENAME


Decompresses a file. This parameter is mandatory.

-   -D, –destination=DIRECTORY


Directory for storing decompressed files. This parameter is mandatory.

## Example<a name="section110917418469"></a>

```
gs_tar -D /home/test/dn1 -F /home/test/trunk/install/data/backup/base.tar
```
