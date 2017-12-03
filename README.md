# police-data-analysis

# Background
I recently found an old article about police procurement data:
https://www.police.uk/news/police-procurement-information-now-policeuk/

and thought it would be really interesting to analyse it.

The actual data is available on this site https://www.police.uk/procurement/custodian-style-police-helmet/ and comes as a two zip files, one for equipment and one for services.

The first challenge was to get the data into one big file for analysis. I did the following (with some trial and error).
1. Unzipped both folders into a new directory
2. Renamed the services data folder 'services' and the equipment folder 'equipment'
3. Ran a command to add a new column at the start of the CSV, containing the filename (which is also the Force name).
`````
find . -type f | while read file; do sed -i -e 's_.*_Services,'"$file"',&_' $file > out; done
`````
4. Removed the strange extra files that got created
`````
rm *.csv-e
`````
5. Concatentated all the files
`````
cat * > services.csv
`````
