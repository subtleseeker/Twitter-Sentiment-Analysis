# Twitter Sentiment Analysis

## Directory structure
- **AFINN.txt**: Dictionary of words which describes the sentiments of words on a dictionary of -5 to 5.  
- **id_tweets.txt**: A set of tweets with the user_id in the format `message$#$user_id`  
- **Sentiment_Analysis.java**: Java code of Driver class, Map and Reduce.  
- **code**: Directory which contains the files compiled by java, namely: Sentiment_Analysis.class, Sentiment_Analysis$Map.class, Sentiment_Analysis$Reduce.class and the jar file of these 3 classes.  
- **part-r-00000**: The sentiment analysis of tweets done using map-reduce.  

## Procedure
1. Write the map-reduce program in a file named `Sentiment_Analysis.java`. The file contains different classes namely 
  - `Map` with the parent class `Mapper`
    - `setup` function for reading the input file
    - `map` function for converting the input lines to intermediate key-value pairs.
    
  - `Reduce`
    - `reduce` function is converting intermediate key-value pairs to final key-value pairs. In this case, both of them are same.       
2. Create the jar file for the required classes. `twitter.jar` is jar file made from the driver class (Sentiment_Analysis class)      
```javac -cp $(hadoop classpath) Sentiment_Analysis.java```    

3. Folder `code` contains three `.class` files (mind the .(dot) in the end)     
```jar -cvf twitter.jar -C /home/subtleseeker/Desktop/sentiment_analysis2/00/codeF .```     


4. Get into directory where AFINN.txt and twitter.jar is present and execute the following commands. This will copy the data from the local harddisk to the hadoop filesystem.

```
hdfs dfs -put AFINN.txt /
hdfs dfs -mkdir /input
hdfs dfs -put id_tweets.txt /input
```

5. Finally execute the jar file to run the program for sentiment analysis.   
```
hadoop jar twitter.jar /input /output
```   

## Input
The input file consisted of many tweets in the following format:   
```<id> <tweet>```
which was then converted to 
```<tweet>$#$<id>```
   
The other file `AFINN.txt` consisted of a dictionary of words which are considered for sentinel analysis.  

## Output Screenshot
[Screenshot of the output](./ss.png)

The output is stored in the file `part-r-00000`.   
To check the complete output, check the file `terminal.txt`. 



