pyspark
=======
Pyspark is version of Spark for python

1. How to use    
    read DataFrame    
    ```python
    from pyspark.sql import SQLContext, SparkSession, Window
    import pyspark.sql.functions as F
    jdbc_url = 'jdbc:mysql://{0}:{1}/{2}?user={3}&password={4}'.format('server adress', 'port', 'DB name', 'user id', 'password')

    sc = SparkSession.builder.getOrCreate()
    sqlContext = SQLContext(self.sc)
    df = sqlContext.read.format('jdbc').options(driver='com.mysql.cj.jdbc.Driver', url=jdbc_url, dbtable='table name', serverTimezone='UTC').load()

    ```
    filter data    
    ```python
    df.filter(F.col('column name') 'condition') # find condition data
    df.filter(F.col('column name').isin('list object')) # find data in list
    ```
    condition :  <, >, =>, <=, == ....    
    Window is powerful to index    
    ```python
    w = Window().partitionBy('partition column').orderby('order column')
    # w = Window().partitionBy('partition column').orderby(F.col('column name').desc()) # descending order 
    df.select('*', F.row_number().over(w).alias('new column')).where(F.col('new column') <= limit_num) # decending limit
    ```
    row_number() : numbering by row

    join function
    ```python
    tmp_df = df.filter('column1' < 1)
    df.join(tmmp_df.select('column2', 'column3'), on='column1')
    ```
    