# SPARK

## Contributing

- [Contributing Guide](http://spark.apache.org/contributing.html)
- [Versioning Policy](http://spark.apache.org/versioning-policy.html)

<!--What the common contributing model is, give overview of JIRA -->

### Merging Model

<!--Discuss SPARK and ARROW's merging model. Refer to script that is being used-->

- [Merging script](https://github.com/apache/spark/blob/master/dev/merge_spark_pr.py)

### Improving PySpark/Pandas interoperability

The core idea is to Apache Arrow as serialization format to reduce the overhead between PySpark and
Pandas.

- [SPARK-22216](https://issues.apache.org/jira/browse/SPARK-22216)
    - [Introducing Pandas UDF for PySpark How to run your native Python code with PySpark, fast.](https://databricks.com/blog/2017/10/30/introducing-vectorized-udfs-for-pyspark.html?_ga=2.2100599.694686473.1588940385-1981038234.1587459746)
    - [pandas user-defined functions](https://docs.databricks.com/spark/latest/spark-sql/udf-python-pandas.html)

### Project Zen: Improving Python usability

- [SPARK-32082](https://issues.apache.org/jira/browse/SPARK-32082)

This epic tickets aims to improve the usability in PySpark, and make it more Pythonic. To be more
explicit, this JIRA targets four bullet points below. Each includes examples:

* Being Pythonic
    - Pandas UDF enhancements and type hints
    - Avoid dynamic function definitions, for example, at funcitons.py which makes IDEs unable to detect.
* Better and easier usability in PySpark
    - User-facing error message and warnings
    - Documentation
    - User guide
    - Better examples and API documentation, e.g. Koalas and pandas
* Better interoperability with other Python libraries
    - Visualization and plotting
    - Potentially better interface by leveraging Arrow
    - Compatibility with other libraries such as NumPy universal functions or pandas possibly by leveraging Koalas
* PyPI Installation
    - PySpark with Hadoop 3 support on PyPi
    - Better error handling

### GPUs on Spark

GPU support for SPARK. More description here
Video --> HERE. Write notes from what was said. Include other tickets

[SparkGraph review process](http://apache-spark-developers-list.1001551.n3.nabble.com/SparkGraph-review-process-td28037.html)

- [SPARK-24615](https://issues.apache.org/jira/browse/SPARK-24615) SPIP: Accelerator-aware task scheduling for Spark
    Summaries topics in ticket
- [SPARK-20928](https://issues.apache.org/jira/browse/SPARK-20928) SPIP: Continuous Processing Mode for Structured Streaming
    Streaming. Real-time. Latency
- [SPARK-27495](https://issues.apache.org/jira/browse/SPARK-27495) SPIP: Support Stage level resource configuration and scheduling
- [SPARK-27396](https://issues.apache.org/jira/browse/SPARK-27396) SPIP: Public APIs for extended Columnar Processing Support


#### Learning Resources

- [Learning Apache Spark with Python](https://runawayhorse001.github.io/LearningApacheSpark/index.html)
- [Koalas: Pandas on Apache Spark](https://databricks.com/jp/session_eu19/koalas-pandas-on-apache-spark)
- [What is the Catalyst Optimizer?](https://databricks.com/glossary/catalyst-optimizer)
- [Glimpse into Apache Spark 3.0 [Early Access]](https://towardsdatascience.com/glimpse-into-spark-3-0-early-access-c1854327d6c)
- [Spark - Calling Scala code from PySpark](https://aseigneurin.github.io/2016/09/01/spark-calling-scala-code-from-pyspark.html)
- [Big Data with Spark Youtube Playlist](https://www.youtube.com/playlist?list=PLLMXbkbDbVt-f6qwCZqfq7e_6eT8aFxzT)
- [Statistical and Mathematical Functions with DataFrames in Apache Spark](https://databricks.com/blog/2015/06/02/statistical-and-mathematical-functions-with-dataframes-in-spark.html)
- Koalas Tutorial
    - [Part I](https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/8266758089056472/1487766102750011/5693546805547978/latest.html)
    - [Part II](https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/8266758089056472/3786652143501164/5693546805547978/latest.html)
- [AMP Camp Exercises](http://ampcamp.berkeley.edu/6/exercises/index.html)

#### Spark + AI Summit 2019 Europe Playlists
* [Data Engineering](https://www.youtube.com/playlist?list=PLTPXxbhUt-YXHc9yNw7CDouQZ3dKWB2rR)
* [Data Science](https://www.youtube.com/playlist?list=PLTPXxbhUt-YXP4ZS4IdA0m227nbFxrk2x)
* [Data and ML](https://www.youtube.com/playlist?list=PLTPXxbhUt-YVDf1ccKSPJ2DKlqupsFNQi)
* [Developer](https://www.youtube.com/playlist?list=PLTPXxbhUt-YWDqGX3onyYD4Fu6yZxpxCP)
* [AI](https://www.youtube.com/playlist?list=PLTPXxbhUt-YVPzqmXpTTNe0mfRqakzFNi)
