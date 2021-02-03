# DMatrix
- Toward Fast and Accurate Queries in Graph Stream Summarization

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
