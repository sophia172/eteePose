
---
17th Oct 2024

### **1. Overview**
This document outlines the data management practices for machine learning projects, focusing on data storage, organisation, and access. The primary storage options are:
- **Google Drive** for collaboration and smaller datasets (current stage).
- **Google Cloud Storage** for large datasets and more secure, scalable storage.

The data will be categorised into two types:
- **Raw Data**: The original, unprocessed datasets.
- **Processed Data**: Datasets that have been cleaned, transformed, and prepared for model training.
- **Published Data**: Datasets that have been cleaned and used in the paper submission.

### **2. Data Storage Locations**

#### **2.1 Google Drive**

Google Drive will be used for:
- Sharing smaller datasets that require collaborative access across team members.
- Documentation, such as data dictionaries and metadata descriptions.
- Quick access to small processed datasets or samples for analysis.

**Structure**:
- `/Shared Drives/R&D/2_SWEE/_AI Division/Database/<Project Name>/raw/` — For storing raw datasets.
- `/Shared Drives/R&D/2_SWEE/_AI Division/Database/<Project Name>/processed/` — For storing processed datasets (e.g., cleaned CSV files, pickle file).

**Key Guidelines**:
- Only store small datasets (less than 15 GB) on Google Drive.
- Regularly back up datasets to Google Cloud Storage.
- Provide appropriate read/write permissions for team members based on their roles.

#### **2.2 Google Cloud Storage (GCS)** (not applicable yet)

Google Cloud Storage will be used for:
- Storing large datasets that is beyond 15 GB.
- Ensuring data security and scalability.
- Backing up both raw and processed datasets to prevent data loss.
- Storing data that requires more robust access control or integration with Google Cloud services (e.g., BigQuery, Dataflow).

**Structure**:
- `gs://<bucket_name>/raw/` — Store raw datasets directly uploaded to Google Cloud.
- `gs://<bucket_name>/processed/` — Store processed data after cleaning, transformation, and feature engineering.

**Key Guidelines**:
- For datasets larger than 15 GB or those requiring frequent machine learning pipeline access, store data in Google Cloud Storage.
- Enable lifecycle management for automatic deletion of older processed data (e.g., versions older than a certain date).
- Enable versioning in the GCS bucket to track changes to critical datasets.

### **3. Data Organisation and Naming Conventions**
Maintaining a consistent naming and organisational scheme is essential for efficient data management.

#### **3.1 Folder Structure** ([example](https://drive.google.com/drive/folders/1bwECBHhvY0YvXJyn6SpFpj-Ph-hZ2-mx?usp=sharing))
- **Raw Data**: Contains the original data as obtained from sources. 
  - Sub-folders based on data sources, e.g., `/raw/date/individual_id/sensor`
  - Files should be named in the format: `movement_repeatition.csv`
  - Add **Metadata** to include Hardware information, individual information and environment information in `.yml` file.
	```yml
	height: 160 # cm
	weight: 50 # kg
	foot_size: 20 # cm?
	gendar: F
	hand: right # right/left handed
	location_ele_map:
	  - [39, 35, 10, 22]
	  - [12, 36, 9, 21]
	  - [13, 37, 8, 20]
	  - [14, 0, 7, 19]
	  - [15, 1, 6, 18]
	  - [16, 2, 5, 11]
	  - [17, 3, 4, 38]
	
	pressure_ele_map:
	  - [23, 34]
	  - [24, 33]
	  - [25, 32]
	  - [26, 31]
	  - [27, 30]
	  - [28, 29]
	
	ui_grid:
	  - 13
	  - 6
	  - 6 # (row in one module, column number in one module, number of module), MCU at left

```

- **Processed Data**: Contains data that has been cleaned and processed.
  - Sub-folders based on the processing date, e.g., `processed/date/sensorName/`, 
  - Files should be named in the format: `processed_version_date.csv`

#### **3.2 File Naming Convention**
- Use clear, descriptive file names.
  - For **raw data**: `/raw/date/individual_id/sensorName/*/set1_1.csv`. 
    - `set1` means the first sequence of movement. 
    - `_1` means the first trial of this set.
  - For **processed data**: `processed/date/sensorName/YYYYMMDD_1_set1_1.csv`
    - `YYYYMMDD` refers to the date this data was processed
    - `_1_` refers to the data is from person 1.
    -  `set1_1` is the same as file name in the **raw data** folder
- Use versioning (`v1`, `v2`, etc.) to track different iterations of the same dataset.
- Add log `.yml` for how this data is processed
	```yml
	20221019_1_set_1_1:
	  date_folder: '20221019'
	  foot_size: 20
	  gendar: F
	  hand: right
	  height: 160
	  individual: '1'
	  keypoint_recording: path
	  marker_set_path: path
	  mat_recording: path
	  set: set_1_1
	  weight: 50
```

### **4. Data Access Control and Permissions**

#### **4.1 Google Drive**
- Use Google Drive’s sharing features to control access.
  - **Read-Only**: For team members who only need to view data.
  - **Edit Access**: For team members who are responsible for uploading or updating datasets.
- Only grant **Edit Access** to the raw data folder to authorized personnel (data engineers or project leads).

#### **4.2 Google Cloud Storage**
- Use Google Cloud IAM (Identity and Access Management) to control access.
  - Grant specific roles such as **Storage Object Viewer** (read-only) and **Storage Object Admin** (full access) to team members as necessary.
  - Create service accounts for machine learning workflows to securely access data in GCS buckets.
- **Audit Logs**: Enable audit logging on GCS to track who accesses and modifies data.

### **5. Data Versioning and Backup**

#### **5.1 Versioning**
- Enable **versioning** for all raw and processed datasets in Google Cloud Storage.
- Ensure that when a new version of a dataset is created (either raw or processed), the older version is not deleted immediately to prevent accidental data loss.

#### **5.2 Backup**
- Set up **automated backups** for Google Drive data using Google Takeout.
- Use **Google Cloud Storage Lifecycle Management** to automate the transition of older processed data to cheaper storage classes
- Maintain regular backups of the raw and processed data in a separate GCS bucket.

### **6. Data Processing Pipeline**
- All data processing should be tracked and version-controlled using tools like **Git** or **DVC (Data Version Control)**.
- Processed data should be stored in the `processed` folder, with logs detailing the transformations applied to the data.
- Maintain a **README** file or **YML** file in each `processed` subfolder to track the operations performed on raw data (e.g., cleaning, imputation, feature selection).

### **7. Data Security and Compliance**

#### **7.1 Security**
- Ensure **data encryption** is enabled for both Google Drive and Google Cloud Storage (GCS).

#### **7.2 Compliance**
- Ensure that the storage of data complies with all relevant legal and regulatory requirements, including:
  - **Data retention policies** (how long data should be stored).
  - **Data anonymization** for datasets containing personally identifiable information (PII).
	- Refer to person in number instead of name

### **8. Data Retention and Deletion**
- Define **retention periods** for both raw and processed data.
  - Raw data: Retain indefinitely or for a defined period (e.g., 5 years) depending on project requirements.
  - Processed data: Retain for a shorter period (e.g., 1-2 years) or until the project concludes.
- Implement **automatic deletion policies** in Google Cloud Storage using lifecycle management rules.
  - Raw data: No automatic deletion without project lead approval.
  - Processed data: Set rules to delete data older than a defined threshold (e.g., 6 months).

### **9. Data Documentation**
- Maintain proper documentation for all datasets, including:
  - **Data Dictionary**: Describes the meaning, units, and types of data in both raw and processed forms.
  - **Metadata**: Include information on data sources, data collection dates, processing steps, and any data-related issues.
  - **Data Walkthrough**: a slide including video, image to explain where the data is from. How each set of movement if performed. 

### **10. Monitoring and Auditing**
- Regularly monitor data usage and storage limits.
- Perform audits on the data management system to ensure compliance with the guidelines and that no sensitive data is improperly handled.

### **11. Data Publish**
- Publish data on TG0UK **GitHub** with readme file to explain 
---

This **Data Management Guideline** ensures that your machine learning project has a robust framework for handling raw and processed data while maintaining security, accessibility, and compliance.