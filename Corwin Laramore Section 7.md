# Section 7.1 
## Question 1
```SQL

SELECT ModelYear, Make, Model
FROM EVRegistry

```
## Question 2 
```SQL

SELECT DISTINCT ElectricVehicleType
FROM EVRegistry

```
## Question 3
```SQL

SELECT *
FROM EVRegistry
WHERE ElectricVehicleType = 'Battery Electric Vehicle (BEV)'

```
## Question 4 
```SQL

SELECT Make, Model
FROM EVRegistry
WHERE BaseMSRP > 20000 AND BaseMSRP < 35000

```

# Section 7.2
## Question 1
```SQL

SELECT *
FROM EVRegistry
WHERE City is NULL

```
## Question 2 
```SQL

SELECT Make, Model, ElectricVehicleType
FROM EVRegistry
WHERE VIN LIKE '%3E1EA1J'

```
## Question 3
```SQL

SELECT ModelYear, Make, Model, ElectricVehicleType, ElectricRange
FROM EVRegistry 
WHERE Make = 'TESLA' OR Make = 'CHEVROLET'
ORDER BY Make, ModelYear DESC

```
## Question 4
```SQL

SELECT stationId, COUNT(stationID) as numStations
FROM EVCharging
GROUP BY stationId
ORDER BY numStations DESC
LIMIT 5

```
## Question 5
```SQL

SELECT userId, MIN(chargeTimeHrs) as 'minTime', MAX(chargeTimeHrs) as 'maxTime'
FROM EVCharging
WHERE chargeTimeHrs > 0.5
GROUP BY userId
ORDER BY minTime, maxTime

```

# Section 7.3
## Question 1
```SQL

SELECT ROUND(AVG(chargeTimeHrs), 2) as avgChargeTime, weekday
FROM EVCharging
GROUP BY weekday
ORDER BY avgChargeTime

```
## Question 2 
```SQL

SELECT userId, ROUND(SUM(kwhTotal), 2) as totalPower
FROM EVCharging
GROUP BY userId
ORDER BY totalPower DESC
LIMIT 15

```
## Question 3
```SQL

SELECT dimFacility.facilityKey, dimFacility.typeFacility, COUNT(factCharge.facilityID) as numStation
FROM dimFacility
INNER JOIN factCharge
ON dimFacility.facilityKey = factCharge.facilityId
GROUP BY Typefacility
ORDER BY numStation DESC

```
## Question 4
```SQL

Primary keys are unique values that identify rows in a database table, similar to a website domain. The foreign key simply link to that value, like a URL will link to that domain.

```
## Question 5
```SQL

SELECT userId, MIN(chargeTimeHrs) as 'minTime', MAX(chargeTimeHrs) as 'maxTime'
FROM EVCharging
WHERE chargeTimeHrs > 1
GROUP BY userId
ORDER BY minTime, maxTime

```