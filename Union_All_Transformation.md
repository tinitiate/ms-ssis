 ![tinitiate.com ssis](/images/tiniaitessis.png)
# Union All

* The Union All transformation is used to combine the rows from two or more input datasets into a single output dataset. 
* This transformation simply concatenates the rows from the input datasets, and it does not perform any sorting or filtering.
* We can configure the Union All transformation by connecting multiple source components to it and mapping the columns appropriately.

## Steps:

1. Launch SQL Server Data Tools (SSDT) or SQL Server Business Intelligence Development Studio (BIDS) and create a new SSIS package project.

2. Drag and drop a Data Flow Task onto the Control Flow design surface.

   

   ![](/images/merge_join/merge_files_1.png)

   

3. Double-click the Data Flow Task to switch to the Data Flow tab.

4. Within the Data Flow tab, drag and drop the source components for the two datasets (Flat File Sources) you want to merge join. 

   

   ![](/images/merge_join/merge_files_2.png)

   

5. Configure the source components by providing the necessary connection information and selecting the source files.

   

   ![merge_files_7](/images/union_all/image-1.png)

   

   ![merge_files_7](/images/union_all/image-2.png)

   

   ​													![merge_files_7](/images/union_all/image-4.png)

   

   ​												 ![merge_files_7](/images/union_all/image-5.png)	

   

6. Drag and drop the Union All transformation from the Toolbox onto the Data Flow design surface .

   

   ![](/images/union_all/image-6.png)

   

7. Connect the Flat File Source to Union All Transformation.

   

   ![](/images/union_all/image-7.png)

   

8. Drag and drop the OLE DB Destination transformation from the Toolbox onto the Data Flow design surface.



![](/images/union_all/image-8.png)



14. Connect the Union All Transform and the OLE DB Destination.

    

    ![](/images/union_all/image-9.png)

    

15. Double-click the OLE DB Transformation to open its editor and click **New** to select the connection.



![](/images/union_all/image-10.png)



16. Select the Data Connection needed and click **OK**. If we now click **New** to create a new Data Connection.

    

​												      ![](/images/union_all/image-11.png)



16.  On the OLE DB Destination Editor Select the "Table or View" from the **Data access mode** and click **New**.

    

​	 ![](/images/union_all/image-12.png)



16.  On the Create Table change the Name of the Table and click  **OK**

    

   ![](/images/union_all/image-13.png)

    

17. On the OLE DB Destination Editor select the **Mappings** tab and verify the columns mappings and click **OK**

    

    ![](/images/union_all/image-14.png)

18. The Final Data Flow Task should like this.

    

    ​												![](/images/union_all/image-15.png)

    

19. To Execute the package go to the solution and select the package you want to execute and right click and click **Execute Package**.

    

​													  ![](/images/union_all/image-16.png)
