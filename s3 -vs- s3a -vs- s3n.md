
There are few Hadoop connectors to S3. Only S3A is actively maintained by the Hadoop project itself.  

Apache’s Hadoop’s original **`s3://`** client. This is no longer included in Hadoop.  
Amazon EMR’s **`s3://`** client. This is from the Amazon EMR team, who actively maintain it.  

Apache’s Hadoop’s **`s3n://`** filesystem client.  
This connector is no longer available: users must migrate to the newer **`s3a://`** client.  

**Reference:**  
1. https://hadoop.apache.org/docs/current/hadoop-aws/tools/hadoop-aws/index.html#Other_S3_Connectors

