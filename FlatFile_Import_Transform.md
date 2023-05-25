![tinitiate.com ssis](/images/tiniaitessis.png)

# Flat File Import

## Flat File Source
* This task is used to read data from a flat file, such as a CSV file. 
* It allows you to specify the file path, delimiter, and text qualifier settings. 
* We can also define the columns by mapping them to the corresponding columns in the CSV file.

## OLE DB Destination
* This task is used to write data to a destination table or view in an OLE DB-compliant database. 
* It allows you to specify the destination database and table or view where the data will be loaded. 
* We can map the input columns from the previous tasks to the corresponding destination columns. 
* This task is commonly used to load data into SQL Server databases.

## Steps to Import data from CSV File to SQL Server
1. Create a new SSIS package or open an existing one.

2. Add a **Data Flow Task** to the Control Flow tab.

    ![Data_Flow](/images/Data_Flow.png)

3. Double-click the **Data Flow Task** to switch to the **Data Flow tab**.

4. Drag and drop a **Flat File Source** component and **OLE DB Destination** component onto the design surface.

    ![Data_Flow](/images/flat_file/flat_file_1.png)

5. Double-click the **Flat File Source** to configure it. a. Specify the CSV file path and select the appropriate delimiter and text qualifier settings. 

    ![Data_Flow](/images/flat_file/flat_file_2.png)

    ![Data_Flow](/images/flat_file/flat_file_3.png)

    ![Data_Flow](/images/flat_file/flat_file_4.png)

    ![Data_Flow](/images/flat_file/flat_file_5.png)

6. Define the columns by clicking on "Columns" and mapping them to the corresponding columns in the CSV file.

   ![Data_Flow](/images/flat_file/flat_file_6.png)

7. Connect the **Flat File Source** to the **OLE DB Destination** by dragging a green arrow from the **Flat File Source** to the **OLE DB Destination**.

8. Double-click the OLE DB Destination to configure it opens **OLE DB Destination Editor**.

    ![Data_Flow](/images/oledb_destination.png)

    ![Data_Flow](/images/oledb_destination_1.png)

9. Select the OLE DB connection manager or create a new one by clicking "New...".

    ![Data_Flow](/images/oledb_destination_2.png)

10. Choose the destination table or view where the CSV data will be loaded. 

    ![Data_Flow](/images/flat_file/flat_file_7.png)

    ![Data_Flow](/images/flat_file/flat_file_8.png)

11. Map the input columns from the Flat File Source to the destination columns in the OLE DB Destination.

    ![Data_Flow](/images/flat_file/flat_file_9.png)

12. Save and close the Data Flow tab.

   ![Data_Flow](/images/flat_file/flat_file_10.png)

13. Execute the SSIS package to load the CSV data into the OLE DB destination using one of the options shown below.

    ![Data_Flow](/images/Execute_package.png)

    ![Data_Flow](/images/run_package.png)
