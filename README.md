
# Chinook Database Report

### Dashboard Link : https://app.powerbi.com/groups/me/reports/75055d27-1722-4269-8655-42630def6790/fa54608890ec031c8657?experience=power-bi&bookmarkGuid=33fea0ead2a3dba61867

## Problem Statement

The Chinook database report is to analyze the sales performance, customer behavior, and operational efficiency of the Chinook music store to derive actionable insights for business improvement.

The Chinook database contains data about the store's media sales, customers, employees, and inventory. The key entities in the database include Albums, Artists, Customers, Employees, Genres, Invoices, InvoiceLines, MediaTypes, Playlists, PlaylistTracks, and Tracks. This reports goal is to leverage this data to understand sales patterns, customer preferences, and the performance of various store components.

### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : One by One 10 file was loaded to Power BI Desktop.
- Step 3 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 4 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 5 : It was observed that in none of the files columns errors were present. But in some files Empty values were present.
- Step 6 : In Model View relationships were established between all files based on their primary and foreign key. Moreover all foreign keys were made hidden on all files.  
- Step 7 : A New Calculated column been added to the Customer table name Full Name to join First Name and Last Name.

for creating new column following DAX expression was written;

        Full Name = Customer[FirstName] & " " & Customer[LastName]
- Step 8 : New Calculated column was added to the Employee table named as Full Name to combine First Name and Last Name.

for creating new column following DAX expression was written;

        Full Name = Employee[FirstName] & " " & Employee[LastName] 
- Step 9 : New Calculated column was added to the InvoiceLine table named as Amount to calculate total revenue.

for creating new column following DAX expression was written;

        Amount = InvoiceLine[UnitPrice] * InvoiceLine[Quantity]             
- Step 10 : Measure table was created to store measures and new measure was created to find Total Albums.

Following DAX expression was written for the same,
        
        Total Albums = DISTINCTCOUNT(Album[Title])
- Step 11 : New measure was created to find  Total Amount,
 
 Following DAX expression was written to find Total Amount,
 
        Total Amount = SUM(Invoice[Total])
- Step 12 : New measure was created to calculate Total Artists.
 
 Following DAX expression was written to find Total Artists,
 
         Total Artists = DISTINCTCOUNT(Artist[Name])
- Step 13 : New measure was created to calculate Total Composers.
 
 Following DAX expression was written to find Total Composers,
 
        Total Composers = DISTINCTCOUNT(Track[Composer])
- Step 14 : New measure was created to calculate Total Customers.
 
 Following DAX expression was written to find Total Customers,
 
        Total Customers = DISTINCTCOUNT('Customer'[CustomerId])
- Step 15 : New measure was created to calculate Total Genre.
 
 Following DAX expression was written to find Total Genre,
 
        Total Genre = DISTINCTCOUNT(Genre[Name])
- Step 16 : New measure was created to calculate Total MediaType.
 
 Following DAX expression was written to find Total MediaType,
 
        Total MediaType = DISTINCTCOUNT(MediaType[Name])
- Step 17 : New measure was created to calculate Total Playlist.
 
 Following DAX expression was written to find Total Playlist,
 
        Total Playlist = DISTINCTCOUNT(Playlist[PlaylistId])  
- Step 18 : New measure was created to calculate Total Track length.
 
 Following DAX expression was written to find Total Track length,
 
        Total Track length = COUNT(Track[Milliseconds])
- Step 19 : New measure was created to calculate Total Tracks.
 
 Following DAX expression was written to find Total Tracks,
 
        Total Tracks = DISTINCTCOUNT(Track[Name])
- Step 20 : New measure was created to calculate % of Total Tracks Sold.
 
 Following DAX expression was written to find % of Total Tracks Sold,
 
        Total Tracks Sold = SUM(InvoiceLine[Quantity])  
- Step 21 : New measure was created to calculate Average Sales Per Invoice.
 
 Following DAX expression was written to find Average Sales Per Invoice,
 
        Average Sales Per Invoice = AVERAGE('Invoice'[Total])
- Step 22 : New measure was created to calculate Sales By Album.
 
 Following DAX expression was written to find Sales By Album,

        Sales By Album = CALCULATE(
    [Total Amount],
    ALL(Album[AlbumId]
)
) 
- Step 23 : New measure was created to calculate Sales By Artist.
 
 Following DAX expression was written to find Sales By Artist,
 
        Sales By Artist = CALCULATE(
    [Total Amount],
    ALL(Artist[ArtistId])
)
- Step 24 : New measure was created to calculate Sales By Gener.
 
 Following DAX expression was written to find Sales By Gener,
 
        Sales By Gener = CALCULATE(
    [Total Amount],
    ALL(Genre[GenreId]
)
)     
                             
- Step 25 : In the report view, under the view tab, theme was selected.
- Step 26 : Four card visuals were added to the canvas in overview page, one representing Total Album, next one representing Total Artist followed by Total Tracks and Total Composers respectively. Also logo been inserted on the top left corner of the page.
           A line Graph was added below cards on left representing Amount By Year and Quarter. Another Line graph were added below previous line graph representing Amount by Country.
           Two Donut Charts were added on the right side of the page representing Tracks Sold by MediaType & Genre. Below that a matrix representing top 10 Artists by Composers(name, Album, composers, tracks).
           Beside Matrix three cards also added to represent top coustomer by amount followed by that customer's country and amount. And a filter button also been inserted to remove all filters present in the page with a tet box.

 
![Screenshot 2024-07-28 165121](https://github.com/user-attachments/assets/df2cbdc7-e277-4a85-afd3-defd3047e1ad)

# Snapshot of Dashboard (Power BI Service)

![dashboard_snapo]![Screenshot 2024-07-28 165450](https://github.com/user-attachments/assets/e4c043bd-b91b-4446-abe2-e11f89580d21)

 
 # Report Snapshot (Power BI DESKTOP)

![Dashboard_upload] ![Opera Snapshot_2024-07-28_165345_app powerbi com](https://github.com/user-attachments/assets/91a399a5-7eca-44ce-9b62-0af617632ab6)

# Insights

A Single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Files = 11

    Total Albums = 347
    Total Artists = 275 
    Total Genre = 25
    Total Playlist = 18
    Total MediaType = 5
    Total Tracks = 3249
    Total Employee = 8
    Total Customers = 59
    Total Revenue = $2,328.60
    Total Composers = 853
    Total Track Length = 3503
    Total Tracks Sold = 2240

    Some Totals while creating report of sales can be seen easily.
           
### [1] Some other stats
    a) Artist with Most Albums - Iron Maiden
    b) Artist with least Albums - Aaron Copland & London Symphony Orchestra 
    c) Artist with Most Tracks Sold - Iron Maiden
    d) Artist with Least Tracks Sold - Aaron Copland & London Symphony Orchestra
    e) Track with Highest length - 2 Minutes To Midnight
    f) Track with Lowest length - "?"
    g) Media Type with highest track length and most tracks sold - MPEG audio file
    h) Media Type with lowest track length and Least tracks sold - Purchased AAC audio file
    i) Genre with highest track length and most tracks sold - Rock
    j) Genre with lowest track length and Least tracks sold - Opera
    k) Album with highest track length and most tracks sold - Greatest Hits
    l) Album with lowest track length and Least tracks sold - A Copland Celebration, Vol. I
    m) Customer with Highest Revenue - Helena Holý
    n) Customer with Lowest Revenue - Puja Srivastava
    o) Country Generating Highest Revenue - USA
    p) Country Generating Lowest Revenue - Spain


  while Creating Measures and dashboard few stats which can be important. 
  
