# Validating Data

## Reconciliation

[Reconciliation](http://freeyourmetadata.org/reconciliation/) allows you to match your data against external data services to reconcile known entities. The goal of reconciliation is to connect your collection-specific vocabulary to a controlled vocabulary on the Web.

## Wikidata Reconciliation

Let's try reconciling the **Place** column against [Wikidata](https://www.wikidata.org/wiki/). 

1. Click the upside down arrow next to the column name and choose Reconcile > Start reconciling from the dropdown menu. 
2. Choose Wikidata under Services, and select "city of the United States" under "Reconcile each cell to an entity of one of these types." 3. Select "Auto-match candidates with high confidence." 
4. Click Start reconciling. It may take a couple of minutes to complete.

You should see 168 values that automatched in the judgment window in the left pane. This is because the judgement score on each search had a high enough probably that the Wikidata match was correct. If we filter by the "matched" values in the judgment window, we'll see that each value is now a link that take us to the Wikidata record. 

If we filter by "none" in the judgment window, we'll see the values that did not automatch along with possible matches sorted by probability of match. For "Chicago, IL" we see that "Chicago" has an 82% probability of a match, followed by "West Chicago" (73%) and "North Chicago" (70%). We can also choose to create a new item or search again for a match. If we select "Chicago" as the match, we can either match just this cell or match all identical cells.

In situations when there are no matches and no search results, you may need to do some research to figure out a better value to use. For example, if we Google "Seal Harbor, ME" we'll find that this is a village in Mount Desert, ME. When we enter "Mount Desert, ME" we get a hit for "Mount Desert town in Maine."

So we're done, right? Nope. All we have right now is the standard Wikidata name form of the entity. This is good, but we still need to extract this name form to its own column, its identifier, or both.

On the Place column, select Edit column > Add column based on this column. Name this column placeIDs. In the transformation window, enter your GREL: 'https://www.wikidata.org/wiki/' + cell.recon.match.id + '/' This will not only extract the identifier for the entity, but create the full Wikidata URI.

Once you have this new column, reconciliation data can be dispatched by selecting Reconcile > Actions > Clear reconciliation data.

## LCSH Reconciliation

Let's try reconciling the **Ethnic Groups** column against [LCSH](http://id.loc.gov/authorities/subjects.html). 

1. Click the upside down arrow next to the column name and choose Reconcile > Start reconciling from the dropdown menu. 
2. Choose LCSH under Services.
3. Select "Auto-match candidates with high confidence." 
4. Click Start reconciling. It may take a couple of minutes to complete.
