### Directory structure
AFINN.txt: Dictionary of words which describes the sentiments of words on a dictionary of -5 to 5.
id_tweets.txt: A set of tweets with the user_id in the format `message$#$user_id`
Sentiment_Analysis.java: Java code of Driver class, Map and Reduce.
ex: Directory which contains the files compiled by java, namely: Sentiment_Analysis.class, Sentiment_Analysis$Map.class, Sentiment_Analysis$Reduce.classand the jar file of these 3 classes.
part-r-00000: The sentiment analysis of tweets done using map-reduce.

### Commands which could be helpful:
// twitter.jar is jar file made from the driver class
javac -cp $(hadoop classpath) Sentiment_Analysis.java

// ex contains 3 .class files &&&&&&& mind the . in the end
jar -cvf twitter.jar -C /home/subtleseeker/Desktop/sentiment_analysis2/00/ex .


// Get into directory where AFINN.txt and twitter.jar is present and execute:

hdfs dfs -put AFINN.txt /    
hdfs dfs -mkdir /input     
hdfs dfs -mkdir /output
hdfs dfs -put id_tweets.txt /input
hadoop jar twitter.jar /input /output