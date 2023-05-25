![tinitiate.com ssis](/images/tiniaitessis.png)

# Audit Transform with Flat File Source and Destination

## Flat File Source Task

* The Flat File Source task is an SSIS component used to read data from a flat file, such as a CSV (Comma-Separated Values) file.
*  It allows us to specify the file path, format, delimiters, and column mappings to extract data from the file. 
* The Flat File Source task reads the data row by row and makes it available for further transformations and processing within the SSIS package.

### Key features of the Flat File Source Task

- File Format: You can choose the appropriate format for your flat file, such as delimited (CSV) or fixed-width.
- Connection Manager: The Flat File Source task uses a connection manager to establish a link to the source file and define its properties, such as file path and format.
- Column Mappings: It enables you to map the columns in the source file to the corresponding columns in the data flow, ensuring that the data is correctly aligned during extraction.

## Audit Task

* The Audit task is a common practice in data integration workflows to track and record information about the data transformation process. 
* It helps monitor and analyze the data flow, capture metadata, and ensure data quality and compliance. 
* Typically, an Audit task involves capturing details such as source file information, transformation timestamps, error counts, and other relevant data for auditing purposes.

## Flat File Destination Task

* The Flat File Destination task is an SSIS component used to write data to a flat file, such as a TXT file. 
*  It allows us to specify the file path, format, delimiters, and column mappings to store data in the file. 
* The Flat File Destination task receives data from upstream transformations or sources and writes it row by row to the specified file.

### Key features of the Flat File Destination Task

- File Format: We can choose the appropriate format for your flat file, such as delimited (TXT) or fixed-width.
- Connection Manager: The Flat File Destination task uses a connection manager to establish a link to the destination file and define its properties, such as file path and format.
- Column Mappings: It enables us to map the columns from the data flow to the corresponding columns in the destination file, ensuring that the data is correctly written and aligned.

## Steps to create the Audit Transform with Flat File Source and Destination

1. Create a new SSIS package or open an existing one.

2. Add a **Data Flow Task** to the Control Flow tab.

   ![Data_Flow](/images/Data_Flow.png)

3. Double-click the **Data Flow Task** to switch to the **Data Flow tab**.

4. Drag and drop a **Flat File Source** task.

   ![flat_file](/images/flat_file.png)

   

5.  Double-click on the "Flat File Source" component to open the editor and configure the flat file connection manager.

   1. In the "Flat File Connection Manager" editor, click on the "Browse" button next to the "File name" field. 

      ![flat_file](/images/Audit/image-3.png)

   2. Navigate to the location of the CSV file you want to use as the source and Select the CSV file and click "Open" to populate the "File name" field with the file path.

      ![flat_file](/images/Audit/image-4.png)

   3.  Click the "Columns" tab and verify that the columns from your CSV file are correctly detected,click "OK" to save the settings and close the "Flat File Connection Manager" editor.

      ![flat_file](/images/Audit/image-5.png)

   4. Click "OK" to save the settings and close the "Flat File Source" editor.

      ![flat_file](/images/Audit/image-6.png)

6. Drag and drop a **Audit** task.

   ![flat_file](/images/Audit/image-7.png)

7. Connect the Flat File Source Task and the Audit Task.

   ![flat_file](/images/Audit/image-8.png)

8. Right Click on the Audit Task and Click **Edit**

   ![flat_file](/images/Audit/image-9.png)

9. On the **Audit Transform Editor** Select the **Machine Name** Audit Type.

   ![flat_file](/images/Audit/image-10.png)

   10. Repeat the step 9 for all other Audit Types.

       ![flat_file](/images/Audit/image-11.png)

11. Drag and drop a **Flat File Destination** task.

    ![flat_file](/images/Audit/image-12.png)

   12. Connect the  **Audit Task** and **Flat File Destination**

       ![flat_file](/images/Audit/image-13.png)

13. Right Click on the **Flat File Destination** task and Click **Edit**.

    ![flat_file](/images/Audit/image-14.png)

14. On the Flat File Destination Click **New** and Select **Overwrite data in the file**.

    ![flat_file](/images/Audit/image-15.png)

15. Select the **Delimited** on the **Flat File Format** and Click **OK**

    ![flat_file](/images/Audit/image-16.png)

16. Change the **Connection manager name** and Click on **Browse** on the **Flat File Connection Manger Editor**.

    ![flat_file](/images/Audit/image-17.png)

17. Navigate to the location of the CSV file you want to use as the source and Select the CSV file and click "Open" to populate the "File name" field with the file path.

    ![flat_file](/images/Audit/image-18.png)

18. Click the "Columns" tab and verify that the columns from your CSV file are correctly detected,click "OK" to save the settings and close the "Flat File Connection Manager" editor.

    ![flat_file](/images/Audit/image-19.png)

19. Click the "Mapping" tab and verify the column mappings ,click "OK" to save the settings and close the "Flat File Destination" editor.

    ![flat_file](/images/Audit/image-20.png)