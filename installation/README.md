# Installing OpenRefine

OpenRefine is available for Windows, Mac OS X, and Linux. Please note that laptops/devices running mobile operating systems and web app platforms (Chrome OS, Android, iOS) are NOT supported by OpenRefine. OpenRefine requires a working Java runtime environment, otherwise the program will not start.

The latest stable release of OpenRefine is version 3.1. You may download it [here](http://openrefine.org/download.html).

| Platform | Installation Instructions |
---------|---------------------------|
| Windows  | Download the ZIP package, unzip, and double-click `openrefine.exe` to start. |
| Mac OS X | Download the DMG package, open, drag the application icon into the Applications folder, and double click it to start. |
| Linux | Download the TAR package, extract it, and run `./refine` to start. |

#### OpenRefine Install Test

Upon launch, OpenRefine will run as a local server, opening your computer's browser. As long as OpenRefine is running, you can point your browser at http://127.0.0.1:3333/ to use it, even in several browser tabs/windows.

# Installing Extensions for OpenRefine

> **Some of this information is copied from https://github.com/OpenRefine/OpenRefine/wiki/Installing-Extensions**

Extensions can be installed in two locations. Either in the OpenRefine `workspace` directory (where all the OpenRefine project files are stored) or in the directory in which you have installed OpenRefine itself. In both cases extensions are installed by copying files into a directory called "extensions".

Extensions installed in the `workspace` directory are available to any version or install of OpenRefine you run which uses that workspace, whereas extensions installed in the OpenRefine directory are only available to that particular version/installation of OpenRefine.

**To find the correct directory either:**

1. Find the OpenRefine folder on your computer, and locate the `extensions` folder/directory (usually this will be similar to `/OpenRefine/webapp/extensions`). If the `extensions` directory doesn't already exist, you can create it OR

2. In OpenRefine's front page (http://127.0.0.1:3333/ ), click `Open Project` and then click the `Browse workspace directory` link at the bottom of the project list. This should open up the workspace directory in your system's file browser. In the workspace directory, create a sub-directory called `extensions` if there isn't one already.
    - For Linux, by default the workspace directory will be at `~/.local/share/openrefine/`
    - For Mac, by default the workspace directory will be at `~/Library/Application Support/OpenRefine`

# Installing the RDF Extension for OpenRefine

1. Download the latest release of the RDF extension from [here](https://github.com/stkenny/grefine-rdf-extension/releases).
2. Unzip the extension into the `extensions` directory (this should create a sub-directory within the extensions directory which holds all of the files for the extension)
3. Start (or restart) OpenRefine
4. You will see the RDF extension in the drop down menu in the top right corner. 
![rdf-extension.PNG](/images/rdf-extension.PNG)

**Note:** Some extensions are more visible than others upon installation. Read the extensions documentation to see how to use it and how it appears in the OpenRefine interface (e.g. if the extension is supposed to appear in the upper right of your working window next to the "Extensions:" label, or if it works through the use of drop-downs or added functions within GREL).

**Note:** Not all extensions are compatible with all versions of OpenRefine. Check the extension documentation and ask the developers of the extension or the OpenRefine community for information about compatibility.

# Adding the LCSH Reconciliation Service

Once you have successfully installed the RDF extension, you are ready to add the LCSH Reconciliation Service. Click the RDF button in the dropdown menu in the top right corner, select Add reconciliation service, Based on SPARQL endpoint. In the dialog, you tell OpenRefine how to access the controlled vocabulary. Provide the following parameters:

Name: LCSH
Endpoint URL: http://sparql.freeyourmetadata.org/
Graph URI: http://id.loc.gov/authorities/subjects
Type: Virtuoso
Label properties: check only `skos:prefLabel`

This instructs OpenRefine to create an LCSH reconciliation service that reads the vocabulary identified by http://id.loc.gov/authorities/subjects from our endpoint. The vocabulary is loaded in Virtuoso (a database type) and uses SKOS for labels.
