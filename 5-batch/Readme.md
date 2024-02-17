Readme

Start VM => ssh vm => mkdir spark => cd spark

Download OpenJDK 11 or Oracle JDK 11 (It's important that the version is 11 - spark requires 8 or 11)
```
wget https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_linux-x64_bin.tar.gz
```
Unpack it:
```
tar xzfv openjdk-11.0.2_linux-x64_bin.tar.gz
```
Remove the archive:
```
rm openjdk-11.0.2_linux-x64_bin.tar.gz
```
define JAVA_HOME and add it to PATH:
```
export JAVA_HOME="${HOME}/spark/jdk-11.0.2"
export PATH="${JAVA_HOME}/bin:${PATH}"
```

```
which java
java --version
```
### Installing Spark
Download Spark. Use 3.5.0 version:
```
wget https://dlcdn.apache.org/spark/spark-3.5.0/spark-3.5.0-bin-hadoop3.tgz
```
Unpack:
```
tar xzfv spark-3.5.0-bin-hadoop3.tgz
```
Remove the archive:

```
rm spark-3.5.0-bin-hadoop3.tgz
```
Add it to PATH:

```
export SPARK_HOME="${HOME}/spark/spark-3.5.0-bin-hadoop3"
export PATH="${SPARK_HOME}/bin:${PATH}"
```
to test run:

```
spark-shell
```

Add paths to .bashrc
```
nano .bashrc
```



### PySpark

To run PySpark, we first need to add it to PYTHONPATH:
```
export PYTHONPATH="${SPARK_HOME}/python/:$PYTHONPATH"
export PYTHONPATH="${SPARK_HOME}/python/lib/py4j-0.10.9.7-src.zip:$PYTHONPATH"
```
Now let's run ipython (or jupyter notebook) and execute:

import pyspark
from pyspark.sql import SparkSession
```
spark = SparkSession.builder \
    .master("local[*]") \
    .appName('test') \
    .getOrCreate()

df = spark.read \
    .option("header", "true") \
    .csv('taxi+_zone_lookup.csv')

df.show()
```
Test that writing works as well:

```
df.write.parquet('zones')
```


