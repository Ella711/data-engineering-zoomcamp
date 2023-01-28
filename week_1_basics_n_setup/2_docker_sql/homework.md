## Homework Week 1
### Question 1

Ran:

    docker build --help

### Question 2

Ran:

    docker run -it --entrypoint=bash python:3.9
    pip list

### Question 3

    SELECT
        COUNT(to_char(lpep_pickup_datetime, 'MM-DD')) as "pickup",
        COUNT(to_char(lpep_dropoff_datetime, 'MM-DD')) as "dropoff"
    FROM
        green_taxi_trips
    WHERE
        to_char(lpep_pickup_datetime, 'MM-DD') = '01-15';

### Question 4

    SELECT
        lpep_pickup_datetime as "pickup",
        trip_distance
    FROM
        green_taxi_trips
    ORDER BY
        trip_distance DESC;

### Question 5

    SELECT
	    COUNT(*)
    FROM
	    green_taxi_trips
    WHERE
	    passenger_count = 2 AND
	    to_char(lpep_pickup_datetime, 'MM-DD') = '01-01';
and

    SELECT
	    COUNT(*)
    FROM
        green_taxi_trips
    WHERE
        passenger_count = 3 AND
        to_char(lpep_pickup_datetime, 'MM-DD') = '01-01';

### Question 6

    SELECT
        zpu."Zone" as "pickup",
        zdo."Zone" as "dropoff",
        tip_amount
    FROM
        green_taxi_trips g
    JOIN zones zpu
    ON
        g."PULocationID" = zpu."LocationID"
    JOIN zones zdo
    ON
        g."DOLocationID" = zdo."LocationID"
    WHERE
        zpu."Zone" = 'Astoria'
    ORDER BY
        tip_amount DESC
    LIMIT 1;