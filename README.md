# AWS-End-to-end-Streaming-Data-Pipeline


![AWS-Project-image](https://user-images.githubusercontent.com/57750483/195297243-3460f0d1-2706-4fdf-87f5-b11ea43d75bd.png)

**Project flow:**

The project depicts an end-to-end streaming data pipeline involving the following steps:
1. Transferring data from local system to AWS Kinesis data stream via AWS API-gateway.
2. Using AWS lambda function to constantly read the json data hitting the AWS API and transferring that to a buffer service, Kinesis stream.
3. Streaming data from Kinesis to be stored in Data Warehouse(Redshift Cluster and DynamoDB) and Data Lakes like S3 bucket:
      Data reaching the Kinesis is to be stored somewhere as Kinesis is just a buffer. This can be done in several ways. One could be to store data in a         structured format in Data Warehouse like Redshift cluster to make that available for further usage and analysis. Secondly, the same data can be             stored in Data Lakes as dump in json format as in AWS S3 bucket or in a no-SQL database like DynamoDB.
      In this project, I have also used DynamoDB, along with S3 bucket.
      For doing so, Lambda function can be used as streaming data processing framework to constantly format the data and organize in desirable formats for       S3, Redshift and DynamoDB.
      
 4. Fetching Data from Data Warehouses
  i) Fetching transactional data from DynamoDB via an app: A streamlit app is build which will be using the API gateway 'GET' request to trigger a lambda function serving to fetch transactional records based on the Customer_ID and Purchase_ID from DynamoDB table.
  ii) Similarly for visualization and analyticsla purposes, bulk data can be accessed by connecting Tableau, Quicksight with the Redshift cluster.
