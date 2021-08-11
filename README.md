# DataBase-Checkpoint-11-AUG

CREATE TABLE destinations (
  id SERIAL,
  name VARCHAR(50),
  average_temp DECIMAL(3, 2),
  has_beaches BOOLEAN,
  has_mountains BOOLEAN,
  cost_of_flight DECIMAL(4, 2)
);

CREATE TABLE airlines (
  id SERIAL,
  name VARCHAR(50)
);

INSERT INTO destinations (name, average_temp, has_beaches, has_mountains, cost_of_flight)
VALUES
    ('Thailand',82,true,true,765),
    ('Minnesota',41,false,false,235),
    ('New Zealand',66,true,true,433),
    ('England',45,false,false,290),
    ('Tristan da Cunha',59,true,true,1304);


INSERT into airlines (name)
VALUES
('Spirit'),
('Lufthansa'),
('Delta'),
('SouthWest');



-- 1
SELECT * FROM destinations;
-- 2
SELECT * FROM destinations WHERE has_beaches = 'true';
-- 3
SELECT * FROM destinations WHERE average_temp > 60;
--4
SELECT * FROM destinations WHERE has_beaches ='true' AND has_mountains='true';
--5
SELECT * FROM destinations WHERE cost_of_flight < 500;
--6
INSERT INTO destinations VALUES (6, 'The Bahamas',78,true,false,345);
--7
UPDATE destinations SET cost_of_flight = 1000 WHERE id = 3;
--8
DELETE FROM destinations WHERE id = 2 RETURNING *;
--9
UPDATE destinations SET name = 'Scotland' WHERE name = 'England';
--10
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

--11

