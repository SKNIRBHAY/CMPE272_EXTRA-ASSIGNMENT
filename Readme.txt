Server log analysis is an ideal use case for Spark. It's a very large, common data source and contains a rich set of information. Spark allows you to store your logs in files on disk cheaply, while still providing a quick and simple way to perform data analysis on them. In this assignment I have shown how to use Apache Spark on real-world text-based production logs and fully harness the power of that data. 

Log data comes can come from following sources: 

Web 
File
Computer servers 
Application logs, 
User-generated content (can be used for monitoring servers, improving business and customer intelligence etc.)



A sample code: 

This code gives any 20 hosts that have accessed the server more than 10 times

# Any hosts that has accessed the server more than 10 times.
hostCountPairTuple = access_logs.map(lambda log: (log.host, 1))

hostSum = hostCountPairTuple.reduceByKey(lambda a, b : a + b)

hostMoreThan10 = hostSum.filter(lambda s: s[1] > 10)

hostsPick20 = (hostMoreThan10
               .map(lambda s: s[0])
               .take(20))

print 'Any 20 hosts that have accessed more then 10 times: %s' % hostsPick20

WORK DONE : In this project the tasks performed in the web server log analysis are : 
1) Parsing each log line using regular expression search function. 
2) Creating RDD of the parsed RDD log file. 
3) Statistical analysis of the size of content returned by the web server. 
4) Plotting the above statistical analysis on pie plot using matplotlib. 
5) Finding out the frequent hosts. 
6) Visualize the number of hits to endpoints (URIs) in the log again using matplotlib.


I have created two graphs:

A pie chart on statistics about the sizes of content being returned by the web server
A bar graph to visualize the number of hits to endpoints (URIs) in the log