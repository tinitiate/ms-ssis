# Foreach Item Enumerator

- The "Foreach Loop Container" with the "Item Enumerator" allows you to loop through a predefined set of items manually specified within the container. 

## Example 

* Right Click on the design Surface and select Variables.

  

   ![](/images/item_enumeration/image-1.png)

  

* On the Variables window create new variables.

  

  ![](/images/item_enumeration/image-2.png)

  

* Create Variables FolderPath (Enter the path of the CSV Files folder) which is a string and File which is an string .

  

  ![](/images/item_enumeration/image-4.png)

  

* Drag and drop a Foreach Loop Container from the SSIS Toolbox onto the Control Flow design surface.

  

  ![](/images/item_enumeration/image-5.png)

  

* Right-click  and click **Edit** the Foreach Loop Container to open its editor.

  

  ![](/images/item_enumeration/image-6.png)

  

* In the editor, go to the "Collection" tab and Select the "Foreach Item Enumerator" as the enumerator and click **Columns**.

  

  ![](/images/item_enumeration/image-7.png)

  

* On the **For Each Item Columns** click **Add** to add New Column and click **OK**.

  

​		![](/images/item_enumeration/image-8.png)

​		![](/images/item_enumeration/image-9.png)



* On the **Foreach Loop Editor** under the **Column 0** enter the file names which needs to be processed.

  

​       ![](/images/item_enumeration/image-10.png)

​       ![](/images/item_enumeration/image-11.png)



* In the editor, go to the "Variable Mappings" tab and Select  `User::FileName` as the variable and click **OK**.

  

  ![](/images/item_enumeration/image-12.png)

  

* In the Foreach Loop container, Drag and drop the Data Flow task.

  

​       ![](/images/item_enumeration/image-13.png)



* On the Data Flow Task drag and drop the Flat File Source.

  

  ![](/images/item_enumeration/image-14.png)



* Right Click on the **Flat File Source** and select **Edit** which will open **Flat File Source Editor**.

  

  ![](/images/item_enumeration/image-15.png)



*  On the **Flat File Source Editor** click on the **New** Button which will open **Flat File Connection Manager Editor**.

  

  ![](/images/item_enumeration/image-16.png)



* Enter the Connection manager name you want, click on **Browse** Button to select the file.

  

  ![](/images/item_enumeration/image-17.png)



* On the **File Explorer** go to the path where the Files are located and change the file type to **CSV**.

  

  ![](/images/item_enumeration/image-18.png)

  

  ![](/images/item_enumeration/image-19.png)



* On **Flat File Connection Manager Editor**  select **Column** tab and Click **OK** which will take you back to the **Flat File Source Editor**.

  

    ![](/images/item_enumeration/image-20.png)



* Drag and drop an **OLE DB Destination** task onto the design surface and connect the Flat File Source and OLE DB Destination.

  

    ![](/images/item_enumeration/image-21.png)

  

    ![](/images/item_enumeration/image-22.png)

  

* Right Click on the **OLE DB Destination** and select **Edit** which will open **OLE DB Destination Editor**.

  

  ​    ![](/images/item_enumeration/image-23.png)

  

* On the Connection Manager Tab select the Connection and Table.

  

  ​    ![](/images/item_enumeration/image-24.png)



* On the Mappings Tab click **OK**.

  

     ![](/images/item_enumeration/image-25.png)



* Right-click on the Flat File Connection and select **Properties**.

  

  ​    ![](/images/item_enumeration/image-26.png)

  

* On the Properties on Expressions click **Three dots** to open Expression Builder.

  

  ​    ![](/images/item_enumeration/image-27.png)

  

* On the **Property Expressions Editor** on the **Property** drop down select **ConnectionString**.

  

  ![](/images/incremental_file_load/image-38.png)

  

* On the **Expressions** click the **Three dots**.

  

​       ![](/images/incremental_file_load/image-39.png)



* On the Expression Builder enter the Expression` @[User::FolderPath] + @[User::FileName]` and click **Evaluate Expression**.

  

  ![](/images/item_enumeration/image-28.png)

  

* Verify the Expression and click **OK**.

  

  ![](/images/item_enumeration/image-29.png)

  

* On the Property Expressions Editor click **OK**.

  

  ![](/images/item_enumeration/image-30.png)

