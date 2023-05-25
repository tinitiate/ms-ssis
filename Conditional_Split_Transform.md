 ![tinitiate.com ssis](/images/tiniaitessis.png)
 
# Conditional Split Transformation
* The Conditional Split transform in SSIS (SQL Server Integration Services) is a data transformation component that allows you to split data rows based on specified conditions. 
* It routes the rows to different output paths based on the evaluation of these conditions.
* The Conditional Split transform enables you to apply conditional logic to your data flow, allowing you to segment, filter, or manipulate data based on specific conditions.
* It provides flexibility in data processing within SSIS packages by dynamically directing rows to different paths based on the evaluation of expressions.

## Steps to Split the data of Flat File Source to Multiple Flat File Destinations using **Conditional Split**.
1.  Open SSIS Designer.
2.  In the SSIS Toolbox, drag and drop a **Data Flow Task** onto the design surface.

     ![Data Flow Task](/images/Data_Flow.png)
     
3.  Double click the **Data Flow Task** to go to **Data Flow** Tab.
4.  Drag and Drop the **Flat File Source** onto the design surface.

    ![OLE DB Source](/images/conditional_split/image-2.png) 
    
    
5.  Right click on the **Flat File** and select **Edit**

    ![OLE DB Source](/images/conditional_split/image-3.png) 
    
6.  On the **Flat File Source Editor** click **New** for the connection manager.
    ![OLE DB Source](/images/conditional_split/image-4.png) 
7.  On the **Flat File Connection Manager Editor** `Change the Connection Manager Name` Select the file you want by clicking browse and select the **Columns Names in the first data row**.

    ![OLE DB Source](/images/conditional_split/image-5.png)
    
8.  Click on the Columns tab click OK.

    ![OLE DB Source](/images/conditional_split/image-6.png)  
    
9.  On the **Flat File Source Editor** select the `Retain null values from the source as null values in the data flow` and click **OK**.

    ![OLE DB Source](/images/conditional_split/image-7.png)  
    
10. Drag and Drop the **Conditional Split** onto the design surface.

    ![character-map](/images/conditional_split/image-8.png) 
    
11. Connect the **Flat File Source** and **Conditional Split**.

    ![character-map](/images/conditional_split/image-9.png) 
    
12. Double click the **Conditional Split** to open the **Conditional Spli Transformation Editor**.

13. Under the **Output Name** enter `Female` and **under Condition** enter `[Gender]== "Female"`, repeat the same for `Male` with Condtion `[Gender]== "Male" and click `OK`.

    ![character-map](/images/conditional_split/image-10.png) 
    
14. Drag and Drop two **Flat File Destination** onto the design surface.

    ![character-map](/images/conditional_split/image-11.png) 
    
15. Connect the **Conditional Split** and First **Flat File Destination** and in the `Input Output Selection` select **Female** from ouput drop down.

    ![character-map](/images/conditional_split/image-12.png) 
    
16. Repeat the step 15 for Second **Flat File Destination** and in the `Input Output Selection` select **Male** from ouput drop down.
17. It should look this after the connections.
    
   ![character-map](/images/conditional_split/image-13.png) 
 
18. Double click the **Flat File Destination** to open the **Editor**
19. On the **Flat File Destination Editor** click **New** which open the **Flat File Format** and select **Delimited** and click **OK**.

    ![Flat File Destination](/images/conditional_split/image-14.png) 
    
20. On the **Flat File Connection Editor** click **Browse** to select the **CSV File**.

    ![Flat File Destination](/images/conditional_split/image-15.png) 
    
21. On the **Flat File Connection Editor** verify the **CSV File** and select **Column names in the first data row**.

    ![Flat File Destination](/images/conditional_split/image-16.png) 
    
22. Click on the **Columns** tab click **OK**

    ![Flat File Destination](/images/conditional_split/image-17.png) 
    
23. Click on the **Mappings** tab verify the columns mappings and click **OK**

    ![Flat File Destination](/images/conditional_split/image-18.png) 

24. Repeat the steps 18 through 23 for the Second **Flat File Destination**.
25. Right click on the package in Solution Explorer and select **Execute the package**.

    ![Execute Package](/images/conditional_split/image-19.png) 
