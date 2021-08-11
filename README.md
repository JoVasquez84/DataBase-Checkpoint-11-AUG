# DataBase-Checkpoint-11-AUG

# database_checkpoint

CHALLENGE 1
Query:
```SQL
SELECT * FROM destinations;
```
Results:
```

```

CHALLENGE 2
Query:
```SQL
SELECT * FROM destinations WHERE has_beaches = 'true';
```
Results:
```

```

CHALLENGE 3
Query:
```SQL
SELECT * FROM destinations WHERE average_temp > 60;
```
Results:
```

```

CHALLENGE 4
Query:
```SQL
SELECT * FROM destinations WHERE has_beaches ='true' AND has_mountains='true';
```
Results:
```

```

CHALLENGE 5
Query:
```SQL
SELECT * FROM destinations WHERE cost_of_flight < 500;
```
Results:
```

```

CHALLENGE 6
Query:
```SQL
INSERT INTO destinations VALUES (6, 'The Bahamas',78,true,false,345);
```
Results:
```

```

CHALLENGE 7
Query:
```SQL
UPDATE destinations SET cost_of_flight = 1000 WHERE id = 3;
```
Results:
```

```

CHALLENGE 8
Query:
```SQL
DELETE FROM destinations WHERE id = 2 RETURNING *;

```
Results:
```

```

CHALLENGE 9
Query:
```SQL
UPDATE destinations SET name = 'Scotland' WHERE name = 'England';
```
Results:
```

```

CHALLENGE 10
Query:
```SQL
ALTER TABLE airlines ADD PRIMARY KEY (id);
ALTER TABLE destinations ADD PRIMARY KEY (id);

CREATE TABLE airlines_destinations (
 id SERIAL,
 PRIMARY KEY (id),
 airline_id integer,
 CONSTRAINT fk_airlines
 FOREIGN KEY (airline_id)
 REFERENCES airlines(id),
 destinations_id integer,
 CONSTRAINT fk_destinations
   FOREIGN KEY (destinations_id)
    REFERENCES destinations(id)
);

INSERT INTO airlines_destinations (airline_id, destinations_id)
VALUES
(1,3),
(1,4),
(2,5),
(2,4),
(2,1),
(3,1),
(3,4),
(4,3),
(4,5);
```
Results:
```

```

CHALLENGE 11
Query:
```SQL
SELECT airlines.name FROM airlines WHERE airlines.id IN (SELECT airline_id FROM airlines_destinations WHERE airlines_destinations.destinations_id=3);
```
Results:
```
   name    
-----------
 Spirit
 SouthWest
(2 rows)
```

CHALLENGE 12
Query:
```SQL
SELECT airlines.name FROM airlines WHERE airlines.id NOT IN (SELECT airline_id FROM airlines_destinations WHERE airlines_destinations.destinations_id=4);
```
Results:
```
   name    
-----------
 SouthWest
(1 row)
```

CHALLENGE 13
Query:
```SQL
SELECT * FROM destinations; 
```
Results:
```
vacations=# SELECT * FROM destinations; 
 id |       name       | average_temp | has_beaches | has_mountains | cost_of_flight 
----+------------------+--------------+-------------+---------------+----------------
  1 | Thailand         |           82 | t           | t             |            765
  5 | Tristan da Cunha |           59 | t           | t             |           1304
  3 | New Zealand      |           66 | t           | t             |           1000
  6 | The Bahamas      |           78 | t           | f             |            345
  4 | Scotland         |           45 | f           | f             |            290
(5 rows)
```
