![tinitiate.com ssis](/images/tiniaitessis.png)

# Flat File Import with Data Conversion and Derived Column 

## Flat File Source

*  This task is used to read data from a flat file, such as a CSV file.
*  It allows you to specify the file path, delimiter, and text qualifier settings. 
* We can also define the columns by mapping them to the corresponding columns in the CSV file.

## Data Conversion

* This task is used to convert the data types of columns in the data flow.
* It allows you to convert columns from one data type to another. 
* For example, you can convert a string column to an integer column or a date column to a string column.
*  This task is useful when the source data types don't match the destination data types.

## Derived Column

* This task is used to create new columns or modify existing columns based on expressions.
*  It allows you to define expressions using functions, operators, and constants to derive values for new columns. 
* For example, you can concatenate two columns, perform mathematical calculations, or extract substrings using this task.

## OLE DB Destination

* This task is used to write data to a destination table or view in an OLE DB-compliant database. 
* It allows us to specify the destination database and table or view where the data will be loaded. 
* We can map the input columns from the previous tasks to the corresponding destination columns. 
* This task is commonly used to load data into SQL Server databases.

## Steps to Import data from CSV File to SQL Server using Data Conversion and Derived Column 

1. Create a new SSIS package or open an existing one.

   - Right-click on the Control Flow tab and select "New SSIS Package" or open an existing package.

2. Add a Data Flow Task to the Control Flow tab.

   - Drag and drop the Data Flow Task from the SSIS Toolbox onto the Control Flow tab.

     ![Data_Flow](/images/Data_Flow.png)

3. Double-click the Data Flow Task to switch to the Data Flow tab.

4. Drag and drop a Flat File Source component onto the design surface.

   - Drag the Flat File Source from the SSIS Toolbox and drop it onto the Data Flow tab.

     ![Data_Flow](/images/flat_file_1.png)

5. Double-click the Flat File Source to configure it.

   - In the Flat File Source Editor, click on "Connection Manager" and select the appropriate Flat File Connection Manager or create a new one by clicking "New...".

     ![Data_Flow](/images/flat_file_2.png)

     ![Data_Flow](/images/flat_file_3.png)

   - Specify the CSV file path in the "File name" field.

   - Configure the delimiter and text qualifier settings according to your CSV file.

   - Click on "Columns" to define the columns by mapping them to the corresponding columns in the CSV file.

6. Drag and drop a Data Conversion Task onto the design surface.

   - Drag the Data Conversion Task from the SSIS Toolbox and drop it onto the Data Flow tab.

7. Connect the Flat File Source to the Data Conversion Task.

   - Click on the green arrow icon on the Flat File Source and drag it to the Data Conversion Task.

8. Double-click the Data Conversion Task to configure it.

   - In the Data Conversion Transformation Editor, click on "Input Columns" and select the columns that need conversion.
   - Specify the desired data types for the selected columns in the "Output Alias" column.
   - Configure the data conversion settings as per your requirements.

9. Drag and drop a Derived Column Task onto the design surface.

   - Drag the Derived Column Task from the SSIS Toolbox and drop it onto the Data Flow tab.

10. Connect the Data Conversion Task to the Derived Column Task.

- Click on the green arrow icon on the Data Conversion Task and drag it to the Derived Column Task.

1. Double-click the Derived Column Task to configure it.
   - In the Derived Column Transformation Editor, click on "Derived Column Name" and specify a name for the derived column.
   - Define the expression for the derived column by clicking on "Expression" and specifying the required transformation logic.
2. Drag and drop an OLE DB Destination component onto the design surface.
   - Drag the OLE DB Destination from the SSIS Toolbox and drop it onto the Data Flow tab.
3. Connect the Derived Column Task to the OLE DB Destination.
   - Click on the green arrow icon on the Derived Column Task and drag it to the OLE DB Destination.
4. Double-click the OLE DB Destination to configure it.
   - In the OLE DB Destination Editor, click on "Connection Manager" and select the appropriate OLE DB Connection Manager or create a new one by clicking "New...".
   - Choose the destination table or view where the CSV data will be loaded.
   - Map the input columns from the Derived Column Task to the destination columns in the OLE DB Destination.
5. Save and close the Data Flow tab.
6. Execute the SSIS package to load the CSV data into the OLE DB destination.
   - Right-click on the Control Flow tab and select "Execute Package" to run the package.