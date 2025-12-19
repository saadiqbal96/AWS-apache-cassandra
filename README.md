Data Modeling with Apache Cassandra
===================================

📌 Project Overview
-------------------

This project focuses on designing and implementing a **NoSQL data model using Apache Cassandra** for a fictional music streaming startup called **Sparkify**. The goal is to efficiently store and query user activity data to understand how users interact with the app — specifically, which songs are being listened to and under what context.

Unlike relational databases, Apache Cassandra requires data to be **modeled based on query patterns**, not normalized schemas. This project demonstrates how to design denormalized tables optimized for fast reads and specific business questions.

🎯 Project Objectives
---------------------

*   Build an **ETL pipeline** to process raw event data stored in multiple CSV files.
    
*   Create a **denormalized dataset** (event\_datafile\_new.csv) optimized for Cassandra ingestion.
    
*   Design and create **Apache Cassandra tables** aligned with predefined queries.
    
*   Insert transformed data into Cassandra tables using appropriate data types.
    
*   Validate the data model by executing SELECT queries **without using ALLOW FILTERING**.
    

🏗️ ETL Pipeline
----------------

The ETL process includes:

1.  **Extract**
    
    *   Read event data from multiple CSV files stored in a directory.
        
2.  **Transform**
    
    *   Filter relevant columns required for query analysis.
        
    *   Clean and restructure the data into a single consolidated dataset.
        
3.  **Load**
    
    *   Write the transformed data into event\_datafile\_new.csv.
        
    *   Insert records into Apache Cassandra tables using INSERT statements.
        

This pipeline ensures the data is structured efficiently for Cassandra’s partition-based storage model.

🧠 Data Modeling Approach
-------------------------

Apache Cassandra does not support joins or complex aggregations. Therefore, each table in this project is **modeled specifically to answer a single query**.

Key design principles used:

*   Tables are created **per query**, not per entity.
    
*   Data is denormalized to eliminate the need for joins.
    
*   Partition keys are carefully chosen to distribute data evenly.
    
*   Clustering columns define the sort order within each partition.
    
*   Each table uses a **PRIMARY KEY** that uniquely identifies rows.
    

🗄️ Cassandra Tables & Queries
------------------------------

Three tables were created to support the following business questions:

1.  **Retrieve song details by session**
    
    *   Query songs played during a specific session, ordered by item number.
        
    *   Partitioned by sessionId and clustered by itemInSession.
        
2.  **Retrieve user song history for a session**
    
    *   Query songs a specific user listened to during a session.
        
    *   Partitioned by userId and sessionId, clustered by itemInSession.
        
3.  **Retrieve users who listened to a specific song**
    
    *   Query all users who listened to a given song.
        
    *   Partitioned by song, clustered by userId.
        

Each table’s schema and primary key were designed to return results efficiently and **exactly match the query requirements**.

🔑 Primary Key Design
---------------------

Special attention was given to primary key selection:

*   Partition keys were chosen to minimize data skew and maximize query efficiency.
    
*   Clustering columns ensure ordered retrieval of records within partitions.
    
*   Composite primary keys are used where necessary to guarantee row uniqueness.
    

Primary key decisions are documented in the notebook alongside each table creation.

🧪 Validation & Testing
-----------------------

*   Data insertion was validated using SELECT statements.
    
*   Queries return correct and complete results without using ALLOW FILTERING.
    
*   Query outputs were optionally formatted using **pandas DataFrames** for improved readability.
    

📁 Repository Structure
-----------------------

├── event_data/                  # Raw CSV event files

├── event_datafile_new.csv        # Transformed dataset

├── Project_1B_*.ipynb            # ETL and Cassandra notebook

├── README.md                     # Project documentation


🛠️ Technologies Used
---------------------

*   Python
    
*   Apache Cassandra
    
*   CQL (Cassandra Query Language)
    
*   pandas
    
*   Jupyter Notebook
    

🚀 Key Takeaways
----------------

*   Demonstrates effective **NoSQL data modeling** using Cassandra.
    
*   Highlights query-driven schema design.
    
*   Reinforces the importance of partitioning and clustering strategies.
    
*   Provides a scalable approach to analyzing user behavior in a streaming application.

### 👤 Author

**Saad Iqbal**
