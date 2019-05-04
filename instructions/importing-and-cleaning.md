# Importing data into OpenRefine

1. OpenRefine can import TSV, CSV, Excel, JSON, and Google Data documents as well as parse raw, unformatted data copied and pasted using the Clipboard function. For this session, we will use sample data from Bryn Mawr College'sthe TriCollege digital library, [Triptych](http://triptych.brynmawr.edu/cdm/landingpage/collection/BMC_Weddings). Go [here](/data/ethnic-wedding-photos.csv), right click on **ethnic-wedding-photos.csv**, and click save as CSV.
2. Launch OpenRefine by clicking the application file (openrefine.exe) on your desktop. This will launch the program in a browser window. From OpenRefine's start screen, select Create Project/Get data from/This Computer/Choose files, then click Next to upload the CSV file you just downloaded.
3. You should now see a parsing window, which previews what your data will look like in the main interface. OpenRefine has automatically skipped the first row of data and parsed them to column headers. OpenRefine does not choose a default character encoding, so make sure you set it to UTF-8.
Click Create Project.

# Assessing and cleaning data

## Splitting & Joining Multi-Valued Cells

When tabular data contains multiple values per field, OpenRefine can easily break them apart and put it back together later when data transformation is complete.Lets try this on the Subjects column.

1. Click the upside down triangle Select Edit Cells > Split Multi-Valued Cells on a column's dropdown menu.
Let's try this on the Provenance column. Enter a single pipe character (|) in the pop-up menu:

Whenever we're done, we can rejoin this split data by selecting Edit Cells > Split Multi-Valued Cells and choosing the appropriate delimiter.

## Faceting and filtering 

Facets allow you to take a macro-level look at a large amount of data by counting individual pieces of column data, and listing them. Filtering can also allow you to select subsets of your data to act on, instead of changing entire columns. Facet information appears in the left hand panel in the OpenRefine interface. Refine supports a range of other types of facet. These include:

- **Text facets** simply list the complete text of each cell and how often those text values exactly appear in the column.
- **Numeric and Timeline facets** display graphs instead of lists of values, with controls to set a start and end range to filter the data displayed.
- **Scatterplot facets** are less commonly used.
- **Custom facets** offer a range of different customized facets, and also allow you write your own.

Let's create a facet on the Subjects column. 
1. Click the upside down triangle next to the column name.
2. Select: Facet > Text facet. A new facet should appear in the lefthand window.
Clicking on any of the entries in the facet window will change the interface to include only the record(s) featuring that facet entry. If you move your mouse pointer over an entry in the facet window, you can select multiple facet entries using the Include popup next to each entry. You can also select Invert at the top of the facet window to automatically select the opposite of the values you chose.
If you move your mouse pointer over an entry in the facet window, you'll also see the option to Edit the term comes up. By changing the text in the edit box and clicking Apply, you will automatically change all instances in the data at once.
In terms of assesssment, how much of each represented element/field is empty? Try creating a custom facet for empty values: Facet > Customized Facets > Facet by Blank
The faceted values for True are cells that are empty, giving us an idea of how much data is missing. (Of course, this doesn't answer why the data is missing.)
