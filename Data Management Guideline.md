

---

## **Data Management Guideline for Machine Learning Project**

### **1. Overview**
This document outlines the data management practices for machine learning projects, focusing on data storage, organisation, and access. The primary storage options are:
1. **Google Drive** for collaboration and smaller datasets (current stage).
2. **Google Cloud Storage** for large datasets and more secure, scalable storage.

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

- **Processed Data**: Contains data that has been cleaned and processed.
  - Sub-folders based on the stages of processing, e.g., `/processed/cleaned/`, `/processed/features/`
  - Files should be named in the format: `processed_version_date.csv`

#### **3.2 File Naming Convention**
- Use clear, descriptive file names.
  - For **raw data**: `raw_source_version_YYYYMMDD.csv`
  - For **processed data**: `processed_cleaned_version_YYYYMMDD.csv`
- Use versioning (`v1`, `v2`, etc.) to track different iterations of the same dataset.

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
- Set up **automated backups** for Google Drive data using Google Takeout or third-party backup solutions.
- Use **Google Cloud Storage Lifecycle Management** to automate the transition of older processed data to cheaper storage classes (e.g., Nearline or Coldline).
- Maintain regular backups of the raw and processed data in a separate GCS bucket.

### **6. Data Processing Pipeline**
- All data processing should be tracked and version-controlled using tools like **Git** or **DVC (Data Version Control)**.
- Processed data should be stored in the `processed_data` folder, with logs detailing the transformations applied to the data.
- Maintain a **README** file in the `processed_data` folder to track the operations performed on raw data (e.g., cleaning, imputation, feature selection).

### **7. Data Security and Compliance**

#### **7.1 Security**
- Ensure **data encryption** is enabled for both Google Drive and Google Cloud Storage (GCS).
- Use **GCS IAM roles** to restrict access to sensitive data, ensuring compliance with relevant privacy regulations (e.g., GDPR, HIPAA).
- For highly sensitive data, consider additional encryption measures (e.g., client-side encryption) before storing in GCS.

#### **7.2 Compliance**
- Ensure that the storage of data complies with all relevant legal and regulatory requirements, including:
  - **Data retention policies** (how long data should be stored).
  - **Data anonymization** for datasets containing personally identifiable information (PII).

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

### **10. Monitoring and Auditing**
- Regularly monitor data usage and storage limits.
- Perform audits on the data management system to ensure compliance with the guidelines and that no sensitive data is improperly handled.

### **11. Data Publish**
- Publish data on github with .md file 
---

This **Data Management Guideline** ensures that your machine learning project has a robust framework for handling raw and processed data while maintaining security, accessibility, and compliance.