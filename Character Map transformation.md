 ![tinitiate.com ssis](/images/tiniaitessis.png)
# Character Map transformation
* The term "Character Map transformation" typically refers to a process of converting characters or symbols from one set or encoding system to another.
* It involves mapping each character from the source encoding to its corresponding character in the target encoding.
* The Character Map Transformation in `SSIS` is a component that enables the modification of the casing of the input column.

## Steps to change the Column casing of OLE DB Source Column to Flat File Destination using **Character Map**.
1.  Open SSIS Designer.
2.  In the SSIS Toolbox, drag and drop a **Data Flow Task** onto the design surface.
     ![Data Flow Task](/images/Data_Flow.png)
4.  Double click the **Data Flow Task** to go to **Data Flow** Tab.
5.  Drag and Drop the **OLE DB Source** onto the design surface.
    ![OLE DB Source](/images/character_map/OLEDB_Source.png) 
6.  Right click on the **OLE DB Source** and select **Edit**
    ![OLE DB Source](/images/character_map/OLEDB_Source-1.png) 
7.  On the **OLE DB Source Editor** click **New** for the connection manager.
    ![OLE DB Source](/images/character_map/OLEDB_Source-2.png) 
8.  On the **Configure OLE DB Connection Manager** Select the desired Data Connection and click **OK**.
    ![OLE DB Source](/images/character_map/OLEDB_Source-3.png)
9.  On the **OLE DB Source Editor** Select the **Table or view** in the **Data access mode** drop down and select the table we want to work with.
    ![OLE DB Source](/images/character_map/OLEDB_Source-4.png)  
10. Select the **Columns** Tab and check if all the mappings are correct and click **OK**.
    ![OLE DB Source](/images/character_map/OLEDB_Source-5.png)  
11. Drag and Drop the **Character Map** onto the design surface.
    ![character-map](/images/character_map/character-map.png) 
12. Connect the **OLE DB Source** and **Character Map**.
    ![character-map](/images/character_map/character-map-2.png) 
13. Double click the **Character Map** to open the **Character Map Transform Editor**.
14. Select the "AddressLine1" collumn from the input columns and in the **Destination** slect `In-place change` and in the **Operation** select the `Lowercase` and click **OK**

    ![character-map](/images/character_map/character-map-3.png) 
    
15. Select the "City" collumn from the input columns and in the **Destination** slect `New Column` and in the **Operation** select the `UpperCase` and click **OK**

    ![character-map](/images/character_map/character-map-4.png) 
    
16. Verify the Transformaion and click **OK**
    ![character-map](/images/character_map/character-map-5.png) 
17. Drag and Drop the **Flat File Destination** onto the design surface.
    ![Flat File Destination](/images/character_map/image-1.png) 
18. Connect the **Character Map** and **Flat File Destination**.
    ![Flat File Destination](/images/character_map/image-2.png) 
19. Double click the **Flat File Destination** to open the **Editor**
20. On the **Flat File Destination Editor** click **New** which open the **Flat File Format** and select **Delimited** and click **OK**.
    ![Flat File Destination](/images/character_map/image-3.png) 
21. On the **Flat File Connection Editor** click **Browse** to select the **CSV File**.
    ![Flat File Destination](/images/character_map/image-4.png) 
22. On the **Flat File Connection Editor** verify the **CSV File** and select **Column names in the first data row**.
    ![Flat File Destination](/images/character_map/image-5.png) 
23. Click on the **Columns** tab click **OK**
    ![Flat File Destination](/images/character_map/image-6.png) 
24. On the **Flat File Destination Editor** select **Overwrite data in the file** and click **OK**
    ![Flat File Destination](/images/character_map/image-7.png) 
25. Click on the **Mappings** tab verify the columns mappings and click **OK**
    ![Flat File Destination](/images/character_map/image-8.png) 
26. This should be the final outcome and save the package.
    ![Flat File Destination](/images/character_map/image-9.png) 
27. Right click on the package in Solution Explorer and select **Execute the package**.
    ![Execute Package](/images/character_map/execute_package.png) 
