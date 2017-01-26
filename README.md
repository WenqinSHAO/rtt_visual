# What is it about?
Visualization tool for RTT trace manual labeling. 

# How to perform manual labeling with the these tools
Example trace is given in the example folder.
Following instruction will be based on the example trace.

## Convert to .xlsx to .csv
Some among you might have traces stored in .xlsx file.
Please first convert it to .csv format using [xlsx2csv.py](./xlsx2csv.py).
Some of the these .xlsx files might contain invalid or empty rows.
These rows will lead to errors in conversion. 
Please remove them manually.

For example, to convert all the .xlsx in the example folder, you can do:
```
$ python xlsx2csv.py -d example/
```

If you were to convert one specific file:
```
$ python xlsx2csv.py -f example/11017.xlsx
```

The resulted .csv file will be stored in the same folder, and have same file prefix.

## Visualize trace
Once .csv files are ready, you can visualize the trace with [visual.py](./visual.py).
The script will produce an .html file and a .txt file with same file prefix.
The usage of .txt file will be introduced in the next section.

For example, to visualize the example trace [example/11017.csv](example/11017.csv):
```
$ python visual.py -f example/11017.csv
```

The produced html look like the following:
![Interactive web page for RTT data inspection](example.png)

With the pan and zoom tool present at the right side, 
details of the RTT trace can be clearly seen.

## Label data
As shown in the above screen shoot, when hover the cursor over certain datapoint,
the pop-up window givens your detailed information of this datapoint.

Please label datapoint by recording the index shown in the hover pop-up in
the previous produced .txt file.
One index per each line.
Please check [example/11017.txt](example/11017.txt) for the exact format.

## Check labeling
Once you've finished labeling one trace, it is recommended to check the
labeled datapoints in a visual way.
With the following command:
```
$ python visual.py -u -f example/11017.csv
```
the .html file will be updated (the __-u__ option) by integrating the indexes
specified in the .txt.
Labeled data will be presented in red square as show in the previous screen shoot.

## Patch operation
It is recommended to label trace and check labeling one by one.
Still it is possible to generate and update .html files in patch.
```
$ python visual.py -d example/
$ python visual.py -u -d example/
```
The above two commands treat all the .csv files in the given directory.




