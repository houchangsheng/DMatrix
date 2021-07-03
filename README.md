# DMatrix
- DMatrix: Toward Fast and Accurate Queries in Graph Stream

## DMatrix_IPtrace and TCM_IPtrace
- Sketch interface for IP-Trace data
- We should first split the pcap file by time
```
$ editcap -i <seconds> input.pcap output.pcap
```

### Files
- adaptor.hpp adaptor.cpp: extract stream data from pcap files
- sketch.hpp. sketch.cpp: the implementation of DMatrix
- main.cpp\tcm.cpp: the interfaces of query operations in DMatrix\TCM

### Compile and Run
- Compile with make
```
$ make dmatrix\tcm
```
- Run the examples, and the program will output some statistics about the accuracy and efficiency. 
```
$ ./dmatrix\tcm
```
- Note that you can change the configuration of DMatrix\TCM, e.g. the depth, length and width of the sketch.


## DMatrix_Twitter and TCM_Twitter
- Sketch interface for Twitter-Communication data
- We should first split the Twitter file by lines
```
$ split -l <number> input output_
```

### Files
- adaptor.hpp adaptor.cpp: extract stream data from twitter files
- sketch.hpp. sketch.cpp: the implementation of DMatrix
- main.cpp\tcm.cpp: the interfaces of query operations in DMatrix\TCM

### Compile and Run
- Compile with make
```
$ make dmatrix\tcm
```
- Run the examples, and the program will output some statistics about the accuracy and efficiency. 
```
$ ./dmatrix\tcm
```
- Note that you can change the configuration of DMatrix\TCM, e.g. the depth, length and width of the sketch.


## DMatrix_DBLP and TCM_DBLP
- Sketch interface for DBLP co-author data
- We should first split the co-author file by lines
```
$ split -l <number> input output_
```

### Files
- adaptor.hpp adaptor.cpp: extract stream data from co-author files
- sketch.hpp. sketch.cpp: the implementation of DMatrix
- main.cpp\tcm.cpp: the interfaces of query operations in DMatrix\TCM

### Compile and Run
- Compile with make
```
$ make dmatrix\tcm
```
- Run the examples, and the program will output some statistics about the accuracy and efficiency. 
```
$ ./dmatrix\tcm
```
- Note that you can change the configuration of DMatrix\TCM, e.g. the depth, length and width of the sketch.


## Dataset processing
- Programs for processing datasets

### Files
- /Twitter/reorder.sh: process files to scramble by line
- /Twitter/replay.py: randomly replay each line of the file
- /Twitter/pareto_random.py: randomly assign values to twitter edges so that the edge weights meet the Pareto distribution
- /DBLP/GetAuthors.py: obtain the author information of the papers from the dblp dataset
- /DBLP/encoded.py: encode the author so that each author corresponds to an ID
- /DBLP/authors_pair.py: obtain author-pairs

### Processing Twitter Dataset
- We first split the Twitter file by lines and take the first 2,400,000 edges
```
$ split -l <number> input output_
```
- Run 'replay.py', randomly replay each edge 1~9 times
- Scramble file
```
$ sh ./reorder.sh input output_
```
- Split the Twitter file by lines and divide it into 5 parts evenly
```
$ split -l <number> input output_
```
- Run 'pareto_random.py' and randomly assign values by lines so that the edge weights meet the Pareto distribution

### Processing DBLP Dataset
- Run 'GetAuthors.py' to obtain the author information of papers from the DBLP dataset
- Run 'encoded.py' to encode the authors' name so that the name corresponds to the ID one by one
- Extract the author's co-authoring relationship from the author list of papers
