# RangerPolicyTool
This tool is used to convert HDFS Native Permissions to Ranger accepted permission format.

## Requirements inorder run the tool
1. Download the keytab file in the local machine. Run this as a super-user so you will require a super-user keytab.
2. Download the krbr.conf from the cluster's /etc/krb5.conf and place it in local machine /etc/krb5.conf

## Steps
Build the project
``` 
mvn clean install 
```
Once the build is complete under `target` there will be a jar `RangerPolicyTool-1.0-SNAPSHOT-jar-with-dependencies.jar`
``` 
java -cp ./target/RangerPolicyTool-1.0-SNAPSHOT-jar-with-dependencies.jar com.RangerPolicyTool.RangerPolicyMigrationTool 
namenode:port principle keytab_location

namenode:port - The namenode uri and the hdfs port, Eg. abc.com:8020
principle - The super user principle, Eg. hdfs/admin@foo.abc.com
keytab_loaction - The location of the super-user keytab storeed in local machine, Eg. /Users/kate/hdfs.keytab
```
This will generate `RangerPolicy.csv` in the required Ranger format.