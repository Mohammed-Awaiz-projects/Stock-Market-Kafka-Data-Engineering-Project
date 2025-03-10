# Stock Market Data Pipeline using Kafka and AWS

![Image Alt Text](Architecture.jpg)

## *Project Overview*

This project demonstrates an **End-to-End Data Engineering pipeline** that processes **real-time stock market data** using **Kafka** and **AWS services**. The pipeline is designed to ingest, process, store, and analyze stock market data in real-time, with a focus on building a scalable and efficient data pipeline for financial data processing.

**Key Technologies:**
- **Python** for data ingestion and processing
- **Apache Kafka** for real-time data streaming
- **Amazon Web Services (AWS)** for cloud storage and services (*S3*, *Glue*, *Athena*, *EC2*)
- **SQL** for querying and analyzing stock data in Athena

## *Technologies Used*

- **Python**: The core language for data processing and Kafka interactions.
- **Apache Kafka**: A distributed streaming platform for real-time data ingestion and processing.
- **AWS Services**:
  - **S3** (*Simple Storage Service*) to store raw stock market data.
  - **Athena** for running SQL queries over the data in S3.
  - **Glue Crawler & Glue Catalog** for automatic schema discovery and data cataloging.
  - **EC2** to run the Kafka producer/consumer scripts.
- **SQL** for querying processed data using AWS Athena.

## *Architecture*

1. **Stock Data Collection**:
   - Fetches **real-time stock market data** from external APIs.
   - Data is processed using Python to structure it before ingestion.

2. **Data Ingestion with Kafka**:
   - Stock data is streamed in real-time via **Kafka**, where the producer sends data to Kafka topics.
   - A Kafka consumer processes the messages and stores them in **AWS S3**.

3. **Data Storage with AWS S3**:
   - The raw stock market data is stored in **S3**, in **JSON/CSV formats**, for further analysis.

4. **Data Cataloging with AWS Glue**:
   - **AWS Glue Crawlers** automatically detect the data structure in S3 and catalog the metadata in **Glue Data Catalog**.

5. **Data Analysis with AWS Athena**:
   - Use **Athena** to run SQL queries directly on the raw stock market data stored in S3, enabling quick analytics.

## *Setup Instructions*

### *Prerequisites*

- **AWS account** and **AWS CLI** configured.
- **Python 3.6 or later**.
- **Kafka** installed on your local machine or Kafka cluster access.
- Required Python packages installed (*e.g.,* `boto3`, `kafka-python`, `pandas`, `requests`, etc.).

### *Step 1: Setting Up AWS Services*

1. **Create S3 Bucket**:
   - Log in to **AWS** and create an **S3 bucket** for storing stock data.

2. **Set up AWS Glue**:
   - Create a **Glue Crawler** to automatically discover and catalog data in the S3 bucket.
   - Set up **Glue Data Catalog** to manage metadata.

3. **Set up AWS Athena**:
   - Set up **Athena** to run queries on data stored in **S3** using the Glue Catalog.

4. **Set up EC2**:
   - Launch an **EC2 instance** to run the Python scripts for Kafka producer/consumer.

### *Step 2: Setting Up Kafka*

1. Install and configure **Kafka** on your local machine or use a managed Kafka service.
2. Create topics for **real-time data ingestion**.
3. Set up a **Kafka producer** in Python to send stock data to Kafka topics.
4. Set up a **Kafka consumer** in Python to read from Kafka topics and store the data in **AWS S3**.

### *Step 3: Running the Pipeline*

1. Start the **Kafka producer** to begin streaming real-time stock data.
   ```bash
   python kafka_producer.py
   
2. Start the **Kafka consumer** to consume data from Kafka and store it in S3.
   ```bash
   python kafka_consumer.py
3. AWS Glue will automatically crawl the data in S3 and update the Glue Catalog with metadata.
4. Use AWS Athena to run SQL queries on the stock market data stored in S3.

### *Conclusion*
This project demonstrates how to design and implement a real-time data pipeline for stock market data using Kafka, AWS, and Python. It provides the foundation for creating scalable data pipelines in the financial domain, where data ingestion, processing, and querying are crucial.
