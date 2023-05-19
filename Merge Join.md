# Merge Join 

* The Merge Join transformation in SQL Server Integration Services (SSIS) is used to combine two sorted datasets based on a common key. 
* It performs a join operation similar to the SQL JOIN clause.
* This tutorial will explain the concept of the Merge Join transformation and guide you through its implementation in SSIS.

# Sort 

* The Sort transformation in SSIS is used to sort data based on one or more columns.
*  It arranges the input rows in ascending or descending order based on the specified sort key columns. 
* The Sort transformation requires the data to be sorted before using it with certain transformations like Merge Join.

## Steps:

1. Launch SQL Server Data Tools (SSDT) or SQL Server Business Intelligence Development Studio (BIDS) and create a new SSIS package project.

2. Drag and drop a Data Flow Task onto the Control Flow design surface.

   ![](\images\merge_files_1.png)

3. Double-click the Data Flow Task to switch to the Data Flow tab.

4. Within the Data Flow tab, drag and drop the source components for the two datasets (Flat File Sources) you want to merge join. 

   ![](\images\merge_files_2.png)

5. Configure the source components by providing the necessary connection information and selecting the source files.

   ![](\images\merge_files_4.png)

   ![merge_files_5](\images\merge_files_5.png)

   ![merge_files_6](\images\merge_files_6.png)

   ![merge_files_7](\images\merge_files_7.png)

   ![merge_files_8](images\merge_files_8.png)

   ![merge_files_9](images\merge_files_9.png)

6. Drag and drop the Sort transformation from the Toolbox onto the Data Flow design surface and connect the source outputs to the Sort transformations.

   ![](images\merge_files_10.png)

7. Double-click each Sort transformation to open its editor.

8. In the Sort transformation editor, specify the sort key columns by clicking on the Columns tab and selecting the columns from the input dataset that should be used for sorting. You can also choose the sort order (ascending or descending) for each column.

9. Optionally, you can enable the Remove rows with duplicate sort values option to remove duplicate rows during the sorting process.

   ![](images\merge_files_11.png)

10. Drag and drop the Merge Join transformation from the Toolbox onto the Data Flow design surface.

    ![](images\merge_files_12.png)

11. Connect the outputs of the Sort components to the Merge Join transformation component.

12. Double-click the Merge Join transformation to open its editor.

    ![](images\merge_files_13.png)

    ![](C:\Users\sriat\OneDrive\Desktop\ssis\merge_files_14.png)

13. In the Merge Join editor, select the appropriate join type (Inner, Left Outer, Full Outer) based on the requirements.

14. Specify the join key columns by clicking on the Join Columns button and selecting the columns from each input dataset that should be used for the join operation.

    ![](images\merge_files_28.png)

15. Click OK to close the Merge Join editor.

16. Drag and drop the OLE DB Destination transformation from the Toolbox onto the Data Flow design surface.

    ![](images\merge_files_16.png)

    

17. Double-click the Merge Join transformation to open its editor.

    ![](images\merge_files_20.png)

    ![merge_files_21](images\merge_files_21.png)

    ![merge_files_22](images\merge_files_22.png)

    ![merge_files_23](images\merge_files_23.png)

    ![merge_files_24](images\merge_files_24.png)

    ![merge_files_25](images\merge_files_25.png)

    ![merge_files_26](images\merge_files_26.png)

    ![merge_files_27](images\merge_files_27.png)

18. Execute the package to run the Merge Join transformation and merge the two datasets based on the specified join criteria.

    ![](images\merge_files_29.png)
