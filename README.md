# Notebook for joining dispatch data
This notebook will focus on what target of joining data, how the process going and what to do with output

## Scope of work
- Gathering/combining from multiple files into one, call it clean_data, file type: tsv.
- Master SKU will be handling in separated notebook, which returns clean master file, call it clean_SKU.
- Joining clean_data and clean_SKU, group by order and sum of billedCBM

## File management
- Raw masterSKU will be put in MasterSKU folder, the rule is one file at the time, user must delete old file before uploading new one.
- Raw data file will be put in one of those, depending on data has been merged or not:
    - If data has already merged, put it in folder DatatoHandle. xlsx file need to have needed data in first sheet (sheet 1).
    - If data is raw (download from system mail), it must be put in folder DatatoMerge, there is another notebook in charged of merging those file into one for further usage.
- After handling, output will be return to the same folder with notebook:
    - Naming: all output file must have prefix 'clean' with cleaning from raw file, 'output' with result from manipulating dataframe.
    - Included datetime or convention, maybe we need to define naming convention for raw files
    - In tsv format
- Move old file to storage folder, the notebook must have checking step to move old file into storage

## Automation
To be clear, the automation is currently not possible via Make.
All files are stored in Google Drive, so there will be a step to mount Drive when using Google Colab. Moreover, ipynb file just runs manually.

These steps below just to intend that automation would be possible in future
- Folder for upload raw files will be share to the team
- Folder contains storage files also be shared

## Process
Below describes overall processes, each process is defined in each notebook.
### Handling master SKU
- Receive raw file from Drive
- Handling and return clean master SKU file

### Handling data file
- Receive raw data file from Drive
- Handling and return clean data file

### Joining
- From clean master SKU and clean data file, join data frames.
- After joined, use aggregate function to return output file.
    - Order
    - CBM of WH
    - CBM of TP