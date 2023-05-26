 ![tinitiate.com ssis](/images/tiniaitessis.png)
# Merge

* It allows you to combine multiple datasets into a single dataset. 
* It allows you to combine multiple datasets into a single dataset. It provides options for sorting, removing duplicates, and directing the output based on predefined rules. 
* This tutorial will explain the concept of the Merge transformation and guide you through its implementation in SSIS.

# Sort 

* The Sort transformation in SSIS is used to sort data based on one or more columns.
*  It arranges the input rows in ascending or descending order based on the specified sort key columns. 
* The Sort transformation requires the data to be sorted before using it with certain transformations like Merge.

## Steps:

1. Launch SQL Server Data Tools (SSDT) or SQL Server Business Intelligence Development Studio (BIDS) and create a new SSIS package project.

2. Drag and drop a Data Flow Task onto the Control Flow design surface.

   

   ![](/images/merge_join/merge_files_1.png)

   

3. Double-click the Data Flow Task to switch to the Data Flow tab.

4. Within the Data Flow tab, drag and drop the source components for the two datasets (Flat File Sources) you want to merge join. 

   

   ![](/images/merge_join/merge_files_2.png)

   

5. Configure the source components by providing the necessary connection information and selecting the source files.

   

   ![merge_files_7](/images/merge/image-15.png)

   

   ![merge_files_7](/images/merge/image-16.png)

   

6. Drag and drop the Sort transformation from the Toolbox onto the Data Flow design surface and connect the source outputs to the Sort transformations.

   

   ![](/images/merge/image-17.png)

   

7. Connect the Flat File Source to corresponding Sort Transforms.

   

   ![](/images/merge/image-18.png)

   

8. Double-click each Sort transformation to open its editor.

9. In the Sort transformation editor, specify the sort key columns by clicking on the Columns tab and selecting the columns from the input dataset that should be used for sorting. You can also choose the sort order (ascending or descending) for each column.

10. Optionally, you can enable the Remove rows with duplicate sort values option to remove duplicate rows during the sorting process.

   

   ![](/images/merge/image-19.png)

   

11. Drag and drop the Merge Join transformation from the Toolbox onto the Data Flow design surface.

    

    ![](/images/merge/merge-1.png)

    

12. Connect the outputs of the Sort components to the Merge Join transformation component.

    

​						![](/images/merge/merge-2.png)



13. Drag and drop the OLE DB Destination transformation from the Toolbox onto the Data Flow design surface.

    

![](/images/merge/merge-4.png)



14. Connect the Merge Transform and the OLE DB Destination.

    

    ![](/images/merge/image-20.png)

    

15. Double-click the OLE DB Transformation to open its editor and click **New** to select the connection.



![](/images/merge/merge-5.png)



16. Select the Data Connection needed and click **OK**. If we now click **New** to create a new Data Connection.

    

​													![](/images/merge/merge-6.png)



17. On the OLE DB Destination Editor Select the "Table or View" from the **Data access mode** and click **New**.

    

​      											 ![](/images/merge/merge-7.png)



18. On the Create Table change the Name of the Table and click  **OK**

    

​												![](/images/merge/merge-8.png)

​     

19. On the OLE DB Destination Editor select the **Mappings** tab and verify the columns mappings and click **OK**

    

​      										  ![](/images/merge/merge-9.png)



20. The Final Data Flow Task should like this.

    

    ![](/images/merge/merge-10.png)

21. To Execute the package go to the solution and select the package you want to execute and right click and click **Execute Package**.



​															       ![](/images/merge/execute-package.png)
