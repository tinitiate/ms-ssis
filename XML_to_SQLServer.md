# 	SSIS XML file import to SQL Server

1. **Create a new SSIS project.**

   * To create a new SSIS project, you can use SQL Server Data Tools (SSDT). In SSDT, click on `File` > `New` > `Project`. 

   * In the `New Project` dialog, select the `Integration Services` project template. Click on `Next`. 

     ![](images/create_integration_project.png "Create New Project")

   * In the `Configure your new project` dialog, enter the following information:

     ```markdown
     * Project name: `Load XML to SQL`
     * Location: `C:\Users\<username>\Desktop`
     * Solution name: `Load XML to SQL`
     
     ```

   * Click on `Create`.

     ![](/images/xml/project_creation.png)

2. **Add a new data flow task.**

   *  To add a new data flow task, , drag and drop the `Data Flow Task` from the `Toolbox` to the `Package` design surface.

     ![](/images/xml/data_flow_task.png)

3. **Add an XML source.**

   *  To add an XML source, drag and drop the `XML Source` task from the `Toolbox` to the `Data Flow` design surface.

     ![](/images/xml/xml_source.png)

4. **Configure the XML source.**

   * In the `XML Source` editor, specify the following information:

     ```markdown
     * **XML file name:** The path and name of the XML file that you want to load.
     * **XML Schema:** The XML schema that defines the structure of the XML file.
     * **Root node name:** The name of the root node in the XML file.
     
     ```

​		      							![](/images/xml/xml_source_configuration.png)

​									      ![](/images/xml/xml_source_configuration_final.png)

5. **Add an OLE DB destination.**

   * To add an OLE DB destination, drag and drop the `OLE DB Destination` task from the `Toolbox` to the `Data Flow` design surface.

     ![](/images/xml/oledb_destination.png)

6. **Configure the OLE DB destination.**

   * In the `OLE DB Destination` editor, specify the following information:

     ```markdown
     * **Connection manager:** The name of the connection manager that you want to use to connect to SQL Server.
     * **Table name:** The name of the table in SQL Server that you want to load the data into.
     * **Column mapping:** Map the columns in the XML file to the columns in the SQL table.
     ```

     
