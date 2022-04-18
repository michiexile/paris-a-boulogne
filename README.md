# paris-a-boulogne

The train map "Ligne de Paris à Boulogne: servive du 1er août 1852" showing train schedules for the Paris - Boulogne service on August 1 1852 has seen some fame in the data visualization literature - most notably as the cover illustration for Edward Tufte's *The Visual Display of Quantitative Information*. The map showed up in Étienne-Jules Marey's *La méthode graphique*, and has often been attributed to Marey, but Marey writes that it was constructed by Mr Charles Ibry. This method of display was also in early use in Russia. For more information, [this blog post](https://sandrarendgen.wordpress.com/2019/03/15/data-trails-from-paris-with-love/) is useful.

Reading the information off of the archival display at BnF Gallica [here](https://gallica.bnf.fr/ark:/12148/btv1b531360656/f1.item.zoom), I have digitized the arrival and departure times to make the data available for anyone wanting to reconstruct or redesign this particular data display.

## Data Layout

The data is organized into 4 tables, 3 with data and 1 with metadata and a log of my data cleaning:

### Cities and Distances

* `City` - name of each city, in the abbreviated form occurring on the train map itself. So instead of `Saint-Just-en-Chaussée` or `Ailly-sur-Noye`, this variable lists `St Just` and `Ailly s.N.`
* `Distance` - distance in kilometers from Paris to each stop, as listed on the left hand side of the train map.

### Timestamps

* `Year`, `Month`, `Day`, `Hour`, `Minute` - date and time for each tick mark and grid line in the train map.
* `Label` - labels for the labelled tick marks
* `Group Label` - labels for the curly brackets over the time ticks, that divide into `Nuit` (night, 18.00-06.00) and `Jour` (day, 06.00-18.00)

### Trains

* `Train Number` - train number as written on the train map. Some trains are *facultatif*, which occassionally is written out, and occassionally abbreviated to `fac` or `fac.`. Some trains are unlabeled, especially the hourly Paris - Enghien and Enghien - Paris shuttles. I have tried to trace the progress of individual trains through the map, and connect the segments that seem to belong to each train label: not every segment is labeled, and for some trains, with long delays in the middle, it is non-trivial to match segment to train number.
* `Start City` - start city for each segment.
* `Start Time` - time of day for the start of each segment.
* `End City` - end city for each segment.
* `End Time` - time of day for the end of each segment.
* `Line Style` - line style used in the diagram. `solid`, `dashed` or `dot-dashed`.

Notice that a few of these segments loop around midnight, so we have entries such as:

```
102,Beaumont,23:50:00,Pontoise,00:45:00,dashed
```

## Train itinerary

The stops on this line are:

* Paris
* Enghien-les-Bains (inner suburb of Paris)
* Pontoise
* Beaumont-sur-Oise
* Creil
* Clermont
* Saint-Just-en-Chaussée
* Breteuil
* Ailly-sur-Noye
* Amiens
* Abbeville
* Montreuil
* Boulogne-sur-Mer
