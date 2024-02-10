# Workaroud for changing the datatype from float64 to int64 of a column in bigquery



## Add new column CAST as integer
```
CREATE OR REPLACE TABLE trips_data_all.test_yellow_new AS
SELECT *, CAST(VendorID AS INT64) AS VendorIDINT FROM trips_data_all.test_yellow;
```
## remove original column using except()
```
CREATE OR REPLACE TABLE trips_data_all.updated_test_yellow_new AS
select * except(VendorID) from trips_data_all.test_yellow_new; 
```
## rename the new casted coumn name as removed column
```
CREATE OR REPLACE TABLE trips_data_all.yellow_tripdata AS
SELECT
 * EXCEPT(VendorIDINT),
 VendorIDINT AS VendorID
FROM
 semiotic-plexus-412804.trips_data_all.updated_test_yellow_new
```
