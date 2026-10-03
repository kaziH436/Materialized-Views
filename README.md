# Materialized-Views
Stores sql query and stores the data returned from the sql query
[Materialized View in SQL | Faster SQL Queries using Materialized Views](https://www.youtube.com/watch?v=WzkBZ0byoYE&list=PLavw5C92dz9GbmgiW4TWVnxhjMFOIf0Q7&index=6)

    create table random_tab (id int, val, decimal);
    insert into random_tab 
    select 1, random() from generate_series(1,10000000);
    insert into random_tab 
    select 2, random() from generate_series(1,10000000);


## Find an average for each id 

    select id, avg(val), couint(*)
    from random_tab
    group by id;

This query took 3secs and its slow so materialized view solves this 

    create materialized view mv_random_tab
    as     
    select id, avg(val), couint(*)
    from random_tab
    group by id;
    
