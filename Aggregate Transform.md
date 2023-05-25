![tinitiate.com ssis](/images/tiniaitessis.png)

# Aggregate Transform

## Aggregate Transformation

* The Aggregate transformation in SSIS is used to perform aggregate operations on data within the data flow. 
* It allows us to group data based on specified columns and perform various aggregate functions such as SUM, COUNT, AVG, MIN, MAX, etc. on the grouped data.
* The Aggregate transformation is often used for tasks such as calculating totals, averages, counts, or identifying the minimum and maximum values within a dataset.

### Key features of the Aggregate transformation

- Grouping: You can define one or more columns to group the data.
- Aggregations: It supports multiple aggregate functions that can be applied to the grouped data.
- Output: The transformation generates output columns containing the aggregated values.

## OLE DB Destination

* The OLE DB Destination is an SSIS component used to write data from the data flow to a destination table in a database using the OLE DB provider.
*  It allows us to establish a connection to the destination database and specify the target table or view where the data will be loaded.
* The OLE DB Destination is commonly used to load data into SQL Server databases or other databases that support OLE DB connections.

### Key features of the OLE DB Destination

- Connection Manager: You can configure an OLE DB connection manager to connect to the destination database.
- Table Mapping: It enables you to map the columns from the data flow to the columns in the destination table.
- Error Handling: The component provides options to handle errors during the data loading process, such as redirecting error rows or ignoring errors.

## Creating Aggregate transform with flat file Source and Oledb  destination 

1. Create a new SSIS package or open an existing one.

2. Drag and drop a "Data Flow Task" from the "Control Flow" toolbox onto the design surface.

   ![Data_Flow](/images/Data_Flow.png)

3. Double-click on the "Data Flow Task" to switch to the data flow design surface.

4. Drag and drop a "Flat File Source" component from the "Data Flow Sources" toolbox onto the design surface.

   ![flat_file](/images/flat_file.png)

5. Double-click on the "Flat File Source" component to configure it.

6. In the "Flat File Connection Manager" editor, click on "New" to create a new flat file connection manager.

   ![flat_file](/images/Aggregates/image-3.png)

7. In the "Flat File Connection Manager" editor, provide a suitable name for the connection manager and select the CSV file format. Browse and select the CSV file you want to use as the source.

   ![flat_file](/images/Aggregates/image-4.png)

8. Configure the column mappings in the "Columns" tab, ensuring that each column from the CSV file is mapped correctly. Click "OK" to save the settings.

   ![flat_file](/images/Aggregates/image-5.png)

   ![flat_file](/images/Aggregates/image-6.png)

   ![flat_file](/images/Aggregates/image-7.png)

9. Drag and drop an "Aggregate" transformation from the "Data Flow Transformations" toolbox onto the design surface. 

   ![flat_file](/images/Aggregates/image-8.png)

10. Connect the "Flat File Source" component to the "Aggregate" transformation.

    ![flat_file](/images/Aggregates/image-9.png)

11. Double-click on the "Aggregate" transformation to configure it. In the "Aggregate Transformation Editor," you can define the grouping and aggregation operations.

    1. In the "Input Columns" tab, select the columns from the source that you want to group by. Click the "Add" button to include additional columns in the grouping.

    2. In the "Aggregates" tab, click the "Add" button to define aggregation functions for the desired columns. For each column, specify the aggregate function (e.g., SUM, COUNT, AVG) and the output column name.

    3. Once you have defined all the necessary groupings and aggregations, click "OK" to save the settings.

       ![flat_file](/images/Aggregates/image-10.png)

12. Drag and drop an "OLE DB Destination" component from the "Data Flow Destinations" toolbox onto the design surface. 

    ![flat_file](/images/Aggregates/image-11.png)

13. Connect the "Aggregate" transformation to the "OLE DB Destination" component.

    ![flat_file](/images/Aggregates/image-12.png)

14. Double-click on the "OLE DB Destination" component to configure it. In the "OLE DB Connection Manager" editor, select an existing connection manager or create a new one for the destination database.

    ![flat_file](/images/Aggregates/image-14.png)

    ![flat_file](/images/Aggregates/image-15.png)

15. Specify the target table or view in the "Name of the table or view" field.

    ![flat_file](/images/Aggregates/image-16.png)

16. Click "Mappings" to ensure that the columns from the aggregate transformation are correctly mapped to the destination table columns.

    and Click "OK" to save the settings and close the "OLE DB Destination Editor."

​	   ![flat_file](/images/Aggregates/count.png)