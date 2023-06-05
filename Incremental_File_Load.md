 ![tinitiate.com ssis](/images/tiniaitessis.png)

# Foreach Loop container

* The Foreach Loop container is a control flow container that allows you to iterate over a collection of items and perform tasks for each item in the collection. 
* It provides a looping mechanism based on enumerators.

## Key features of the Foreach Loop Container
- **Purpose**: The Foreach Loop Container is used when you need to perform a set of tasks repeatedly for each item in a collection, such as files in a directory or rows in a result set.

- **Collection and Enumerator**: The Foreach Loop Container requires a collection to iterate over. It supports various types of enumerators, including:

    - **Foreach File Enumerator**: Iterates over files in a specified directory.
    - **Foreach ADO Enumerator**: Iterates over rows in a result set from a database query.
    - **Foreach Item Enumerator**: Iterates over a manually defined list of items.
    - **Foreach NodeList Enumerator**: Iterates over XML nodes.
    - **Foreach From Variable Enumerator**: Iterates over a collection stored in a variable.
- **Variable Mapping**: The Foreach Loop Container uses variables to store the values from each iteration. You can map variables to capture the current item being processed, the index of the current iteration, and any other necessary data.

- **Task Execution**: Within the Foreach Loop Container, you can define a set of tasks that will be executed for each item in the collection. These tasks can perform operations such as data transformations, file processing, or database operations.

- **Expressions and Evaluators**: The Foreach Loop Container allows you to use expressions to dynamically configure properties and expressions for the tasks within the container. You can use variables and expressions to control the behavior of the loop and the tasks being executed.

- **Event Handling**: The Foreach Loop Container provides event handlers that allow you to capture and handle specific events that occur during the loop execution, such as when an item starts or completes processing.

- **Nested Containers**: The Foreach Loop Container supports nesting, meaning you can place other containers or tasks within it to create more complex looping scenarios.

## Execute Sql Task 
- The "Execute SQL Task" is a control flow task that allows you to execute SQL statements or queries against a database.
- It is a versatile task that can be used for a variety of purposes, such as data manipulation, data extraction, or administrative tasks.

- **Connection**: The task requires a database connection manager to specify the database server and authentication details. You can either select an existing connection manager or create a new one.

- **SQLStatement**: This property is where you provide the SQL statement or query that you want to execute. It can be a simple SQL statement or a complex query involving multiple tables, joins, conditions, etc.

- **Result Set**: If your SQL statement returns a result set, you can configure the task to store the result in SSIS variables. This allows you to use the result set in subsequent tasks or components within your SSIS package.

- **Parameter Mapping**: If your SQL statement includes parameters, you can map SSIS variables or package parameters to those parameters. This enables you to dynamically pass values to the SQL statement during execution.

- **ResultSetType**: This property determines the type of result set returned by the SQL statement. It can be set to "None" if the SQL statement does not return a result set, "SingleRow" if it returns a single row, or "FullResultSet" if it returns multiple rows.

- **ConnectionType**: The task supports different connection types depending on the database provider you are using. For SQL Server, the options include OLE DB, ADO.NET, or SQL Server Native Client.

- **Error** **Handling**: You can specify how the task should handle errors during execution. For example, you can choose to fail the task if an error occurs or continue execution while logging the error.

- **Logging**: SSIS provides logging capabilities to capture execution details and errors. You can configure the task to log information such as start time, end time, SQL statement, result set, and any error messages generated during execution.

## Example

1. Open SSIS Designer.

2. Right Click on the design Surface and select Variables

   

   ![](/images/incremental_file_load/image-1.png)

   

3. On the Variables window create new variables.

   

   ![](/images/incremental_file_load/image-2.png)

   

4. Create Variables FilePath (Enter the path of the CSV Files selecting the First csv files) which is a string and InsertedRecords and IsFileAlreadyLoaded which are integer.

   

   ![](/images/incremental_file_load/image-3.png)

   ![](/images/incremental_file_load/image-4.png)

   

5. In the SSIS Toolbox, drag and drop a **Execute SQL Task** onto the design surface.

   

   ![](/images/incremental_file_load/image-5.png)

   

6. Right Click on the **load data** and select **Edit** which will open **Execute SQL Task**.

   

​		![](/images/incremental_file_load/image-6.png)



8. On the General Tab Select the **Connection**.

   

​		![](/images/incremental_file_load/image-7.png)

​    

9. On the **SQLStatement** click the three dots.

   

   ![](/images/incremental_file_load/image-8.png)

   

10. On the **Enter SQL Query** add the Sql Query and click **OK**

    

    ![](/images/incremental_file_load/image-9.png)

    

11. On the **Execute SQL Task Editor**.

    

​      ![](/images/incremental_file_load/image-10.png)



12. In the SSIS Toolbox, drag and drop a **Foreach Loop container** onto the design surface.

    

    ![](/images/incremental_file_load/image-11.png)

    

13. Connect the SQL Task and Foreach Loop Container.

    

    ![](/images/incremental_file_load/image-12.png)

    

14. Right click  on the Foreach Loop Container and click **Edit**.

    

    ![](/images/incremental_file_load/image-13.png)

    

15. On the Foreach Loop Editor on the **Collection** tab and Select the **Foreach File Enumerator**.

    

    ![](/images/incremental_file_load/image-14.png)

    

16. Click Browse to the select the Folder where the files are located.

    

​	 ![](/images/incremental_file_load/image-15.png)



17. Enter the Type of Files `*.csv` 



​    ![](/images/incremental_file_load/image-16.png)



18. On the Variable Mappings Tab select the `User::FilePath` and click **OK**

    

​    ![](/images/incremental_file_load/image-17.png)



​    ![](/images/incremental_file_load/image-18.png)



19. In the Foreach Loop container, Drag and drop the Data Flow task.

​    

​    ![](/images/incremental_file_load/image-19.png)

​     

20. Double Click the Data Flow task which will open **Data Flow Tab**. In the  **Data Flow Tab** Drag and drop Flat File Source.



​    ![](/images/incremental_file_load/image-20.png)



21. Right Click on the **Flat File Source** and select **Edit** which will open **Flat File Source Editor** and Click **New**.

   

​    ![](/images/incremental_file_load/image-21.png)



22. On the **Flat File Connection Manager Editor** click **Browse** to select the file which needs to be processed.

    

   ![](/images/incremental_file_load/image-22.png)



   ![](/images/incremental_file_load/image-23.png)



23. On the Columns Tab click **OK**.

    

    ![](/images/incremental_file_load/image-24.png)

    

24. On the **Flat File Source** click **OK**.

    

    ![](/images/incremental_file_load/image-25.png)

    

25. Drag and drop an **Row Count** task onto the design surface and connect the **Flat File Source** and **Row Count**.

    

    ![](/images/incremental_file_load/image-26.png)

    

    ![](/images/incremental_file_load/image-27.png)

    

26. Right Click on the **Row Count** and select **Edit** which will open **Row Count** and select `User::InsertedRecords` and click **OK**

    

    ![](/images/incremental_file_load/image-28.png)

    

    ![](/images/incremental_file_load/image-29.png)

    

    ![](/images/incremental_file_load/image-30.png)

    

27. Drag and drop an **OLE DB Destination** task onto the design surface and connect the **Row Count** and **OLE DB Destination**.

    

    ![](/images/incremental_file_load/image-31.png)

    

    ![](/images/incremental_file_load/image-32.png)

    

28. Right Click on the **OLE DB Destination** and select **Edit** which will open **OLE DB Destination Editor**.

29. On the **OLE DB Destination Editor** select the connection and the destination table.

    

    ![](/images/incremental_file_load/image-33.png)

    

30. On the **OLE DB Destination Editor** select the Mappings tab and click **OK**.

    

    ![](/images/incremental_file_load/image-34.png)

    

31. Right click on the Customer Connection Manger and select **Properties**.

    

​      ![](/images/incremental_file_load/image-36.png)



32. On the **Properties** on the Expressions click the **Three dots**.

    

    ![](/images/incremental_file_load/image-37.png)

    

33. On the **Property Expressions Editor** on the **Property** drop down select **ConnectionString**.

    

    ![](/images/incremental_file_load/image-38.png)

    

34. On the **Expressions** click the **Three dots**.

    

    ![](/images/incremental_file_load/image-39.png)

    

35. On the **Expression Builder** drag and drop the `User::FilePath` and click the Evaluate Expression and click **OK**.

    

    ![](/images/incremental_file_load/image-40.png)

    

    ![](/images/incremental_file_load/image-41.png)

    

36. On the **Property Expressions Editor** click **OK**.

    

    ![](/images/incremental_file_load/image-42.png)

    

37. Drag and drop the **Execute SQL Task** on to the **Foreach Loop Container** and connect the **Data Flow Task** and **Execute SQL Task**.

    

    ![](/images/incremental_file_load/image-43.png)

    

    ![](/images/incremental_file_load/image-44.png)

    

38. On the **Execute SQL Task Editor** under the Connection select the **Connection**.

    

    ![](/images/incremental_file_load/image-45.png)

    

39. On the **Expressions** tab click the **Three dots**.

    

    ![](/images/incremental_file_load/image-46.png)

    

40. On the **Property Expressions Editor** Under Property select **SqlStatementSource** and click the **Three dots** on the Expression.

    

    ![](/images/incremental_file_load/image-47.png)

    

41. On the Expression Builder Enter the Expression `"Insert into File_Logs Select 'File loaded', '" + @[User::FilePath] + "', (DT_WSTR,12)@[User::Records_Count], GETUTCDATE()" `and click **Evaluate Expression**.

    

    ![](/images/incremental_file_load/image-48.png)

    

42. On the Expression Builder verify the Expression and click **OK**.

    

    ![](/images/incremental_file_load/image-49.png)

    

43. On the **Property Expressions Editor** click **OK**.

    

    ![](/images/incremental_file_load/image-50.png)

    

    ![](/images/incremental_file_load/image-51.png)

    

44. On the **Execute SQL Task Editor** click **OK**.

45. Drag and drop the **Execute SQL Task** on to the **Foreach Loop Container**.

46. On the **Execute SQL Task Editor** under the Connection select the **Connection**.

    

    ![](/images/incremental_file_load/image-45.png)

    

47. On the **Expressions** tab click the **Three dots**.

    

    ![](/images/incremental_file_load/image-46.png)

    

48. On the **Property Expressions Editor** Under Property select **SqlStatementSource** and click the **Three dots** on the Expression.

    

    ![](/images/incremental_file_load/image-47.png)

    

49. On the Expression Builder Enter the Expression `"Select Count(*) From File_Logs where File_Name ='" + @[User::FilePath] + "'"` and click **Evaluate Expression**.

    

    ![](/images/incremental_file_load/image-54.png)

    

50. On the Expression Builder verify the Expression and click **OK** and click **OK** on the Property Expression Editor.

    

    ![](/images/incremental_file_load/image-55.png)

    

    ![](/images/incremental_file_load/image-56.png)

    

51. On the **Execute SQL Task Editor** from the drop down of **ResultSet** select the **Single row**.

    

    ![](/images/incremental_file_load/image-57.png)

    

52. On the **Result Set** tab click **Add**.

    

    ![](/images/incremental_file_load/image-58.png)

    

53. On the Variable Name drop down select the `IsFileAlreadyLoaded` and click **OK**.

    

    ![](/images/incremental_file_load/image-59.png)

    

54. Connect the **Execute SQL Task** and **Data Flow Task**.

    

    ![](/images/incremental_file_load/image-60.png)

    

55. Right click on the connection and **Edit**.

    

    ![](/images/incremental_file_load/image-61.png)

    

56. On the Precedence Constraint Editor select the **Expression and Constraint**.

    

    ![](/images/incremental_file_load/image-62.png)

    

57. On the Expression click the **Three dots** to open the Expression Builder.

    

    ![](/images/incremental_file_load/image-63.png)

    

58. On the Expression Builder Enter the expression `@[User::IsFileAlreadyLoaded]==0` and click **Evaluate Expression**.

    

    ![](/images/incremental_file_load/image-64.png)

    

59. Verify the expression and click **OK**.

    

    ![](/images/incremental_file_load/image-65.png)

    

60. Click **OK** on the Precedence Constraint Editor.

    

    ![](/images/incremental_file_load/image-66.png)

    

61. Right click on the Control flow and click **Properties**.

    

    ![](/images/incremental_file_load/image-68.png)

    

62. On the Properties select **True** for the DelayValidation.

    

    ![](/images/incremental_file_load/image-69.png)

    

    

