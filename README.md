# staynest-adf-assignment
# StayNest Azure Data Factory Assignment

## Objective

This project uses Azure Data Factory to move StayNest CSV files
from the raw area of Azure Data Lake Storage Gen2 to the bronze area.

## Storage structure

staynest/
- raw/
  - hotels.csv
  - customers.csv
  - bookings.csv
- bronze/
  - hotels.csv

## Azure Data Factory objects

### Linked service

- ls_staynest_storage
- Connects Azure Data Factory to the StayNest storage account.

### Datasets

- ds_source: points to raw/hotels.csv
- ds_sink: points to the bronze folder
- ds_raw_folder: points to the raw folder for metadata inspection

### Pipeline

- pl_staynest_raw_to_bronze

The pipeline:
1. Copies hotels.csv from raw to bronze.
2. Uses Get Metadata to return the raw folder child items.

## How to run

1. Open the pipeline in Azure Data Factory Studio.
2. Select Debug.
3. Confirm both activities succeed.
4. Check the bronze folder for hotels.csv.
5. Open the Get Metadata output and confirm that all three raw files are listed.

## Result

The pipeline successfully copied hotels.csv to bronze and returned
hotels.csv, customers.csv and bookings.csv through Get Metadata.

## Security

No storage account keys or connection strings are stored in this repository.
