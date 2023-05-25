 ![tinitiate.com ssis](/images/tiniaitessis.png)

# Foreach Loop container

* The Foreach Loop container is a control flow container that allows you to execute a set of tasks repeatedly, once for each item in a collection.

## Foreach File enumerator

* The Foreach File enumerator is an enumerator that allows you to iterate over the files in a folder.

## Example

1. Open SSIS Designer.

2. In the SSIS Toolbox, drag and drop a **Foreach Loop container** onto the design surface.

   ![](/images/foreachloop/foreachloop_1.png)

3. Right Click on the design Surface and select Variables

   ![](/images/foreachloop/foreachloop_2.png)

4. On the Variables window create new vairables.

   ![](/images/foreachloop/foreachloop_3.png)

5. Create Variables FilePath (Enter the path of the CSV Files selecting the First csv files) which is a string and Records_Count which is an integer.

   ![](/images/foreachloop/foreachloop_4.png)

   ![](/images/foreachloop/foreachloop_5.png)

   ![](/images/foreachloop/foreachloop_6.png)

6. In the Foreach Loop container, Drag and drop the Data Flow task and rename the task to **load data.**

   ![](/images/foreachloop/foreachloop_7.png)

7. Right Click on the **load data** and select **Edit** which will open **Data Flow Tab**.

   ![](/images/foreachloop/foreachloop_8.png)

8. In the  **Data Flow Tab** Drag and drop Flat File Source.

   ![](/images/flat_file.png)

9. Right Click on the **Flat File Source** and select **Edit** which will open **Flat File Source Editor**.

   ![](/images/flat_file_2.png)

10. On the **Flat File Source Editor** click on the **New** Button which will open **Flat File Connection Manager Editor**.

    ![](/images/flat_file_2.png)

11. Enter the Connection manager name you want or you can leave it as it is, same for Description and Finally click on **Browse** Button to select the file.

    ![](/images/flat_file_4.png)

12. On the **File Explorer** go to the path where the Files are located and change the file type to **CSV**.

    ![](/images/flat_file_5.png)

13. Select the File which we want to use and click on **Open** Button. This will take you back to the **Flat File Connection Manager Editor**.

    ![](/images/flat_file_6.png)

14. On **Flat File Connection Manager Editor**  select **Column** tab and Click **OK** which will take you back to the **Flat File Source Editor**.

    ![](/images/flat_file_7.png)

15. On the **Flat File Source Editor** click on the **OK** Button.

    ![](/images/flat_file_8.png)

16. Drag and drop an **Row Count** task onto the design surface.

    ![](/images/foreachloop/row_count.png)

17. Right Click on the **Row Count** and select **Edit** which will open **Row Count**.

    ![](/images/foreachloop/row_count_1.png)

    ![](/images/foreachloop/row_count_2.png)

    ![](/images/foreachloop/row_count_3.png)

18. Drag and drop an **OLE DB Destination** task onto the design surface.

    ![](/images/foreachloop/OLEDB-Destination.png)

19. Right Click on the **OLE DB Destination** and select **Edit** which will open **OLE DB Destination Editor**.

​	   ![](/images/foreachloop/OLEDB-Destination-Editor.png)

​	   ![](/images/foreachloop/OLEDB-Destination-Editor_2.png)

20. Drag and drop an **Execute SQL Task** onto the design surface and rename the task as **Logs** and Connect the **Load Data** and **Logs** Task.

    ![](/images/foreachloop/foreachloop_10.png)

21. Right Click on the  **Execute SQL Task** and select **Edit** which will open **Execute SQL Task Editor**.

    ![](/images/foreachloop/foreachloop_11.png)

22. Select the Existing connection, if no connections are available create a new connection.

    ![](/images/foreachloop/foreachloop_12.png)

23. Go to the Expressions tab on the **Execute SQL Task Editor** and click on the three dots and follow the instructions in the images below. 

    ![](/images/foreachloop/foreachloop_13.png)

    ![](/images/foreachloop/foreachloop_14.png)

    ![](/images/foreachloop/foreachloop_15.png)

    ![](/images/foreachloop/foreachloop_16.png)

    ![](/images/foreachloop/foreachloop_17.png)

    ![](/images/foreachloop/foreachloop_18.png)

24. Right Click on the  **Foreach Loop container**  and select **Edit** which will open **Foreach Loop Editor**.

    ![](/images/foreachloop/foreachloop_19.png)

25. On the **Foreach Loop Editor** click on the **Collection** tab and Select the **Folder** of the Source Files by clicking on **Browse**

    ![](/images/foreachloop/foreachloop_20.png)

    ![](/images/foreachloop/foreachloop_21.png)

26. On the **Foreach Loop Editor** click on the **Variable Mappings** tab and Select the **Variable**  `User:FilePath` and click **OK**

27. Right click on the **Connection Manager** and select **Properties**

    ![](/images/foreachloop/Connection_manager_properties.png)

28. On the **Properties** Under the **Expressions** select the three dots, it will open the **Property Expressions Editor**

    ![](/images/foreachloop/Connection_manager_properties_1.png)

29. On the **Property Expressions Editor** select the Property **Connection String** and select the select the three dots, it will open the **Expression Builder**

    ![](/images/foreachloop/Connection_manager_properties_2.png)

30. On the **Expression Builder** expand the variables and Parameters and select the `User:FilePath` and click Evaluate Expression.

    ![](/images/foreachloop/Connection_manager_properties_3.png)

    ![](/images/foreachloop/Connection_manager_properties_4.png)

31. We should see the **Evaluated Value** as the File we selected, once we verify the path click **OK** on both **Expression Builder** and  **Property Expressions Editor** .

    ![](/images/foreachloop/Connection_manager_properties_5.png)

    ![](/images/foreachloop/Connection_manager_properties_6.png)
