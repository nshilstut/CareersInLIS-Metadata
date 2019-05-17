# Importing data into OpenRefine

> **If you haven't installed OpenRefine yet, follow the instructions [here](/installation/README.md)**.

OpenRefine can import TSV, CSV, Excel, JSON, and Google Data documents as well as parse raw, unformatted data copied and pasted using the Clipboard function. For this session, we will use sample data from the TriCollege digital library, [Triptych](http://triptych.brynmawr.edu/cdm/landingpage/collection/BMC_Weddings). 

1. Go [here](/data/ethnic-wedding-photos.csv) and click **View raw**, then right click anywhere on the page, choose **Save as**, and add the extension **.csv** to the file name.
2. Launch OpenRefine by clicking the application file `openrefine.exe`. This will launch the program in a browser window. From OpenRefine's start screen, select **Create Project > Get data from > This Computer > Choose files**, then locate the CSV file you just downloaded, and click **Next** to upload it.
3. You should now see a parsing window, which previews what your data will look like in the main interface. OpenRefine has automatically skipped the first row of data and parsed them to column headers. OpenRefine does not choose a default character encoding, so make sure you set it to **UTF-8.**
4. Click **Create Project**.

![OR Preview](/images/OR-preview-window.png)

## Layout of OpenRefine

OpenRefine displays data in a tabular format, like a spreadsheet, where data lives in the cells at the intersection of a row and a column. 

OpenRefine only displays a limited number of rows of data at one time. You can adjust the number choosing between 5, 10 (the default), 25, and 50 at the top left of the table of data. You can navigate through the records by using the previous/next/first/last navigation options at the top right of the table of data.

OpenRefine has two modes of viewing data: **Rows** and **Records**. Rows is used by default. In this mode, each row represents a single record in the data set. In Records mode, OpenRefine can link together multiple rows as belonging to the same record.

# Assessing and cleaning data

## Splitting & Joining Multi-Valued Cells

When tabular data contains multiple values per field, OpenRefine can easily break them apart and put them back together later when data transformation is complete. Lets try this on the **Subjects** column.

1. Click the upside down triangle next to the Subjects column. 
2. Select **Edit Cells > Split Multi-Valued Cells** in the dropdown menu.
3. Enter " | " (space pipe space, without quotations) as the delimiter.

When we're done, we can rejoin this split data by selecting **Edit Cells > Join Multi-Valued Cells**.

## Undo/Redo

OpenRefine lets you undo (and redo) any number of the transformations you will enact on your imported data. Your Undo/Redo history is stored with the Project and is saved automatically as you work, so the next time you open the project, you can access your full history of transformations; this means you can always try out transformations and wipe them if needed.

![Undo Redo](/images/undo-redo.PNG)

The 'Undo' and 'Redo' options are accessed via the lefthand panel, which lists all the steps you have undertaken. To undo, simply click on the last step you want to preserve in the list. This will automatically wipe out all the changes made after that step. The remaining steps will continue to show as greyed out; you can reapply them by simply clicking on the last step you want to apply. However, if you undo something and then apply new transformations, the greyed out steps will disappear completely, so make sure you don't need to save any of these steps before you get back to work!

## Faceting

Facets allow you to take a macro-level look at a large amount of data by counting individual pieces of column data, and listing them. Filtering allows you to select subsets of your data to act on, instead of changing entire columns. Facet information appears in the left panel of the interface. OpenRefine supports a range of facet types. These include:

- **Text facets** simply list the complete text of each cell and how often those text values exactly appear in the column.
- **Numeric and Timeline facets** display graphs instead of lists of values, with controls to set a start and end range to filter the data displayed.
- **Scatterplot facets** are less commonly used.
- **Custom facets** offer a range of different customized facets, and also allow you write your own.

Now that we've split the values in the **Subjects** column, let's create facets.

1. Click the upside down triangle next to the Subjects column.
2. Select **Facet > Text facet**. A list of values and the number of times they occur appears in the left panel.

![Subject Facets](/images/subjects-facet.PNG)

3. Clicking on any of the entries in the facet list will change the interface to include only the record(s) featuring that facet entry. You can click **reset** to go back to the full list. 
4. If you move your mouse pointer over an entry in the facet window, you can select multiple facet entries using the **include** popup next to each entry. You can also select **invert** at the top of the facet window to select the opposite of the values you chose.
5. If you move your mouse pointer over an entry in the facet window, you'll also see the option to **edit** the term comes up. By changing the text in the edit box and clicking **Apply**, you will automatically change all instances in the data at once.
6. You may also notice that there are some values sorting at the top because they have a leading whitespace. We can remove the extra whitespace by clicking the dropdown menu and choosing **Edit Cells > Common transformations > Trim leading and trailing whitespace**.

## Filtering

You can also apply text filters which look for a particular piece of text appearing in a column. 

1. On the **Subjects** column, click the upside triangle again and choose **Text filter** from the dropdown menu. In the facet area, a filter box will appear. 
2. Try typing "wedding" to display only rows which contain that text.

## Clustering

Clustering is OpenRefine's method of algorithmically comparing a column's data against itself to look for inconsistencies. It uses two methods (Key Collision and Nearest Neighbor) with different functions to look for potential data inconsistencies.

1. On the Subjects facet window, close all filters or individual data selections, and click the **Cluster** button at the top right corner.
2. The Clusters from our dataset are mostly capitalization inconsistencies. For each, you have the option of merging the values together or replacing inconsistencies with a single, consistent value. By default, OpenRefine uses the most common value in the cluster as the new value, but you can select one of the other values by clicking the value itself, or you can simply type the desired value into the **New Cell Value** box.

![Clustering](/images/clustering.PNG)

> **Questions?**
> **In the next section we will try out [validating and exporting our data](/instructions/validating-and-exporting.md).** 
