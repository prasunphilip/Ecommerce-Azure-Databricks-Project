# Ecommerce-Azure-Databricks-Project
In this project, I developed an ETL pipeline leveraging Azure services and Databricks to process e-commerce data sourced from Data.com. The data is stored in Azure Data Lake, where Azure Databricks is utilized to transform the data before storing it back in the Data Lake for further analysis.

# Extract:
- The data was sourced from Data.com and stored in Azure Data Lake as CSV files.
- It includes information about buyers, sellers, countries, and users. The user data is further divided into smaller chunks to simulate new user activity.
- The CSV files are organized within the Azure Data Lake under the container _landing_zone_1_, with separate folders for buyers, sellers, countries, and users.
- Using Azure Data Factory, the data is converted from CSV to Parquet format. After conversion, the Parquet files are stored in the container _landing_zone_2_, maintaining the same folder structure.
- Two distinct pipelines were created: one for buyers, sellers, and countries, and another specifically for users. This separation was implemented because user data is updated daily, while buyers, sellers, and countries     are updated on a weekly basis.
- Correspondingly, two triggers were configured: one for buyers, sellers, and countries that runs weekly, and another for users that runs daily.

# Transform:
- Azure Databricks was utilized to transform the data following the Medallion Architecture (Bronze, Silver, and Gold layers) to ensure a structured and scalable data transformation process.

### Bronze Layer:
- Data from _landing_zone_2_ was loaded into Delta format to enable efficient processing.
- The ingested raw data was stored in the Bronze Layer, serving as the foundational storage layer for all incoming data.
### Silver Layer:
- Data transformations, such as cleaning, aggregation, and standardization, were applied to the raw data in the Bronze Layer.
- The transformed data was then stored in the Silver Layer, ensuring it is organized and ready for analytical use.

# Load:
### Gold Layer:
- Data from multiple tables was combined into a consolidated, unified table to facilitate comprehensive analysis and reporting.
- The final processed data was stored in the Gold Layer, representing the highest level of refinement and usability for downstream analytics.

# Summary of Azure Serviecs Used:
- _**Azure Resource Group:**_ A logical container that organizes and manages Azure resources for easy deployment, monitoring, and management.
- _**Azure Storage Accounts:**_ A scalable and secure storage solution for storing blobs, files, queues, tables, and data in the cloud.
- _**Azure App Registration:**_ A service to register applications with Azure Active Directory for authentication and secure access to resources.
- _**Azure Data Factory:**_ A cloud-based data integration service to orchestrate and automate data movement and transformation workflows.
- _**Azure Databricks:**_ A collaborative, Apache Spark-based platform optimized for big data analytics and machine learning.

# Architecture of the ETL Pipeline:
![image](https://github.com/user-attachments/assets/7da7178b-b6e4-4165-b272-da249470fdf0)

  
