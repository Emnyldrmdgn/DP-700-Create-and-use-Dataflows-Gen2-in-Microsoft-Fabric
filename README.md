# DP-700-Create-and-use-Dataflows-Gen2-in-Microsoft-Fabric
In Microsoft Fabric, Dataflows (Gen2) connect to various data sources and perform transformations in Power Query Online. They can then be used in Data Pipelines to ingest data into a lakehouse or other analytical store, or to define a dataset for a Power BI report.

# README: Create and Use Dataflows (Gen2) in Microsoft Fabric

## Overview

This lab introduces **Dataflows (Gen2)** in **Microsoft Fabric**. You will:
- Create a Fabric-enabled workspace.
- Create a **Lakehouse**.
- Build a **Dataflow (Gen2)** using Power Query Online.
- Ingest and transform data from a CSV file.
- Store data into a lakehouse.
- Add the Dataflow to a **Data Pipeline** for scheduled execution.
- Validate the ingested data.

> 🕒 Estimated time to complete: **30 minutes**  
> 🔐 Note: You need an active **Microsoft Fabric Trial**.

---

## Steps Summary

### 1. Create a Workspace
- Go to [Microsoft Fabric](https://app.fabric.microsoft.com/home?experience=fabric)
- Select **Workspaces > New Workspace**
- Choose a name and enable Fabric capacity (Trial/Premium/Fabric)

### 2. Create a Lakehouse
- Select **Create > Lakehouse**
- Provide a unique name and wait for creation to finish

### 3. Create a Dataflow (Gen2)
- From the workspace, select **Get data > New Dataflow Gen2**
- Import data from CSV:
  - File URL: `https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/orders.csv`
  - Connection: Anonymous
- In Power Query:
  - Add a custom column:  
    ```m
    MonthNo = Date.Month([OrderDate])
    ```
  - Ensure `OrderDate` is of type *Date* and `MonthNo` is *Whole Number*

### 4. Configure Lakehouse as Destination
- In the **Home** tab, select **Add data destination > Lakehouse**
- Choose the workspace and lakehouse created earlier
- Set destination table name as `orders`
- Under settings, disable auto settings and choose **Append**
- Select **Publish** to publish the dataflow

### 5. Add Dataflow to Pipeline
- From the workspace, select **+ New item > Data pipeline**
- Name the pipeline `Load data`
- Add a **Dataflow** activity to the pipeline and select your dataflow
- Save and **Run** the pipeline
- Refresh your lakehouse tables to view the `orders` table

---

## Additional Notes
- You can connect to your Dataflow from **Power BI Desktop** using the *Dataflows (Legacy)* connector
- Transformations can be reused in datasets for reporting and analytics

---

## Clean-Up
To delete the workspace:
- Go to **Workspace settings**
- Under **General**, select **Remove this workspace > Delete**



### Screenshots

![fabriclab5](https://github.com/user-attachments/assets/5cf6a0b3-1f52-4ed0-a6ff-c37355a3cf5e)
![fabriclab5_1](https://github.com/user-attachments/assets/8ba2c652-5655-4712-9ac6-5a5bd0ed23ba)
![fabriclab5_2](https://github.com/user-attachments/assets/076f003a-65e9-41bd-bddf-bc713e4eeaa9)
![fabriclab5_3](https://github.com/user-attachments/assets/2999ff15-eb75-42eb-8780-725bcf987a34)
![fabriclab5_4](https://github.com/user-attachments/assets/6fd81e82-4bb8-4a8f-b8eb-69d083bba959)
![fabriclab5_5](https://github.com/user-attachments/assets/569914d0-7bbb-4a3d-aa63-8c4e5634f6ba)
![fabriclab5_6](https://github.com/user-attachments/assets/c3608695-9ee6-43a0-92d6-fb5322a7763e)
![fabriclab5_7](https://github.com/user-attachments/assets/b62e3126-ef35-440d-9bbf-ce43989f7d65)
<img width="372" alt="fabriclab5_8" src="https://github.com/user-attachments/assets/9ce8d57b-343f-478c-b502-ed449b0b41d1" />
