# Population Data Processing with PySpark and Azure Data Lake Storage (ADLS)

## Overview

This project demonstrates a complete data processing pipeline leveraging PySpark to transform population data stored in Azure Data Lake Storage (ADLS). Through a series of data cleaning, transformation, and filtering steps, this project showcases the power of PySpark for handling large datasets and preparing them for further analysis or machine learning workflows.

## Project Goals

1. **Data Connectivity**: Connect seamlessly to Azure Data Lake Storage to read and write data.
2. **Data Cleaning**: Remove unnecessary prefixes, non-numeric characters, and filter records based on specific criteria.
3. **Data Transformation**: Pivot the data for a better representation of population distribution by age groups across countries.
4. **ETL Process**: Create an efficient Extract, Transform, Load (ETL) process with PySpark and SQL for easy scalability and reusability.

## Key Steps

1. **Azure Configuration**:
   - Set up PySpark with the necessary access configuration to Azure Data Lake Storage (ADLS).
   - Verify connectivity by listing files in the ADLS container.

2. **Data Loading**:
   - Load a raw TSV file from ADLS into a PySpark DataFrame.
   - Define the schema, delimiters, and header to efficiently read and structure the data.

3. **Data Transformation and Cleaning**:
   - **Split and Extract Columns**: Separate combined fields (age group and country code) into distinct columns for easier data manipulation.
   - **Data Filtering**: Exclude entries where the `country_code` exceeds two characters in length.
   - **Regex-Based Cleaning**: Remove alphabetic characters from `population_2019`, leaving only numeric values and decimal points.
   - **Column Renaming and Selection**: Make column names intuitive and select only necessary columns for further processing.

4. **Pivot Operation**:
   - Use PySpark’s pivot functionality to reshape the data, making each age group a column and each country a row.
   - Sum the population by age group for each country to provide an aggregated view of population distribution.

5. **Data Output**:
   - Write the transformed data back to ADLS in JSON format, storing it in a separate container for easy access and further analysis.

## Code Highlights

- **PySpark and SQL Integration**: This project utilizes both PySpark DataFrame operations and SQL syntax, providing a flexible approach to data cleaning and querying.
- **Regex-Based Cleaning**: Regular expressions are used to remove unwanted characters from specific fields, showcasing advanced data manipulation techniques.
- **Pivoting for Aggregation**: The pivot operation effectively summarizes the data by grouping population by age and country, making the data more insightful for analysis.

## Setup Instructions

### Prerequisites
- **Databricks Workspace** or a PySpark environment with Azure access
- **Azure Data Lake Storage (ADLS)** with necessary permissions
- **Python 3.x** and **PySpark**

### Steps
1. Clone this repository to your Databricks workspace or local PySpark environment.
2. Ensure the necessary configurations for ADLS are set up, including account name and key.
3. Upload the raw population data TSV file to your ADLS account under the designated container (`raw`).
4. Run the notebook to execute the data pipeline, with output data saved in JSON format in the `processed` container.
