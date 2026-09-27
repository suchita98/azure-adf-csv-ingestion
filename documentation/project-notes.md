# Project Notes — Azure Data Factory CSV Ingestion

## 1. Project Objective

The objective of this project is to build a simple data ingestion pipeline using Azure Data Factory (ADF).

The pipeline reads an employee CSV file from an Azure Storage input container and copies it to an output container.

This project was created to gain hands-on experience with the fundamental components of Azure Data Factory and understand how a basic cloud data ingestion pipeline works.

## 2. Architecture

```text
Azure Blob Storage
       |
       | employee.csv
       v
   Input Container
       |
       v
Azure Data Factory
   Copy Data Activity
       |
       v
  Output Container
       |
       | employee.csv
       v
Azure Blob Storage
```

## 3. Technologies Used

- Microsoft Azure
- Azure Data Factory
- Azure Blob Storage
- CSV
- GitHub

## 4. Azure Resources

### Storage Account

An Azure Storage Account was used to store the source and destination files.

Two containers were created:

- `input`
- `output`

The source file `employee.csv` was uploaded to the `input` container.

### Azure Data Factory

Azure Data Factory was used to orchestrate the movement of data from the input container to the output container.

## 5. Source File

The source file used in this project is:

`employee.csv`

The file contains the following employee information:

| EmployeeID | Name | Department | Salary |
|------------|------|------------|--------|
| 101 | Ravi | IT | 60000 |
| 102 | Anu | HR | 50000 |
| 103 | Priya | Finance | 65000 |
| 104 | Kiran | IT | 70000 |
| 105 | Meena | Sales | 55000 |

The source file was uploaded to:

```text
Azure Storage → input → employee.csv
```

## 6. Azure Data Factory Pipeline

### Pipeline Name

`PL_Copy_Employees`

The pipeline contains a **Copy Data** activity.

The purpose of the pipeline is to copy the employee CSV file from the input container to the output container.

## 7. Linked Service

### Linked Service Name

`LS_AzureBlob_Employee`

The Linked Service was created to establish a connection between Azure Data Factory and the Azure Storage Account.

Authentication was configured using the Azure Storage Account key.

The connection was tested successfully.

## 8. Source Dataset

### Dataset Name

`DS_Employees_CSV`

Configuration:

- Format: DelimitedText / CSV
- Storage: Azure Storage
- Container: `input`
- File: `employee.csv`
- First row as header: Enabled

This dataset represents the source employee CSV file.

## 9. Sink Dataset

### Dataset Name

`DS_Employees_Output`

Configuration:

- Format: DelimitedText / CSV
- Storage: Azure Storage
- Container: `output`
- File: `employee.csv`

This dataset represents the destination file.

## 10. Copy Data Activity

The Copy Data activity was configured with:

### Source

`DS_Employees_CSV`

### Sink

`DS_Employees_Output`

The Copy Data activity reads the employee data from the source dataset and writes it to the destination dataset.

## 11. Pipeline Execution

The pipeline was executed using the **Debug** option in Azure Data Factory.

The pipeline execution completed successfully.

The execution status was:

`Succeeded`

After the successful execution, the output container was checked to verify that the file had been copied successfully.

## 12. Validation

The following validations were performed:

- Verified that `employee.csv` exists in the `input` container.
- Tested the Azure Storage Linked Service successfully.
- Verified the source dataset configuration.
- Verified the sink dataset configuration.
- Executed the ADF pipeline using Debug.
- Confirmed that the pipeline execution status was `Succeeded`.
- Verified that `employee.csv` was created in the `output` container.

## 13. Key Azure Data Factory Concepts Learned

### Linked Service

A Linked Service defines the connection between Azure Data Factory and an external data store.

### Dataset

A Dataset represents the structure and location of the data used by an ADF pipeline.

### Pipeline

A Pipeline is a logical workflow that contains activities used to perform data processing or movement.

### Copy Data Activity

The Copy Data activity is used to move data from a source system to a destination system.

### Source

The source is the location from which data is read.

### Sink

The sink is the destination where the data is written.

### Debug

Debug allows a pipeline to be executed and tested during development.

### Monitor

Monitor allows pipeline executions and their statuses to be reviewed.

## 14. Project Outcome

Successfully built and tested an Azure Data Factory pipeline that copies a CSV file between two Azure Storage containers.

This project provided hands-on experience with:

- Azure Storage
- Azure Data Factory
- Linked Services
- Datasets
- Copy Data Activity
- Source and Sink configuration
- Pipeline execution
- Pipeline monitoring
- Basic GitHub documentation

## 15. Future Improvements

The project can be extended with additional Data Engineering concepts such as:

- Parameterizing source and destination paths
- Using dynamic file names
- Processing multiple CSV files
- Adding data transformations
- Implementing incremental data loading
- Using Azure Data Lake Storage Gen2
- Adding error handling
- Adding pipeline monitoring and alerts
- Loading the processed data into a database
- Creating a more complete ETL pipeline

## 16. Screenshots

The project screenshots are available in the `screenshots` folder of this repository.

The screenshots demonstrate:

1. Source `employee.csv` in the input container
2. Azure Data Factory pipeline
3. Successful pipeline execution
4. Output `employee.csv` in the output container
