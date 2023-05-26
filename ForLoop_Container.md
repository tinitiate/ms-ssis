 ![tinitiate.com ssis](/images/tiniaitessis.png)

# For Loop Container

* The Loop Container in SSIS provides looping functionality, allowing you to repeat a set of tasks or operations based on a defined condition. 
* It is useful when you need to perform iterative tasks or process multiple items in a repetitive manner.
* The Loop Container is commonly used when you need to process files, perform calculations on multiple data sets, or execute a set of tasks repetitively.

## Key features of the Loop Container

- Purpose: The For Loop Container is used in SSIS to repeat a set of tasks based on a specified condition or iteration count. It provides looping functionality within the control flow of an SSIS package.

- Control Flow Structure: The For Loop Container acts as a control flow structure similar to the Sequence Container. However, instead of executing tasks sequentially, it repeats the contained tasks until a specific     condition is met or a specified number of iterations are completed.

- Looping Options: The For Loop Container provides different looping options:

- Predefined Count: You can specify a fixed number of iterations to repeat the contained tasks.
- Expression-Based Condition: You can define an expression that evaluates a Boolean condition. The tasks within the container will be repeated until the condition evaluates to False.
- Enumerator: You can use an enumerator, such as the Foreach Loop Enumerator, to iterate over a collection, such as files in a directory or rows in a result set.
- Variable Usage: The For Loop Container often utilizes variables to control the looping behavior. Variables can be used to track the current iteration count, store the result of an expression-based condition, or hold values from the enumerator.

- Task Execution and Precedence Constraints: The tasks within the For Loop Container are executed in a sequential order defined by precedence constraints. These constraints determine the execution flow between the tasks and provide flexibility in designing the workflow within the loop.

- Incrementing/Decrementing Variables: In cases where a fixed number of iterations is specified, the For Loop Container typically uses variables to increment or decrement a counter value to track the progress of the loop.

- Nested Containers: The For Loop Container can be nested within other containers or even within itself, enabling complex looping scenarios and nested iterations.


## Execute SQL Task

* The Execute SQL Task in SSIS allows you to execute SQL statements or stored procedures against a database.
*  It provides a flexible and versatile way to interact with databases and perform data manipulation or retrieval operations.

### Key features of the Execute SQL Task

- Connection Manager: You can specify an existing connection manager or create a new one to establish a connection to the database.
- SQL Statement/SP: You define the SQL statement or stored procedure that you want to execute. It can include parameterization and variable usage for dynamic SQL.
- Result Sets: The Execute SQL Task supports retrieving result sets from the executed SQL statement. You can map the result set to variables or destination components for further processing.
- Error Handling: It provides options to handle errors during SQL execution, such as capturing errors, redirecting error rows, or specifying actions for different error scenarios.
- The Execute SQL Task is commonly used for tasks such as executing data manipulation statements (e.g., INSERT, UPDATE, DELETE), retrieving data, creating or modifying database objects, and calling stored procedures.

## Steps to Loop through the Table and Export the Data to CSV Files using **For Loop**

1. Open SSIS Designer.

2. On the **Control Flow** right click and Select **Variables** which will open the `Variables` window.

    ![Sql Task](/images/forloop/forloop_2.png)

   1. On the **Variables** window click the button shown in the image to create the new variable.

       ![Sql Task](/images/forloop/forloop_3.png)

   2. Under the "Name" enter `FolderPath` on the "Data Type" drop down select `String`

       ![Sql Task](/images/forloop/forloop_4.png)

   3. On the Value enter `C:\Users\sriat\OneDrive\Desktop\ssis\csv_destination_files`, change the path depending on your folder location.

      ![Sql Task](/images/forloop/forloop_5.png)

   4. Create the following Variables:

      1. `Filepath` as string and leave the value "Empty"

      2. `LoopCounter` as Int32 and enter "1" for the value.

      3. `MaxTerritoryId` as Int32 and enter "0" for the value.

         ![Sql Task](/images/forloop/forloop_6.png)

3. In the SSIS Toolbox, drag and drop a **Execute SQL Task** onto the design surface and Rename it to "Get Max Territory Id".

    ![Sql Task](/images/forloop/forloop_7.png)

4. Right Click on the SQL Task and Click **Edit**

    ![Sql Task 2](/images/forloop/forloop_8.png)

4. On the **Execute SQL Task Editor** go to **Connection** and Select "New Connection".

    ![Sql Task](/images/forloop/forloop_9.png)

5. On the **Configure OLE DB Connection Manager** Select the desired Data Connection or Click **New** to create a new connection and click **OK**

    ![Sql Task](/images/forloop/forloop_10.png)

6. On the **Execute SQL Task Editor** go to **SQLStatement** and Click the **Three Dots**.

    ![Sql Task](/images/forloop/forloop_11.png)

7. On the **Enter SQL Query** window, enter the command `Select MAX(TerritoryID) from Customer_territory ct ` and Click **OK**.

   ![Sql Task](/images/forloop/forloop_12.png)

8. On the **Execute SQL Task Editor** go to **ResultSet** and Click the **Drop Down** and Select **Single Row**.

   ![Sql Task](/images/forloop/forloop_13.png)

9. On the **Result Set** Tab of the **Execute SQL Task Editor** Click **ADD**.

   ![Sql Task](/images/forloop/forloop_14.png)

   1. Select the Variable Name from the **Drop Down** and Select **User::Filepath** and Click **OK**.

      ![Sql Task](/images/forloop/forloop_15.png)

10.In the SSIS Toolbox, drag and drop a **For Loop Container** onto the design surface.

​		![Sql Task](/images/forloop/forloop_16.png)

11. Connect the **Execute SQL Task**  and **For Loop Container**.

    ![Sql Task](/images/forloop/forloop_17.png)

12. Right Click on the "For Loop Container" and Click **Edit**.

    ![Sql Task](/images/forloop/forloop_18.png)

13. On the **For Loop Editor** Enter the Values for:

    1.  `InitExpression`  "@LoopCounter=1"
    2.  `EvalExpression`  "@LoopCounter <= @MaxTerritoryId"
    3. `AssignExpression` "@LoopCounter = @LoopCounter+1"
    4. Click **OK**.

    ![Sql Task](/images/forloop/forloop_19.png)

14. Drag and Drop the **Data Flow Task** inside the **For Loop Container**.

    ![Sql Task](/images/forloop/forloop_20.png)

15. Double Click the **Data Flow Task** which will open the **Data Flow Tab**

16. On the **Data Flow Tab** drag and drop the **OLE DB Source**.

    ![Sql Task](/images/forloop/forloop_21.png)

17. Double Click the **OLE DB Source** which will open the **OLE DB Source Editor**.

18. On the **OLE DB Source Editor** Select the desired Data Connection in the **OLE DB connection Manager** drop down and Select the **SQL command** in the **Data access mode** drop down.

    ![Sql Task](/images/forloop/forloop_22.png)

19. On the **SQL command text** enter the command `SELECT  * from Customer_territory ct 
where TerritoryID = ?` and Click on **Parameters**

    ![Sql Task](/images/forloop/forloop_23.png)

20. On the **Set Query Parameters** Under the Variables drop down Select the **User::LoopCounter** and Click **OK**

    ![Sql Task](/images/forloop/forloop_24.png)

21. On the **OLE DB Source Editor** Click **OK**.

    ![Sql Task](/images/forloop/forloop_25.png)

22. Drag and Drop the **Flat File Destination**.

    ![Sql Task](/images/forloop/forloop_26.png)

23. Connect the **OLE DB Source** and **Flat File Destination**.

    ![Sql Task](/images/forloop/forloop_27.png)

24. Right Click on the **Flat File Destination** and click **Edit**

    ![Sql Task](/images/forloop/forloop_28.png)

25. On the **Flat File Destination Editor** Click **New**.

    ![Sql Task](/images/forloop/forloop_29.png)

26. Select the **Delimited** On the **Flat File Format** and Click **OK**.

    ![Sql Task](/images/forloop/forloop_30.png)

27. On the **Flat File Connection Manager Editor** Enter the name you want to give the "Connection" and Click **Browse** to select the File for destination.

    ![Sql Task](/images/forloop/forloop_31.png)

28. After selecting the file, change the **Text Qualifier** to `"` and Select the "Check Box" Next to **Column names in the first row** and Click **OK**.

    ![Sql Task](/images/forloop/forloop_32.png)

29. Select the **Preview** tab and Click **OK**

    ![Sql Task](/images/forloop/forloop_33.png)

30. On the **Flat File Destination Editor** Click **Mappings**, On the **Mappings** tab Click **OK**

    ![Sql Task](/images/forloop/forloop_34.png)

31. Right Click on the **Flat File Connection** under the `Connection Managers` and click **Properties**.

    ![Sql Task](/images/forloop/forloop_35.png)

32. On the **Properties** window go **Expressions** and Click on the "three dots" to open the `Property Expressions Editor`

    ![Sql Task](/images/forloop/forloop_36.png)

33. On the **Property Expressions Editor** on the "Property" drop down Select **ConnectionString**.

    ![Sql Task](/images/forloop/forloop_37.png)

    1. Click on the three dots under expression to open `Expression Builder`

       ![Sql Task](/images/forloop/forloop_38.png)

    2. On the **Expression Builder** enter the expression `""+ @[User::FolderPath]+"\\Customer"+(DT_WSTR,12) @[User::LoopCounter]+".csv"` and click on **Evaluate Expression**.

       ![Sql Task](/images/forloop/forloop_39.png)

    3. Verify that the Expression is Correct and click **OK**.

       ![Sql Task](/images/forloop/forloop_40.png)

