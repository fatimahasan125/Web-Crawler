# Web-Crawler
A simple web crawler in python with a frontier following the mercator scheme


### 1)	URL Frontier 
The URL frontier is a structure of front queues and back queues. When the crawler starts for the first time, URL frontier will contain seed URLs as given below: \
https://docs.oracle.com/en/ \
https://www.oracle.com/corporate/ \
https://en.wikipedia.org/wiki/Machine_learning \
https://www.csie.ntu.edu.tw/~cjlin/libsvm/index.html \
https://docs.oracle.com/middleware/jet210/jet/index.html \
https://en.wikipedia.org/w/api.php \
https://en.wikipedia.org/api/ \
https://en.wikipedia.org/wiki/Weka_(machine_learning) 

The process is multithreaded. Each thread will request a URL from frontier when required. The process of getting data from threads while maintaining politeness and moving data from F-queues to B-queues is done as per the mercator scheme. Prioritizer function is just a stub right now. 
URLS that go out of frontier are maintained in a list 

Newly encountered URL’s will be en-queued after passing through URL filtering and Dup-URL elimination module.  
For this project we wait for 15 to 20 seconds after sending one request to send another request


### 2)	Fetch 
After getting one URL from frontier, we retrieve its content from the webserver. 

### 3)	Parse 
We parse the content of the fetched page and retrieve all the URLS from it. 

### 4)	URL Filter 
In this module we filter the URLs received from parser that are restricted from its webserver. The restricted page/s are given in robot.txt file. 

### 5)	Duplicate URL Elimination  
After filtering restricted URLS, we check if the newly extracted URLs are already crawled or not. The URLS that pass this test are added to the frontier 

### 6)	Stopping the process 
We stop the process when a certain number of urls are crawled
