### Directory structure
**AFINN.txt**: Dictionary of words which describes the sentiments of words on a dictionary of -5 to 5.
**id_tweets.txt**: A set of tweets with the user_id in the format `message$#$user_id`
**Sentiment_Analysis.java**: Java code of Driver class, Map and Reduce.
**ex**: Directory which contains the files compiled by java, namely: Sentiment_Analysis.class, Sentiment_Analysis$Map.class, Sentiment_Analysis$Reduce.classand the jar file of these 3 classes.
**part-r-00000**: The sentiment analysis of tweets done using map-reduce.

### Commands which could be helpful:
// twitter.jar is jar file made from the driver class (Sentiment_Analysis class)<br/>    
`javac -cp $(hadoop classpath) Sentiment_Analysis.java` <br/>    

// ex contains 3 .class files & mind the .(dot) in the end <br/>    
`jar -cvf twitter.jar -C /home/subtleseeker/Desktop/sentiment_analysis2/00/ex .` <br/>    


// Get into directory where AFINN.txt and twitter.jar is present and execute:

`hdfs dfs -put AFINN.txt /`   <br/>      
`hdfs dfs -mkdir /input`    <br/>    
`hdfs dfs -mkdir /output`<br/>    
`hdfs dfs -put id_tweets.txt /input`<br/>    
`hadoop jar twitter.jar /input /output`<br/>    
