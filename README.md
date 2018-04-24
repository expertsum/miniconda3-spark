# miniconda3-spark

A Docker image based on Miniconda3 that includes Spark. The image can be used to create Spark standalone clusters on a single host (using docker-compose) or on multiple hosts (using Kubernetes). It can also be used to create a Jupyter notebeook server that can run Spark jobs in local mode through PySpark.

## Contents

- Miniconda3
    - numpy, pandas, matplotlib, scikt-learn, jupyter, ipython & pyspark
- OpenJDK 8
- Spark 2.3.0
- Google Cloud Storage Connector

## Spark Standalone Cluster on a single host (using docker-compose)

See [this](https://github.com/expertsum/spark-docker) repository.

## Spark Standalone Cluster on multiple hosts (using Kubernetes)

See [this](https://github.com/expertsum/spark-kubernetes) repository.

## Jupyter Notebook with PySpark in local mode

To start the server execute the following command:

```
$ docker run --rm -p 8888:8888 elopezdelara/miniconda3-spark jupyter notebook --ip='*' --no-browser --allow-root --NotebookApp.token=''
```

Then from within a notebook execute the following code to create a Spark session and execute a job:

```python
In [1]: from pyspark.sql import SparkSession
        spark = SparkSession.builder.master('local[*]').getOrCreate()
        df = spark.range(10)
        df.count()

Out[1]: 10
```
