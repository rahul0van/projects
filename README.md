# Lost and Found Animal Data Analysis
The dataset contains the animals (dog breeds) lost and found in Vancouver since 1999. The dataset contains 674 records and 6 attributes (Breed, Color, Date, Name, Sex, and State). There are 5 breeds of dogs listed, and its gender could be (M = Male, F = Female, M/N or F/S = Neutered/Spayed and X = Unknown). The pets are either “Matched” i.e. reunited with their owner, “Lost” which means still missing, and “Found” recently found but not matched.  From this dataset, we want to answer: “What is the total percent of lost and found animals in the dataset by Breed?”


## Data Wrangling

### Project Description
This phase involved cleaning and transforming the dataset of lost and found animals in Vancouver. The objective was to prepare the data for analysis by ensuring accuracy, consistency, and completeness.

### Project Title
**Data Wrangling for Lost and Found Animal Analysis**

### Objective
To handle inconsistencies and prepare a high-quality dataset for analysis, ensuring that it meets the requirements for subsequent descriptive and exploratory phases.

### Dataset
The dataset consisted of **674 records** detailing animal attributes such as breed, color, date, name, gender, and state (e.g., Lost, Found, or Matched).

### Methodology

#### **1. Data Ingestion**
- **Storage Setup**:
  - Created an Amazon S3 bucket, “vcaci-raw-rah,” to store the raw dataset securely.
  - Ensured data was stored in its original format for reprocessing if needed.
- **Folder Organization**:
  - Organized data into structured folders under the “lost_and_found_pets” directory for easy management.
- **Storage Class Selection**:
  - Used Standard-AI for storage efficiency, suitable for data updated infrequently.

#### **2. Data Profiling**
- **Dataset Connection**:
  - Connected the raw dataset in AWS Glue DataBrew for profiling and quality assessment.
- **Profile Job Execution**:
  - Ran profiling jobs to generate insights about missing values, duplicates, and overall dataset health.
- **Insights Gathering**:
  - Identified 2% missing values and less than 1% duplicates in attributes like Color, Name, and Sex.
- **Storage of Results**:
  - Saved profiling results in a designated folder within the transformed bucket.

#### **3. Data Cleaning**
- **Cleaning Recipe Creation**:
  - Developed a cleaning recipe using AWS Glue DataBrew to handle invalid and missing values.
- **Attribute-Specific Fixes**:
  - Standardized date formats and removed invalid characters from attributes such as Name and Color.
  - Deleted rows with missing or null values in key attributes like Name and Sex.
- **Output Configuration**:
  - Stored cleaned data in two formats:
    - User-readable (CSV) for manual use.
    - System-efficient (Parquet) for automated analytics workflows.

### Tools and Technologies
- **AWS Services**: S3, Glue DataBrew
- **Programming**: Python for data preprocessing (optional)
- **Data Formats**: CSV and Parquet

### Deliverables
- A cleaned dataset with **434 records** ready for further analysis.
- Outputs in user-readable (CSV) and system-efficient (Parquet) formats.

---

## Descriptive Analysis

### Project Description
This phase aimed to summarize key metrics about the lost and found animals, including their distribution by breed, state, and gender.

### Project Title
**Descriptive Analysis of Lost and Found Animals in Vancouver**

### Objective
To provide an overview of the dataset, highlighting trends and patterns in lost and found animals.

### Methodology

#### **4. Data Pipeline Design**
- **Source Loading**:
  - Extracted transformed and cleaned data from the “data-cleaning/System” folder in S3.
- **Transformation**:
  - Dropped unnecessary columns like Name to focus on relevant analysis.
  - Aggregated data by breed and state to derive metrics, such as counts of lost and found animals.
- **Schema Modification**:
  - Used change schema nodes to rename columns for better clarity.
- **Derived Metrics**:
  - Created new attributes (e.g., `found_percent`, `lost_percent`) using SQL expressions.
- **Result Storage**:
  - Saved the final pipeline output in separate folders for system and user use.

### Tools and Technologies
- **AWS Services**: Glue Visual ETL, Athena
- **Visualization**: CloudWatch Dashboards, Tableau

### Deliverables
- A summary report detailing animal distributions by breed, state, and gender.
- Visualizations to communicate trends effectively.

---

## Exploratory Analysis

### Project Description
This phase explored relationships between attributes such as spayed/neutered status, breed, and likelihood of recovery.

### Project Title
**Exploratory Analysis of Lost and Found Animal Trends**

### Objective
To uncover patterns and relationships within the data, such as whether spayed/neutered animals are more likely to be found.

### Methodology

#### **5. Data Protection**
- **Encryption**:
  - Enabled server-side encryption using AWS Key Management Service (KMS).
- **Versioning**:
  - Configured bucket versioning for data integrity and recovery.
- **Backup Setup**:
  - Created backup buckets and implemented replication rules for high availability.

#### **6. Data Governance**
- **Quality Check Pipeline**:
  - Designed an ETL job to detect sensitive data and evaluate data quality.
- **Criteria Definition**:
  - Set rules for completeness and uniqueness of specific columns.
- **Segregation of Data**:
  - Divided data into “Passed” and “Failed” categories based on quality checks.
- **Result Storage**:
  - Stored passed data in the “Passed” folder and failed data in the “Failed” folder.

#### **7. Data Observability**
- **Dashboard Setup**:
  - Created a custom AWS CloudWatch dashboard to monitor storage usage, object counts, and billing estimates.
- **Alert Configuration**:
  - Set up alarms to notify when object counts exceeded defined thresholds.
- **Audit and Logging**:
  - Integrated AWS CloudTrail to track system logs and user activities.

#### **8. Exploratory Data Enrichment**
- **Feature Engineering**:
  - Derived new attributes (e.g., `is_spayed_neutered`, `is_found`) using SQL transformations.
- **Data Merging**:
  - Joined datasets from different sources based on attributes like Name, Date, and Breed.
- **Enriched Data Output**:
  - Saved enriched datasets in user-readable and system-efficient formats in the curated bucket.

### Tools and Technologies
- **AWS Services**: Glue ETL, Athena
- **Programming**: Python (Pandas, Seaborn for plotting)
- **Visualization**: Tableau, Power BI, AWS QuickSight

### Deliverables
- Insights into recovery trends by breed and spayed/neutered status.
- Data-driven recommendations for improving animal recovery strategies.
- A comprehensive dashboard summarizing exploratory findings.

---

## Conclusion
This project demonstrates a systematic approach to cleaning, summarizing, and exploring a dataset of lost and found animals. Through **data wrangling**, the dataset was made reliable for analysis. **Descriptive analysis** provided an overview of key metrics, while **exploratory analysis** uncovered deeper trends and relationships. The insights generated can assist stakeholders, such as shelters and local authorities, in improving animal recovery rates and designing more effective intervention strategies.


