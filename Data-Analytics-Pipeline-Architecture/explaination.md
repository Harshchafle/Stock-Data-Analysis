# Data Analytics Pipeline (Architecture)

1. A python script continuously fetches real-time stock market data from APIs like yfinance and pushes it to Amazon Kinesis Data Streams.
2. Amazon Kinesis Data Stream Acts as a real-time data pipeline.
3. Aws Lambda function is triggered by Kinesis to process, clean and transform the incoming data before storing it in S3 and DynamoDB.
4. The raw stock data is stored in Amazon S3 for historical Analysis.
5. AWS Glue Data Catalogue crawls the raw data stored in S3, creating a structured schema that enables querying using Athena.
6. Amazon Athena, A serverless SQL query engine, runs analytical queries, over the structured stock data via Glue Data Catalogue.
7. Query result from Athena is then stored in dedicated S3 bucket.
8. Amazon DynamoDB stores stores processed stock data for real time lookups.
9. An AWS Lambda function analyzes real time stock trends by computing moving averages (SMA-5 and SMA-20) and detecting potential buy/sell signals.
10. Amazon SNS sends real-time stock trend alerts via Email to user.


Amazon Athena:
    It is serverless sql querying.
    It queries s3 data without creating database
    Cost optimized cause we are paying for the data we are querying only.
    Scalable to handle large scale data with ease.
    Requires Amazon Glue catalogue to define the schema of s3 bucket.