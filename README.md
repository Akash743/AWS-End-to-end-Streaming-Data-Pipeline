# AWS-End-to-end-Streaming-Data-Pipeline


![AWS-Project-image](https://user-images.githubusercontent.com/57750483/195297243-3460f0d1-2706-4fdf-87f5-b11ea43d75bd.png)

**Project flow:**

The project depicts an end-to-end streaming data pipeline. Streaming data is purchase data  involving the following steps:

1. Transferring data from local system to AWS Kinesis data stream via AWS API-gateway.

2. Using AWS lambda function to constantly read the json data hitting the AWS API and transferring that to a buffer service, Kinesis stream.

3. Streaming data from Kinesis being stored in Data Warehouse(Redshift Cluster and DynamoDB) and Data Lake, S3 bucket:

      i) Data reaching the Kinesis is to be stored somewhere as Kinesis is just a buffer. This can be done in several ways. One could be to store data in a         structured format in Data Warehouse like Redshift cluster to make that available for further usage and analysis. For transferring data from Kinesis         to Redshift, we're using Kinesis Firehose.
      
      ii) Same data is being stored in AWS S3 bucket Data Lake as dump in json format and in a no-SQL database, DynamoDB.
        For doing so, I'm using Lambda function as a streaming data processing framework to constantly format the data and organize in desirable formats           for S3, Redshift and DynamoDB.
      
 4. Fetching Data from Data Warehouses

        i) Fetching transactional data from DynamoDB via an app: A streamlit app is build which will be using the API gateway 'GET' request to trigger a              lambda function serving to fetch transactional records based on the Customer_ID and Purchase_ID from DynamoDB table.

        ii) Visualization and analysis: Data stored in Redshift can be accesses for visualization and analysis purposes, by connecting Tableau, Quicksight             with the Redshift cluster.
