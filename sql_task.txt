/*1*/
SELECT DISTINCT status
FROM tasks
ORDER BY status ASC

/*2*/
SELECT P.name, COUNT (T.id) tasks_qty
FROM tasks T JOIN projects P ON T.project_id = P.id
GROUP BY P.name
ORDER BY tasks_qty DESC

/*3*/
SELECT P.name, COUNT (T.id) tasks_qty
FROM tasks T JOIN projects P ON T.project_id = P.id
GROUP BY P.name
ORDER BY P.name

/*4*/
SELECT name
FROM tasks
WHERE name LIKE 'N%'

/*5*/
SELECT P.name, COUNT (T.id) tasks_qty
FROM projects P LEFT JOIN tasks T ON P.id = T.project_id
WHERE P.name LIKE '%a%'
GROUP BY P.name

/*6*/
SELECT name
FROM tasks
GROUP BY name
HAVING COUNT (name) >= 2
ORDER BY name

/*7*/
SELECT name
FROM tasks
GROUP BY name, status
HAVING COUNT(*) > 1
ORDER BY COUNT(*)

/*8*/
SELECT P.name
FROM projects P JOIN tasks T ON P.id = T.project_id
WHERE T.status = 'complete'
GROUP BY P.name
HAVING COUNT(T.id) > 10
ORDER BY P.id