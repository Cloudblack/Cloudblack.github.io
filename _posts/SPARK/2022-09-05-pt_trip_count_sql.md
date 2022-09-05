---
date created: 월요일, 9월 5일 2022
date modified: 월요일, 9월 5일 2022
---

<head>
  <style>
    table.dataframe {
      white-space: normal;
      width: 100%;
      height: 240px;
      display: block;
      overflow: auto;
      font-family: Arial, sans-serif;
      font-size: 0.9rem;
      line-height: 20px;
      text-align: center;
      border: 0px !important;
    }

    table.dataframe th {
      text-align: center;
      font-weight: bold;
      padding: 8px;
    }

    table.dataframe td {
      text-align: center;
      padding: 8px;
    }

    table.dataframe tr:hover {
      background: #b8d1f3; 
    }

    .output_prompt {
      overflow: auto;
      font-size: 0.9rem;
      line-height: 1.45;
      border-radius: 0.3rem;
      -webkit-overflow-scrolling: touch;
      padding: 0.8rem;
      margin-top: 0;
      margin-bottom: 15px;
      font: 1rem Consolas, "Liberation Mono", Menlo, Courier, monospace;
      color: $code-text-color;
      border: solid 1px $border-color;
      border-radius: 0.3rem;
      word-break: normal;
      white-space: pre;
    }

  .dataframe tbody tr th:only-of-type {  
      vertical-align: middle;  
  }

  .dataframe tbody tr th {  
      vertical-align: top;  
  }

  .dataframe thead th {  
      text-align: center !important;  
      padding: 8px;  
  }

  .page__content p {  
      margin: 0 0 0px !important;  
  }

  .page__content p > strong {  
    font-size: 0.8rem !important;  
  }

  </style>
</head>

```python
import findspark
findspark.init()
```

```python
from pyspark.sql import SparkSession
```

```python
spark = SparkSession.builder.appName("trip_count_sql").getOrCreate()
```

```python
# directory = 'E:\\GIt작업\\data-engineering\\01-spark\\data'
# filename = 'fhvhv_tripdata_2020-03.csv'
# data = spark.read.csv(f"file:///{directory}/{filename}", inferSchema = True, header = True)
```

# 20년 3월 한달, 일간 택시 이용 수 조회
```python
trip_file = 'E:\\GIt작업\\data-engineering\\01-spark\\data\\fhvhv_trip_file_2020-03.csv'
data = spark.read.csv(trip_file, inferSchema = True, header = True)
```

```python
data.show(5)
```

<pre>
+-----------------+--------------------+--------------------+-------------------+-------------------+-------------------+-------------------+------------+------------+----------+---------+-------------------+-----+----+---------+--------------------+-----------+----+----------+-------------------+-----------------+------------------+----------------+--------------+
|hvfhs_license_num|dispatching_base_num|originating_base_num| request_datetime| on_scene_datetime| pickup_datetime| dropoff_datetime|PULocationID|DOLocationID|trip_miles|trip_time|base_passenger_fare|tolls| bcf|sales_tax|congestion_surcharge|airport_fee|tips|driver_pay|shared_request_flag|shared_match_flag|access_a_ride_flag|wav_request_flag|wav_match_flag|
+-----------------+--------------------+--------------------+-------------------+-------------------+-------------------+-------------------+------------+------------+----------+---------+-------------------+-----+----+---------+--------------------+-----------+----+----------+-------------------+-----------------+------------------+----------------+--------------+
| HV0005| B02510| null|2020-03-01 00:00:12| null|2020-03-01 00:03:40|2020-03-01 00:23:39| 81| 159| 8.655| 1199| 24.45| 0.0|0.54| 1.9| 0.0| null| 0.0| 19.65| N| N| N| N| N|
| HV0005| B02510| null|2020-03-01 00:22:03| null|2020-03-01 00:28:05|2020-03-01 00:38:57| 168| 119| 3.523| 652| 11.88| 0.0|0.24| 0.85| 0.0| null| 0.0| 9.37| N| N| N| N| N|
| HV0003| B02764| B02764|2020-02-29 23:57:45|2020-03-01 00:01:04|2020-03-01 00:03:07|2020-03-01 00:15:04| 137| 209| 4.07| 717| 14.57| 0.0|0.38| 1.38| 2.75| null| 0.0| 16.24| N| Y| |               N| N|
| HV0003| B02764| B02764|2020-03-01 00:04:06|2020-03-01 00:15:48|2020-03-01 00:18:42|2020-03-01 00:38:42| 209| 80| 4.73| 1200| 13.89| 0.0|0.35| 1.23| 0.75| null| 0.0| 21.76| Y| N| |               N| N|
| HV0003| B02764| B02764|2020-03-01 00:42:46|2020-03-01 00:43:18|2020-03-01 00:44:24|2020-03-01 00:58:44| 256| 226| 4.03| 860| 20.2| 0.0|0.51| 1.79| 0.0| null| 0.0| 19.64| N| N| |               N| N|
+-----------------+--------------------+--------------------+-------------------+-------------------+-------------------+-------------------+------------+------------+----------+---------+-------------------+-----+----+---------+--------------------+-----------+----+----------+-------------------+-----------------+------------------+----------------+--------------+
only showing top 5 rows

</pre>

```python
data.createOrReplaceTempView("mobility_data")
```

```python
spark.sql("select * from mobility_data limit 5").show()
```

<pre>
+-----------------+--------------------+--------------------+-------------------+-------------------+-------------------+-------------------+------------+------------+----------+---------+-------------------+-----+----+---------+--------------------+-----------+----+----------+-------------------+-----------------+------------------+----------------+--------------+
|hvfhs_license_num|dispatching_base_num|originating_base_num| request_datetime| on_scene_datetime| pickup_datetime| dropoff_datetime|PULocationID|DOLocationID|trip_miles|trip_time|base_passenger_fare|tolls| bcf|sales_tax|congestion_surcharge|airport_fee|tips|driver_pay|shared_request_flag|shared_match_flag|access_a_ride_flag|wav_request_flag|wav_match_flag|
+-----------------+--------------------+--------------------+-------------------+-------------------+-------------------+-------------------+------------+------------+----------+---------+-------------------+-----+----+---------+--------------------+-----------+----+----------+-------------------+-----------------+------------------+----------------+--------------+
| HV0005| B02510| null|2020-03-01 00:00:12| null|2020-03-01 00:03:40|2020-03-01 00:23:39| 81| 159| 8.655| 1199| 24.45| 0.0|0.54| 1.9| 0.0| null| 0.0| 19.65| N| N| N| N| N|
| HV0005| B02510| null|2020-03-01 00:22:03| null|2020-03-01 00:28:05|2020-03-01 00:38:57| 168| 119| 3.523| 652| 11.88| 0.0|0.24| 0.85| 0.0| null| 0.0| 9.37| N| N| N| N| N|
| HV0003| B02764| B02764|2020-02-29 23:57:45|2020-03-01 00:01:04|2020-03-01 00:03:07|2020-03-01 00:15:04| 137| 209| 4.07| 717| 14.57| 0.0|0.38| 1.38| 2.75| null| 0.0| 16.24| N| Y| |               N| N|
| HV0003| B02764| B02764|2020-03-01 00:04:06|2020-03-01 00:15:48|2020-03-01 00:18:42|2020-03-01 00:38:42| 209| 80| 4.73| 1200| 13.89| 0.0|0.35| 1.23| 0.75| null| 0.0| 21.76| Y| N| |               N| N|
| HV0003| B02764| B02764|2020-03-01 00:42:46|2020-03-01 00:43:18|2020-03-01 00:44:24|2020-03-01 00:58:44| 256| 226| 4.03| 860| 20.2| 0.0|0.51| 1.79| 0.0| null| 0.0| 19.64| N| N| |               N| N|
+-----------------+--------------------+--------------------+-------------------+-------------------+-------------------+-------------------+------------+------------+----------+---------+-------------------+-----+----+---------+--------------------+-----------+----+----------+-------------------+-----------------+------------------+----------------+--------------+

</pre>

```python
spark.sql("select pickup_datetime from mobility_data").show()
```

<pre>
+-------------------+
| pickup_datetime|
+-------------------+
|2020-03-01 00:03:40|
|2020-03-01 00:28:05|
|2020-03-01 00:03:07|
|2020-03-01 00:18:42|
|2020-03-01 00:44:24|
|2020-03-01 00:17:23|
|2020-03-01 00:01:18|
|2020-03-01 00:43:27|
|2020-03-01 00:52:23|
|2020-03-01 00:19:49|
|2020-03-01 00:29:34|
|2020-03-01 00:41:44|
|2020-03-01 00:11:26|
|2020-03-01 00:28:05|
|2020-03-01 00:44:28|
|2020-03-01 00:56:50|
|2020-03-01 00:56:14|
|2020-03-01 00:14:15|
|2020-03-01 00:31:38|
|2020-03-01 00:26:31|
+-------------------+
only showing top 20 rows

</pre>

```python
spark.sql("select split(pickup_datetime,' ')[0] as pickup_date from mobility_data").show()
```

<pre>
+-----------+
|pickup_date|
+-----------+
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
| 2020-03-01|
+-----------+
only showing top 20 rows

</pre>

```python
spark.sql("select pickup_date,count(*) as trips from (select split(pickup_datetime,' ')[0] as pickup_date from mobility_data) group by pickup_date").show()
```

<pre>
+-----------+------+
|pickup_date| trips|
+-----------+------+
| 2020-03-02|648990|
| 2020-03-01|784260|
| 2020-03-03|697880|
| 2020-03-04|707879|
| 2020-03-05|731165|
| 2020-03-06|872012|
| 2020-03-07|886071|
| 2020-03-08|731222|
| 2020-03-10|626474|
| 2020-03-09|628940|
| 2020-03-11|628601|
| 2020-03-12|643257|
| 2020-03-13|660914|
| 2020-03-14|569397|
| 2020-03-16|391518|
| 2020-03-15|448125|
| 2020-03-17|312298|
| 2020-03-18|269233|
| 2020-03-20|261900|
| 2020-03-22|162165|
+-----------+------+
only showing top 20 rows

</pre>

# 뉴욕의 각 행정구 별 데이터 추출하기
```python
zone_file = "E:\\GIt작업\\data-engineering\\01-spark\\data\\taxi+_zone_lookup.csv"
```

```python
zone_data = spark.read.csv(zone_file,inferSchema=True,header=True)
```

```python
zone_data.show(5)
```

<pre>
+----------+-------------+--------------------+------------+
|LocationID| Borough| Zone|service_zone|
+----------+-------------+--------------------+------------+
| 1| EWR| Newark Airport| EWR|
| 2| Queens| Jamaica Bay| Boro Zone|
| 3| Bronx|Allerton/Pelham G…| Boro Zone|
| 4| Manhattan| Alphabet City| Yellow Zone|
| 5|Staten Island| Arden Heights| Boro Zone|
+----------+-------------+--------------------+------------+
only showing top 5 rows

</pre>

```python
zone_data.createOrReplaceTempView('zone_data')
data.createOrReplaceTempView('trip_data')
```

```python
spark.sql("select * from zone_data limit 5").show()
```

<pre>
+----------+-------------+--------------------+------------+
|LocationID| Borough| Zone|service_zone|
+----------+-------------+--------------------+------------+
| 1| EWR| Newark Airport| EWR|
| 2| Queens| Jamaica Bay| Boro Zone|
| 3| Bronx|Allerton/Pelham G…| Boro Zone|
| 4| Manhattan| Alphabet City| Yellow Zone|
| 5|Staten Island| Arden Heights| Boro Zone|
+----------+-------------+--------------------+------------+

</pre>
어디에서 가장 승차가 많았나?

```python
spark.sql("select zone_data.borough,count(*) \
    from (trip_data join zone_data on trip_data.PULocationID = zone_data.LocationID) \
    group by zone_data.borough \
    order by count(*) desc").show()
```

<pre>
+-------------+--------+
| borough|count(1)|
+-------------+--------+
| Manhattan| 4953147|
| Brooklyn| 3735765|
| Queens| 2437394|
| Bronx| 2086597|
|Staten Island| 178818|
| Unknown| 845|
| EWR| 362|
+-------------+--------+

</pre>
어디에서 가장 하차가 많았나?

```python
spark.sql("select zone_data.borough,count(*) as drop_count \
        from (trip_data join zone_data on trip_data.DOLocationID = zone_data.LocationID) \
        group by zone_data.borough \
        order by drop_count desc").show()
```



```python
```
