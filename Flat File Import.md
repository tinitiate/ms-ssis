![tinitiate.com ssis](/images/tiniaitessis.png)

# Flat File Import

- Create a new SSIS package or open an existing one.

- Add a **Data Flow Task** to the Control Flow tab.

  ![Data_Flow](/images/Data_Flow.png)

- Double-click the **Data Flow Task** to switch to the **Data Flow tab**.

- Drag and drop a **Flat File Source** component and **OLE DB Destination** component onto the design surface.

  ![Data_Flow](/images/flat_file/flat_file_1.png)

- Double-click the **Flat File Source** to configure it. a. Specify the CSV file path and select the appropriate delimiter and text qualifier settings. 

  ![Data_Flow](/images/flat_file/flat_file_2.png)

  ![Data_Flow](/images/flat_file/flat_file_3.png)

  ![Data_Flow](/images/flat_file/flat_file_4.png)

  ![Data_Flow](/images/flat_file/flat_file_5.png)

- Define the columns by clicking on "Columns" and mapping them to the corresponding columns in the CSV file.

  ![Data_Flow](/images/flat_file/flat_file_6.png)

- Connect the **Flat File Source** to the **OLE DB Destination** by dragging a green arrow from the **Flat File Source** to the **OLE DB Destination**.

- Double-click the OLE DB Destination to configure it opens **OLE DB Destination Editor**.

  ![Data_Flow](/images/oledb_destination.png)

  ![Data_Flow](/images/oledb_destination_1.png)

- Select the OLE DB connection manager or create a new one by clicking "New...".

  ![Data_Flow](/images/oledb_destination_2.png)

- Choose the destination table or view where the CSV data will be loaded. 

  ![Data_Flow](/images/flat_file/flat_file_7.png)

  ![Data_Flow](/images/flat_file/flat_file_8.png)

- Map the input columns from the Flat File Source to the destination columns in the OLE DB Destination.

  ![Data_Flow](/images/flat_file/flat_file_9.png)

- Save and close the Data Flow tab.

  ![Data_Flow](/images/flat_file/flat_file_10.png)

- Execute the SSIS package to load the CSV data into the OLE DB destination using one of the options shown below.

  ![Data_Flow](/images/Execute_package.png)

  ![Data_Flow](/images/run_package.png)