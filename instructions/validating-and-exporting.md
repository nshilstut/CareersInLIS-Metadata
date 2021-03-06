# Validating Data

## Reconciliation

[Reconciliation](http://freeyourmetadata.org/reconciliation/) allows you to match your data against external data services to reconcile known entities. The goal of reconciliation is to connect your collection-specific vocabulary to a controlled vocabulary on the Web.

## Wikidata Reconciliation

Let's try reconciling the **Place** column against [Wikidata](https://www.wikidata.org/wiki/). 

1. On the Place column, click the upside down arrow and choose **Reconcile > Start reconciling** from the dropdown menu. 
2. Choose **Wikidata** under "Services," and select **city of the United States** under "Reconcile each cell to an entity of one of these types."
3. Select **Auto-match candidates with high confidence**.
4. Click **Start reconciling**. It may take a couple of minutes to complete.

You should now see 168 values that automatched in the judgment window in the left pane. This is because the judgement score on each search had a high enough probability that the Wikidata match was correct. If we filter by the **matched** values in the judgment window, we'll see that each value is now a link that takes us to the Wikidata record. 

![Judgment Window](/images/judgment-window.PNG)

If we filter by **none** in the judgment window, we'll see the values that did not automatch, along with possible matches sorted by probability of match. For "Chicago, IL" we see that "Chicago" has an 82% probability of a match, followed by "West Chicago" (73%) and "North Chicago" (70%). We can also choose to create a new item or search again for a match. If we select "Chicago" as the match, we can either match just this cell or match all identical cells.

In situations when there are no matches and no search results, you may need to do some research to figure out a better value to use. For example, if we Google "Seal Harbor, ME" we'll find that this is a village in Mount Desert, ME. When we enter "Mount Desert, ME" we get a hit for "Mount Desert town in Maine."

Once we are done validating all of our unmatched values against Wikidata values, we should extract the [URIs](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) (Uniform Resource Identifiers) for each value. We will do this using GREL.

Transformations in OpenRefine are ways of manipulating data in columns beyond facets and filters. Transformations are predominantly written in **GREL**, or General Refine Expression Language. If you are familiar with Python commands or Excel formulas, you may see a number of similarities in GREL. Read more about GREL functions [here](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Functions).

On the **Place** column, select **Edit column > Add column based on this column**. Name this column **placeIDs**. In the transformation window, enter this GREL: 

`'https://www.wikidata.org/wiki/' + cell.recon.match.id'`

This will not only extract the identifier for the entity, but create the full Wikidata URI.

Once you have this new column, reconciliation data can be dispatched by selecting **Reconcile > Actions > Clear reconciliation data**.

# Getting Data Out of OpenRefine

When your data has been cleaned to your satisfaction, you can export it to a variety of different file formats. Be sure all text filters and facet windows are closed, and that you have joined any split multi-valued data before you export! 

Clicking on the **Export** button in the upper right corner of the screen will display the export file formats available. **Export Project**, on the other hand, will save a copy of your Refine project as a TAR archive that can be shared with other people and opened in other Refine installations.

OpenRefine's **Templating** function allows you to export your data in a "roll your own" fashion. As OpenRefine's wiki states, "this is useful for formats that we don't support natively yet, or won't support." Currently, Templating is set up to generate a single JSON document of your data by default; with a few changes, we can set up a template to put our enriched data out to, say, an XML file. You'll need to fill out these spaces with the below template:

Prefix:
```
<?xml version="1.0" encoding="UTF-8"?>
<records>
[blank line break]
```
**Row template:**
```
    <record>
        <title>{{escape(cells["Title"].value,"xml")}}</title>
        <ethnicGroup>{{escape(cells["Ethnic Group"].value,"xml")}}</ethnicGroup>
        <place>{{escape(cells["Place"].value,"xml")}}</place>
        <placeIDs>{{escape(cells["Place IDs"].value,"xml")}}</placeIDs>
        <date>{{escape(cells["Date"].value,"xml")}}</date>
        <subjects>{{escape(cells["Subjects"].value,"xml")}}</subjects>
        <photographerCategories>{{escape(cells["Photographer's categories"].value,"xml")}}</photographerCategories>
        <photographerNotes>{{escape(cells["Photographer's notes"].value,"xml")}}</photographerNotes>
        <description>{{escape(cells["Description"].value,"xml")}}</description>
        <photographer>{{escape(cells["Photographer"].value,"xml")}}</photographer>
        <scanNo>{{escape(cells["Scan number"].value,"xml")}}</scanNo>
        <institution>{{escape(cells["Institution"].value,"xml")}}</institution>
        <department>{{escape(cells["Department"].value,"xml")}}</department>
        <collection>{{escape(cells["Collection"].value,"xml")}}</collection>
        <databaseInfo>{{escape(cells["Database information"].value,"xml")}}</databaseInfo>
        <rights>{{escape(cells["Rights"].value,"xml")}}</rights>
        <format>{{escape(cells["Format"].value,"xml")}}</format>
        <dateCreated>{{escape(cells["Date created"].value,"xml")}}</dateCreated>
        <dateModified>{{escape(cells["Date modified"].value,"xml")}}</dateModified>
        <referenceURL>{{escape(cells["Reference URL"].value,"xml")}}</referenceURL>
   </record>
```
**Row separator:**
```
[blank line break]
```
**Suffix:**
```
[blank line break]
</records>
```
Once you have pasted in this code, you can click **Export** to download your XML file.

> **If there's time, try out these [Practice Exercises](/instructions/practice-exercise.md), or try them later on your own.**
