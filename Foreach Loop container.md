 ![tinitiate.com ssis](/images/tiniaitessis.png)

# Foreach Loop container

* The Foreach Loop container is a control flow container that allows you to execute a set of tasks repeatedly, once for each item in a collection.

## Foreach File enumerator

* The Foreach File enumerator is an enumerator that allows you to iterate over the files in a folder.

## Example

1. Open SSIS Designer.

2. In the SSIS Toolbox, drag and drop a Foreach Loop container onto the design surface.

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

16. In the Foreach Loop container, click the Enumerator tab.

17. Select the Foreach File Enumerator option.

18. In the Directory field, type the path to the folder that contains the files that you want to process.

19. In the FileSpec field, type a wildcard that specifies the files that you want to process.

20. Click OK.

21. 

22. Drag and drop a Flat File Source task onto the design surface.

23. In the Flat File Source task, click the Connection Manager tab.

24. Select the connection manager that you created for the flat file that you want to process.

25. Click OK.

26. Drag and drop a Row Count Task onto the design surface.

27. In the Row Count Task, click the Connection Manager tab.

28. Select the same connection manager that you selected for the Flat File Source task.

29. Click OK.

30. Drag and drop an Oledb Destination task onto the design surface.

31. In the Oledb Destination task, click the Connection Manager tab.

32. Select the connection manager that you created for the SQL Server database that you want to insert the row count into.

33. In the OLEDB Destination Properties dialog box, click the Mappings tab.

34. In the Column Mappings list, select the OLE DB column that you want to map to the Records_Count variable.

35. Click OK.

36. Drag and drop a Logs task onto the design surface.

37. In the Logs task, click the Connection Manager tab.

38. Select the same connection manager that you selected for the Flat File Source task.

39. In the Logs task, click the Script tab.

40. In the Script type drop-down list, select Execute SQL.

41. In the Script text box, type the following expression:

```
insert into FileInfo values ('@[User::FilePath]', @[User::Records_Count], GETDATE())
```

1. In the Variables section, click the Add button.
2. In the Variable Name field, type Records_Count.
3. In the Variable Value field, type @[User::Records_Count].
4. Click OK.
5. Click OK.
6. Save the SSIS package.
7. In Object Explorer, right-click the SSIS package and select Deploy.
8. In the Deploy SSIS Package dialog box, click Next.
9. In the Target Server drop-down list, select the SQL Server instance that you want to deploy the package to.
10. In the Package path field, type the path to the SSIS package.
11. Click Next.
12. In the Deployment Action drop-down list, select Deploy.
13. Click Next.
14. In the Deployment Options section, select the options that you want to use.
15. Click Next.
16. In the Review Deployment Results section, review the deployment results.
17. Click Finish.

The SSIS package will now be deployed to the SQL Server instance. You can then run the package to process the files and insert the row count into the SQL Server database.