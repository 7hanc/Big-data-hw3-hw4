# Big-data (hw3)

# Homework 3 (Spark MapReduce programming)

> Goal
* Practice Spark MapReduce programming on Hadoop platform. You may choose either one program language from Java, Scala, and Python to implement your program on Spark.
>> Dataset
* Taxi data: http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml
> Question
* Q1: Implement a MapReduce program to count occurrences of each word in the attached article (IhaveaDream.txt).
  * A: Show the top 20 most frequent occurring words and their counts.
  * B: According to the word counting result, can you summarize this article by using some keywords? Show at least three keywords you choose and the reason of choosing these words.
* Q2: Implement a MapReduce program to calculate the average number of passengers in one trip for each "Payment_type" in 2015 NYC Yellow Taxi trip data. In NYC Taxi data, the "Passenger_count" is a driver-entered value. Explain how you deal with the data loss issue.
* Q3: For each of the above task 1 and 2, compare the execution time on local worker and yarn cluster. Also, give some discussions on your observation.
***
Answer 1:   
Step1: upload txt file to hdfs.   
`hdfs dfs -put /home_il/s31tsm40/IhaveaDream.txt hw.txt`   
Step2: turn to spark environment   
`spark-shell \\ will turn to "scala>"`   
Step3: open txt file which is in hdfs   
`val textFile = sc.textFile("hw.txt")`   
Step4: use mapreduce method to count the words   
`val counts = textFile.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey(_+_)`   
Step5: save the result to the directory   
`counts.saveAsTextFile("output")`   
Step6: download the “output” directory to the localhost   
`hdfs dfs -get output /home_il/s31tsm40`   
![a](https://i.imgur.com/wAEGcWF.jpg])

