README.md:

# Hadoop Log Analysis and N-Gram Frequency Processing 💻🚀

This project demonstrates how to set up a Hadoop cluster in Docker, run Hadoop streaming jobs, and analyze real log data using custom MapReduce programs. It showcases Hadoop's distributed processing capabilities with Docker and Python-based MapReduce tasks, providing insights into N-Gram analysis and log data analytics.

## Project Structure 🗂️

### Part 1: Setting up Hadoop in Docker 

In this part, we set up Hadoop in Docker and ran a default WordCount example program to verify the setup.

#### Steps:
1. **Run the WordCount program:**
   ```bash
   bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-3.2.1.jar wordcount input/ output/
   ```
2. Display the output in HDFS:
   
   ```bash
   hdfs dfs -cat output/*
   ```

Part 2: N-Gram Frequency Analysis in Hadoop 

Developed a Hadoop program using Python scripts to compute n-gram frequencies from a text file.

Steps:

1. Transfer files to HDFS:

 ```bash
   hdfs dfs -put ngram_input.txt /part2
 ```

```bash
  hdfs dfs -put ngram_mapper.py /part2
 ```

```bash
  hdfs dfs -put ngram_reducer.py /part
 ```

2. Run the Hadoop streaming job:

   
```bash
  bin/hadoop jar share/hadoop/tools/lib/hadoop-streaming-3.2.1.jar \
 ```

```bash
 files ngram_mapper.py,ngram_reducer.py \
 ```

```bash  
mapper "python3 ngram_mapper.py" \
 ```

```bash  
reducer "python3 ngram_reducer.py" \
 ```

```bash  
input /ngram_input.txt \
 ```

```bash  
output /output_ngram
 ```

3. Display the output in HDFS:

```bash  
hdfs dfs -cat /output_ngram/*
 ```

Part 3: Log Data Analysis with Hadoop 

Using real-world anonymous log data, we created MapReduce programs to answer several questions by analyzing the log entries.

Steps:

1. Transfer log data and scripts to HDFS:

```bash  
hdfs dfs -put access_log /part3
 ```

```bash  
hdfs dfs -put part3_mapper.py /part3
 ```

```bash  
hdfs dfs -put part3_reducer.py /part3
 ```


2. Run the Hadoop streaming job for log analysis:

```bash  
bin/hadoop jar share/hadoop/tools/lib/hadoop-streaming-3.2.1.jar \
```

```bash  
file part3_mapper.py,part3_reducer.py \
```

```bash  
mapper "python3 part3_mapper.py" \
```

```bash  
reducer "python3 part3_reducer.py" \
```

```bash  
input /access_log \
```

```bash  
output /output_part3final
```

3. Display the output in HDFS:

```bash  
hdfs dfs -cat /output_part3final/*
```

4. Run a second log analysis job for specific queries:


```bash  
bin/hadoop jar share/hadoop/tools/lib/hadoop-streaming-3.2.1.jar \
```

```bash  
file part3_q4910_mapper.py,part3_q4910_reducer.py \
```

```bash  
mapper "python3 part3_q4910_mapper.py" \
```

```bash  
reducer "python3 part3_q4910_reducer.py" \
```

```bash  
input /access_log \
```

```bash  
output /output_part3q4910
```


5. Display the output in HDFS:

```bash  
hdfs dfs -cat /output_part3q4910/*
```


## Key Skills Demonstrated 🧑‍💻

- Hadoop & MapReduce: Distributed processing of large-scale data using Hadoop and MapReduce.
- Docker: Virtualized environment setup for Hadoop cluster management.
- Python: Custom n-gram frequency analysis and log file parsing using MapReduce in Python.
- Data Processing & Analytics: Processing real-world log files for meaningful insights.
  
