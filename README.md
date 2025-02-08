# Olympic Dataset Power BI Report

## Overview
This project analyzes an **Olympic dataset** using **Power BI**. The interactive report includes **DAX analysis** and multiple filtering options for deeper insights into the data.

## Features
- **Fully interactive Power BI report** with dynamic filtering
- **DAX (Data Analysis Expressions) calculations** to derive insights
- **Multiple filtering features** to refine data views
- **Data collection using Python**

## Data Collection
The dataset was collected using a Python script. Below is the script used for data extraction:

```python
import kaggle
import os
import pandas as pd

# Set Kaggle API credentials directory
os.environ['KAGGLE_CONFIG_DIR'] = 'Your_pc_kaggle_folder_path'  # Update this path to your Kaggle configuration directory

# Specify the dataset identifier
dataset = 'piterfm/paris-2024-olympic-summer-games'

# Set the download path
download_path = 'provide_destination_for_folder' # Change this to your preferred download directory

# Remove existing files in the folder to prevent duplicates or outdated files
for file in os.listdir(download_path):
    file_path = os.path.join(download_path, file)
    try:
        if os.path.isfile(file_path):
            os.unlink(file_path)  # Delete the file
            print(f"Deleted {file_path}")
    except Exception as e:
        print(f"Error deleting {file_path}: {e}")

# Download the dataset using the Kaggle API and unzip the files
kaggle.api.dataset_download_files(dataset, path=download_path, unzip=True)

# List of CSV files to be imported
csv_files = [
    'athletes.csv',
    'events.csv',
    'medallists.csv',
    'medals.csv',
    'medals_total.csv',
    'schedules.csv',
    'schedules_preliminary.csv',
    'teams.csv',
    'torch_route.csv',
    'venues.csv'
]

# Initialize a dictionary to hold DataFrames
dataframes = {}

# Iterate through each CSV file and load it into a DataFrame
for file in csv_files:
    # Construct the full path to the CSV file
    file_path = os.path.join(download_path, file)
    
    # Load the CSV file into a Pandas DataFrame
    df = pd.read_csv(file_path)
    
    # Add the DataFrame to the dictionary using the file name as the key
    table_name = file.split('.')[0]  # Remove the .csv extension
    dataframes[table_name] = df
```

## Dataset
The dataset used in this project can be found here:
[https://www.kaggle.com/datasets/piterfm/paris-2024-olympic-summer-games]



## Installation & Usage
1. Install Power BI Desktop from [Microsoft](https://powerbi.microsoft.com/)
2. Open the Power BI file (`.pbix` format) included in this repository
3. Ensure the dataset is linked correctly
4. Explore the interactive report

## Future Enhancements
- Add more advanced DAX measures
- Enhance visualizations with custom Power BI visuals
- Incorporate real-time data updates

##Project Demo Video
https://github.com/user-attachments/assets/57811683-5a7b-44f4-883a-b9911a62b7ea
